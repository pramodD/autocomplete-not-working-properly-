autocomplete-not-working-properly-
==================================

autocomplete not working properly (It shows list on backpress or delete after one character). Here is my code


<div data-role="page" id="mainPage">
    <div data-role="header">
        <h1>jQM Autocomplete</h1>
    </div>
    <div data-role="content">
        <p>
            <input type="text" id="searchField" placeholder="Categories">
            <ul id="suggestions" data-role="listview" data-inset="true"></ul>
        </p>
        <p>
            <a href="https://github.com/commadelimited/autoComplete.js" data-role="button"></a>
        </p>
    </div>
</div>
<script type="text/javascript">
$('#searchField').keyup(function () {
    var val = $.trim(this.value).length;
    if (val == 3) {
        // do something
        test = this.value;
        console.log("&&&&&&&&&&&&&&&&&&&&&" + test);
        callFunction();
    }
})
</script>
<script>
function callFunction() {
    console.log("Inside callFunction>>>>>>>>>>>>>");
    var newArray = new Array();
    console.log("Inside bind????????????");
    var substr, out, pra;
    var finalStr = "system" + encodeURIComponent("|^") + "0" + encodeURIComponent("|^") + test;
    var encodedURL = encodeURI("http://myDomainSearch.asp?requestString=");
    var parameters = decodeURIComponent(finalStr);
    console.log("Before calling ajax");
    $.ajax({
        type: "POST",
        contentType: "application/x-www-form-urlencoded; charset=UTF-8",
        url: encodedURL,
        data: parameters
    }).done(function (msg) {
        response = msg
        if (response.charAt(0) == '0') {
            console.log("***" + response);
            substr = response.split('$');
            console.log("!@#!@#!@#" + substr.length);
            for (var out = 1; out < substr.length - 1; out++) {
                pra = substr[out].split('|^');
                console.log("!!!!!!" + pra[0]);
                newArray.push(pra[0]);
            }
            console.log("$%^$%^$%^$%^" + newArray.length);
            for (var c = 0; c < newArray.length - 1; c++) {
                console.log(newArray[c]);
            }
            $("#searchField").autocomplete({
                target: $('#suggestions'),
                source: newArray,
                link: 'target.html?term=',
                minLength: 0
            });
        }
        else {
            alert("error");
        }
    });
}
</script>

