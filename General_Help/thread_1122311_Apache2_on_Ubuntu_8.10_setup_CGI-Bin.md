---
title: "Apache2 on Ubuntu 8.10 setup CGI-Bin"
date: 2009-04-10
forum: General Help
---

### Post by Priest.Lucard on 2009-04-10
What I am looking for is how to link my CGI-Bin perl programs to my web site.
 
My CGI-Bin locatioin is /usr/lib/cgi-bin/ 
My web pages location are /var/www/

How do i get them to run under the web server?
If i type in the URL [http://127.0.0.1/cgi-bin/listip.pl](http://127.0.0.1/cgi-bin/listip.pl) it will not run the perl program just try to download it.

Apache/2.2.9 (Ubuntu) mod_perl/2.0.4 Perl/v5.10.0 Server at 127.0.0.1 Port 80

But all the rest of my web pages work.

This is my perl code
#!/usr/bin/perl
print "content-type: text//html\n\n";
print "<HTML><HEAD>";
print "<TITLE>Alex Lucard's Home Page<//TITLE>\n";
print "<META HTTP-EQUIV=\"Pragma\" CONTENT=\"no-cache\">\n";
print "<bgsound src=\"CHIMAI.mid\" loop=\"-1\"></HEAD>\n";
print "<Body BACKGROUND=\"/Images/logo02.gif\">\n";
print "<img src=\"/Images/logo06.gif\">\n";
print "</Body></HTML>";


lucard@Boo:/usr/lib/cgi-bin$ ls -la
total 664
drwxr-xr-x   2 lucard root     4096 2009-04-10 21:55 .
drwxr-xr-x 267 root   root   106496 2009-04-10 12:51 ..
-rwxr-xr-x   1 root   root   548960 2008-12-03 15:10 awstats.pl
-rwxr-xr-x   1 lucard lucard    353 2009-04-10 22:17 listip.pl

/etc/apache2/sites-enabled/

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

---

