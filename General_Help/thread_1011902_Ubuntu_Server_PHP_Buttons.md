---
title: "Ubuntu Server PHP Buttons"
date: 2008-12-15
forum: General Help
---

### Post by CrusaderAD on 2008-12-15
I have a php site on my Ubuntu Test server and it has a few forms on it. Here's the code:

```
<form method="post" action="category.php">
<select name=cid>
<OPTION value="0">Shop By Category</OPTION>
<?

$cid = (isset($_REQUEST['cid'])) ? $_REQUEST['cid']: null;
$catname = (isset($_REQUEST['catname'])) ? $_REQUEST['catname']: null;

$result = mysql_query("select * from categories ORDER by catname ASC") or die (mysql_error()); 
while ($row = mysql_fetch_array($result))
{
echo "
<OPTION value=\"{$row['cid']}\">{$row['catname']}</OPTION>
";
}
mysql_free_result($result);
?>
</select>
<input type="submit" value=" GO ">
</form>
```

Right now it seems to just use some defaulted gray button labeled as "GO" like in the code. How can I change it to use a button of my choice?

---

### Post by eBoxNet on 2008-12-15
that has nothing to do with ubuntu server,anyways you can use an input image with a javascript call and style it with an image or whatever you want,there are many ways to do it,i am giving you a javascript way to do it.

try this :
```

<html>
<head>
<script>
function submitform()
{
document.formname.submit();
}
</script>
</head>
<body>
<form name="formname" method="post" action="mailto:youremail@email.com">
<input type="button" value="SubmitMe" OnClick="submitform();return false;" style="background-image:url(my_button.gif); width:200px; height:23px; border:0; color:#036;font-family: Verdana; font-weight: bold;" />
</form>
</body>
</html>
```

---

### Post by CrusaderAD on 2008-12-15
I know it has nothing to do with the server I'm running... just thought the more info the better. Thanks for the input! I'll give it a shot.

---

