---
title: "Php parsing error"
date: 2009-04-23
forum: General Help
---

### Post by tomo11 on 2009-04-23
I have ubuntu 8.10 and i have installed apache2, php5 and myslq5.
I am trying to pars from mysql to xml with php, but i get an error:
**'Parsing error:** syntax error, unexpected T_OBJECT_OPERATOR in var/www/testbook.php on line 22'

I read in a few forums and they all said that php4 doesn't support this, and i gave to get php5. which i have.
I have **libxml2** installed as well.
Can anyone tell me what the problem is please?? very urgent

this is my code:

<?php 

// query database for records 
$connection = mysql_connect("localhost", "root", "root") or die ("Unable to connect!"); 
mysql_select_db("testbook") or die ("Unable to select database!"); 
$query = "SELECT id, title, artist FROM cds"; 
$result = mysql_query($query) or die ("Error in query: $query. " . mysql_error()); 

if (mysql_num_rows($result) > 0) 
{
      // create DomDocument object 
      $doc = new_xmldoc("1.0"); 

      // add root node 
      $root = $doc->add_root("cds"); 

      // iterate through result set 
      while(list($id, $title, $artist) = mysql_fetch_row($result)) 
      {
            // create item node 
            $record = $root->new_child("cd", ""); 
             record->set_attribute("id", $id); 

            // attach title and artist as children of item node 
            $record->new_child("title", $title); 
            $record->new_child("artist", $artist); 
      } 

// print the tree 
echo $doc->dumpmem(); 
}   
// close connection 
mysql_close($connection); 
?>

Thank You

---

### Post by Arndt on 2009-04-23
> **tomo11 said:**
> I have ubuntu 8.10 and i have installed apache2, php5 and myslq5.
I am trying to pars from mysql to xml with php, but i get an error:
**'Parsing error:** syntax error, unexpected T_OBJECT_OPERATOR in var/www/testbook.php on line 22'

I read in a few forums and they all said that php4 doesn't support this, and i gave to get php5. which i have.
I have **libxml2** installed as well.
Can anyone tell me what the problem is please?? very urgent

this is my code:

<?php 

// query database for records 
$connection = mysql_connect("localhost", "root", "root") or die ("Unable to connect!"); 
mysql_select_db("testbook") or die ("Unable to select database!"); 
$query = "SELECT id, title, artist FROM cds"; 
$result = mysql_query($query) or die ("Error in query: $query. " . mysql_error()); 

if (mysql_num_rows($result) > 0) 
{
      // create DomDocument object 
      $doc = new_xmldoc("1.0"); 

      // add root node 
      $root = $doc->add_root("cds"); 

      // iterate through result set 
      while(list($id, $title, $artist) = mysql_fetch_row($result)) 
      {
            // create item node 
            $record = $root->new_child("cd", ""); 
             record->set_attribute("id", $id); 

            // attach title and artist as children of item node 
            $record->new_child("title", $title); 
            $record->new_child("artist", $artist); 
      } 

// print the tree 
echo $doc->dumpmem(); 
}   
// close connection 
mysql_close($connection); 
?>

Thank You

Look at line 22, and compare with how the other lines are written.

---

### Post by enervation on 2009-04-23
'record' is a variable, so should always be written with a $ preceding its name.

---

### Post by tomo11 on 2009-04-24
thanx [enervation]("http://ubuntuforums.org/member.php?u=201261"), the error was the $ in-front of record
but now i get this "**Fatal error**:  Call to undefined function new_xmldoc() in **/var/www/testbook.php** on line [B]12" 
line 12 being "[/B]$doc = new_xmldoc("1.0");"
i even tried "domxml_new_xmldoc("1.0")"
Any suggestions here??
Thank you

---

### Post by Arndt on 2009-04-24
> **tomo11 said:**
> thanx [enervation]("http://ubuntuforums.org/member.php?u=201261"), the error was the $ in-front of record
but now i get this "**Fatal error**:  Call to undefined function new_xmldoc() in **/var/www/testbook.php** on line [B]12" 
line 12 being "[/B]$doc = new_xmldoc("1.0");"
i even tried "domxml_new_xmldoc("1.0")"
Any suggestions here??
Thank you

You said it was your code. Where does it come from?

---

### Post by tomo11 on 2009-04-25
I didn't say its my code i said I'm trying to pars it. its from a book New Riders - XML and PHP if it makes any difference.

---

### Post by Arndt on 2009-04-25
> **tomo11 said:**
> I didn't say its my code i said I'm trying to pars it. its from a book New Riders - XML and PHP if it makes any difference.

It makes some difference if you had to type it in from a book, or if you got it computer-ready from someone. Did you type it in? To me, new_xmldoc looks like a mistyping of new xmldoc. It could be printed wrong, too, of course. If you google for "new_xmldoc", you will find questions from people who seem to have the same problem as you.

I'm a beginner of PHP myself, and haven't used the XML functions yet.

---

### Post by tomo11 on 2009-04-26
thanx, I'll see what i can dig out from that

---

### Post by indytim on 2009-04-26
Either new_xmldoc is a function (which you haven't defined in the code) or, again you are missing the "$" as a variable.

IndyTim

---

