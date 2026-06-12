---
title: "ODBC driver information need"
date: 2009-04-07
forum: General Help
---

### Post by suresh_vandiyur on 2009-04-07
**** i had installed the php and mysql.so i need ODBC driver information.any one know means reply me...

---

### Post by sahabcse on 2009-04-07
Have a look on

 /etc/php5/apache2/php.ini

---

### Post by suresh_vandiyur on 2009-04-07
> **sahabcse said:**
> Have a look on

 /etc/php5/apache2/php.ini how to edit the file for connect the php and mysql can u explain me.

---

### Post by sahabcse on 2009-04-07
Hi 

You want to create database for php application?? Install phpmyadmin tool for easy doing. For installing php myadmin

#sudo apt-get install phpmyadmin

Otherwise pls let me know Your exact issue??

---

### Post by suresh_vandiyur on 2009-04-07
> **sahabcse said:**
> Hi 

You want to create database for php application?? Install phpmyadmin tool for easy doing. For installing php myadmin

#sudo apt-get install phpmyadmin
 i had installed phpmyadmin. what i can sselect apache or apache2 or apache-ssl or apache-perl or lighttpd.

Otherwise pls let me know Your exact issue?? now am using ubuntu. A small program Frontend-php nd Backend-mysql.. that purpose am asking the information can u explain me..

---

### Post by sahabcse on 2009-04-07
Hi

Its web based application means First you have to install apache and copy your web directory into /var/www/. Then create the database and user for your application using phpmyadimn. For more info please follow below url


[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by suresh_vandiyur on 2009-04-07
> **sahabcse said:**
> Hi

Its web based application means First you have to install apache and copy your web directory into /var/www/. Then create the database and user for your application using phpmyadimn. For more info please follow below url


[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
no its offline.. i had installed and configured phpmyadmin.. then what i can do?.. can u tell me... are you well know about the php and mysql.

---

### Post by mb_webguy on 2009-04-07
Do you have an existing database to which you're trying to connect, or would you like to create a new database?  

If it's the first, and it's an Access database hosted on another computer, then you *will* need ODBC.  You can get the ODBC extension for PHP by installing the php5-odbc package.

If you don't already have a database, MySQL is your friend.  I recommend the official GUI administration tools (which you can get by installing the mysql-admin package) rather than phpMyAdmin, though.  You would use the mysqli PHP extension to access the MySQL database once you've created it.

---

### Post by sahabcse on 2009-04-07
Hi

This will help follow

[http://www.howtoforge.com/adding-an-odbc-driver-for-mysql-on-ubuntu](http://www.howtoforge.com/adding-an-odbc-driver-for-mysql-on-ubuntu)

---

### Post by suresh_vandiyur on 2009-04-07
> **mb_webguy said:**
> Do you have an existing database to which you're trying to connect, or would you like to create a new database?  

If it's the first, and it's an Access database hosted on another computer, then you *will* need ODBC.  You can get the ODBC extension for PHP by installing the php5-odbc package.

If you don't already have a database, MySQL is your friend.  I recommend the official GUI administration tools (which you can get by installing the mysql-admin package) rather than phpMyAdmin, though.  You would use the mysqli PHP extension to access the MySQL database once you've created it.
i already installed the mysql adminstrator
[B]Could not connect to host 'krishna'.
MySQL Error Nr. 2005
Unknown MySQL server host 'krishna' (1)

Click the 'Ping' button to see if there is a networking problem
[/B] how recover this problem...

---

### Post by sahabcse on 2009-04-07
paste the follwing

cat /etc/hosts
cat /etc/network/interfaces
ifconfig

Also Check did u assign the database privilege for the user for the host 'krishna'.

---

### Post by suresh_vandiyur on 2009-04-07
> **sahabcse said:**
> paste the follwing

cat /etc/hosts
cat /etc/network/interfaces
ifconfig

Also Check did u assign the database privilege for the user for the host 'krishna'.

<html>
<body>

<?php
$conn=odbc_connect('northwind','','');
if (!$conn)
  {exit("Connection Failed: " . $conn);}
$sql="SELECT * FROM customers";
$rs=odbc_exec($conn,$sql);
if (!$rs)
  {exit("Error in SQL");}
echo "<table><tr>";
echo "<th>Companyname</th>";
echo "<th>Contactname</th></tr>";
while (odbc_fetch_row($rs))
{
  $compname=odbc_result($rs,"CompanyName");
  $conname=odbc_result($rs,"ContactName");
  echo "<tr><td>$compname</td>";
  echo "<td>$conname</td></tr>";
}
odbc_close($conn);
echo "</table>";
?>

</body>
</html> what i configure for execute the above program.. can u exaplain me.

---

### Post by suresh_vandiyur on 2009-04-12
> **suresh_vandiyur said:**
> <html>
<body>

<?php
$conn=odbc_connect('northwind','','');
if (!$conn)
  {exit("Connection Failed: " . $conn);}
$sql="SELECT * FROM customers";
$rs=odbc_exec($conn,$sql);
if (!$rs)
  {exit("Error in SQL");}
echo "<table><tr>";
echo "<th>Companyname</th>";
echo "<th>Contactname</th></tr>";
while (odbc_fetch_row($rs))
{
  $compname=odbc_result($rs,"CompanyName");
  $conname=odbc_result($rs,"ContactName");
  echo "<tr><td>$compname</td>";
  echo "<td>$conname</td></tr>";
}
odbc_close($conn);
echo "</table>";
?>

</body>
</html> what i configure for execute the above program.. can u exaplain me.

i had installed phpmyadmin and then removed.. and also i delete cat /etc/network/interfaces file.. after then i reboot and my system. At the boot NFS Kernel deamon service was started very slowly.. it takes 5 minutes or more time.. how to recover this problem.. any one know means reply me..

---

