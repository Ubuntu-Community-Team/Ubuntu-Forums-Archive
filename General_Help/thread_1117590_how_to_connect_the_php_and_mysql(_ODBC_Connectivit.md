---
title: "how to connect the php and mysql( ODBC Connectivity Information need)"
date: 2009-04-06
forum: General Help
---

### Post by suresh_vandiyur on 2009-04-06
**** how to connect the php and mysql.. i have suresh database in emma mysql. how to connect the databast retrieve or modify or delete records in php.. Any one know means reply me..**(ODBC)**

---

### Post by tornadof3 on 2009-04-06
<?php
$mysql_database="name of your database";
$mysql_user="username";
$mysql_pwd="password";
$hostname = "server, eg localhost";
$db = mysql_connect($hostname,$mysql_user,$mysql_pwd) or die("Database connection failed: \n".mysql_error());
mysql_select_db($mysql_database,$db);

$sql="SELECT * FROM `table`";
	$result=mysql_query($sql, $db) or die ("\nCould not query MySQL: ". mysql_error());
	$results=mysql_num_rows($result);
	
	if ($results > 0) {
		while($row=mysql_fetch_array($result)) {
			$data=$result["field1"];
                        $data2=$result["field2"]; 
			}

?>

---

### Post by suresh_vandiyur on 2009-04-07
> **tornadof3 said:**
> <?php
$mysql_database="name of your database";
$mysql_user="username";
$mysql_pwd="password";
$hostname = "server, eg localhost";
$db = mysql_connect($hostname,$mysql_user,$mysql_pwd) or die("Database connection failed: \n".mysql_error());
mysql_select_db($mysql_database,$db);

$sql="SELECT * FROM `table`";
	$result=mysql_query($sql, $db) or die ("\nCould not query MySQL: ". mysql_error());
	$results=mysql_num_rows($result);
	
	if ($results > 0) {
		while($row=mysql_fetch_array($result)) {
			$data=$result["field1"];
                        $data2=$result["field2"]; 
			}

?>
ok..thank you so much.. i asking about the driver information.. if u know means reply me..

---

