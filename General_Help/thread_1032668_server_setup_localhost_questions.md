---
title: "server setup/ localhost questions"
date: 2009-01-06
forum: General Help
---

### Post by infernus_crusher on 2009-01-06
hi im a beginner at PHP and server setup and im wondering how to test PHP files on your own computer. i read somewhere that you can do it by typing "localhost" on firefox but all that comes out was the message "It works!".

i'm also wondering which directory localhost refers to in my own computer and what i can do to change the contents so that firefox can be used to test my PHP driven web pages?

i have apache2 installed with "apt-get install apache2". thanks in advance!

---

### Post by nikgare on 2009-01-06
The It Works! info is coming from the index.html file in **/var/www**
YOu canj either start by putting your web pages in this folder, or altering Apache's config (in /etc/apache2) files to change the www-root folder

---

### Post by bukwirm on 2009-01-06
You'll have to change the configuration file anyway (*/etc/apache2/sites-available/default*) to make Apache stop redirecting to the "It works" page.

---

### Post by erflol on 2009-01-06
As bukwirm mentioned you have to edit the default file in the sites-available folder. Simply change the DocumentRoot and the Directory locations.

For example I have set up a public_html folder in my home folder. I have changed the DocumentRoot and Directory locations as follows:

DocumentRoot /home/user/public_html/

<Directory /home/user/public_html/>
...
</Directory>

If you put an index.html file in that folder it will be displayed. Alternatively since the Indexes option is in the directory config by default you can place any file into that folder (provided you do not have an index file) and it will be displayed.

Make sure to restart apache (sudo /etc/init.d/apache2 restart) after making changes to that file. 

If this is only to be used for testing you should be fine with that. If you will be serving webpages from this computer you will want to secure it. 

Cheers
eRflol

---

### Post by infernus_crusher on 2009-01-13
I've managed to set up the directory and stuff, but there's still a problem. This is the code that I got from the book I'm learning PHP with:

<?
session_start();
if(!isset($count)) {
	session_register("count");
	$count = 1;
}
?>
You have been to this page <?=$count?> times.
<?
$count++;
?>

So the script will display "You have been to this page 1 times" the first time "localhost" is typed into the browser.

According to the book, pressing refresh several times will increase "count', but for some reasons it doesn't on my computer. It kept saying "1 times".

Can anybody help?

---

