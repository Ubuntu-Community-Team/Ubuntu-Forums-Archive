---
title: "Converting documents to text ..."
date: 2009-02-19
forum: General Help
---

### Post by gvanto on 2009-02-19
I've installed docvert according to: [http://holloway.co.nz/docvert/documentation/](http://holloway.co.nz/docvert/documentation/) and after alot of googling to try and see how to work with it, i tried the sample-use.php document, but get a Forbidden cant access error:

------------------
Forbidden

You don't have permission to access /docvert/writable/preview1598761/sample-document/sample-document.odt on this server.
------------------

I'm trying to get it to work with a simple php script in /var/www/testdocvert.php

If anyone has managed to get tihs working on their local server and have any tips, it would be much appreciated !

gvanto
ps: the main aim here is to get most commonly used word processor files (odt, doc, DOCX, rtf, pdf) converted into plain text on a Centos (remote hosting) server ... ( so far using antiword and xpdf and they're great, but we need support for .odt and .docx files too)

---

### Post by Yellow Pasque on 2009-02-19
You have a permissions issue. You'll either need to run docvert as a root procees or change the permissions of "sample-document.odt"
As root on the Centos server:
```
chmod +r sample-document.odt
```
EDIT: I'm assuming docvert does not alter the original in any way. If it does +rw instead of +r

---

### Post by gvanto on 2009-02-19
OK I've done that, still getting Forbidden error.

I've also tried changing the permission on the writable folder (output below), as the install says to do ([http://holloway.co.nz/docvert/documentation/install](http://holloway.co.nz/docvert/documentation/install) under >Install & Security)

STILL, I get this error ...

help much appreciated,
gvanto


> 
pacific@mainbox:/usr/share/docvert$ ls -al
total 72
drwxr-xr-x   6 root root 4096 2009-02-20 13:00 .
drwxr-xr-x 223 root root 4096 2009-02-20 13:00 ..
-rw-r--r--   1 root root  142 2008-07-03 15:47 admin.php
drwxr-xr-x  10 root root 4096 2009-02-20 13:00 core
drwxr-xr-x   3 root root 4096 2009-02-20 13:00 doc
-rw-r--r--   1 root root 2967 2008-07-03 15:47 frameset.php
-rw-r--r--   1 root root  569 2008-07-03 15:47 generate-document.php
-rw-r--r--   1 root root  206 2008-07-03 15:47 generation.php
drwxr-xr-x   4 root root 4096 2009-02-20 13:00 generator-pipeline
-rw-r--r--   1 root root   47 2008-07-03 15:47 index.php
-rw-r--r--   1 root root  504 2008-07-03 15:47 list-pipelines.php
-rw-r--r--   1 root root  150 2008-07-03 15:47 loading.php
drwxr-xr-x   6 root root 4096 2009-02-20 13:00 pipeline
-rw-r--r--   1 root root  206 2008-07-03 15:47 sample-use.php
-rw-r--r--   1 root root 5516 2008-07-03 15:47 save-changes.php
-rw-r--r--   1 root root 2476 2008-07-03 15:47 upload-results.php
-rw-r--r--   1 root root 2699 2008-07-03 15:47 web-service.php
lrwxrwxrwx   1 root root   25 2009-02-20 13:00 writable -> /var/lib/docvert/writable
pacific@mainbox:/usr/share/docvert$ sudo chmod -R a=wrx /var/lib/docvert/writable
pacific@mainbox:/usr/share/docvert$ sudo /etc/init.d/apache2 restart



---

### Post by bodhi.zazen on 2009-02-19
Looks like the directory "writable" is a link.

By default apache will not follow links.

IMO you are best off unlinking the directory and then copy the directory.

The other option is to configure apache to follow links which is a bit of a (small) security risk.

Also you do not want documents to bw world writable.

They should , IMO, be owned by root.www-data

www-data should have ro (you need x for directories).

---

### Post by gvanto on 2009-02-20
Hey thanks much Bohdi!

This has worked to solve this problem. Can now convert basic odt file (or at least the demo can which is pretty cool! I still don't know how to do it in my own scripts, but I'm sure I'll get there eventually ... perhaps even create a blog showing how its done :-)

OK, next problem. Need to get docx files convertd (the new Windows uses this format)... now, using the same sample-use.php page, attempting to upload a docx file gives the following error (of which there isn't anythign within /usr/share/docvert/doc/troubleshooting.txt):


----------------------------------------------------------------------

Unable to generate an OpenDocument file from your upload.

The command I tried to run was:

    /usr/share/docvert/core/lib/pyodconverter/pyodconverter.py --stream

In response to that command, the following was returned

    Error: URL seems to be an unsupported one.

&#8226; Read install.txt and troubleshooting.txt for general tips.


----------------------------------------------------------------------

OK, so it seems gotta install PyODConverter, back to step 3 within: [http://holloway.co.nz/docvert/documentation/install](http://holloway.co.nz/docvert/documentation/install)

Now, reading this paragraph as a newbie to both Linux servers and OpenOffice server and a host of other linux-y things, a myriad of questions come up, to the extent that I'm not going to even attempt doing anything until there's a bit more clarity, so if someone knows, advice would be great!
(Q's within text below, which is the excerpt from the page on how to get OOo server & PyODConverter working to convert docx)

> 
1) PyODConverter via OOo Server
	-------------------------------
	
		This requires Python, python-uno, and
		OpenOffice.org 2.3+ running in server mode
		(which means it's listening on a port).

- (these i have installed)
- seems this OOo server process has already been started (do I need to start it again?), see (way below) bottom ... **


		Docvert includes its own highly customised version of
		PyODConverter so there's no need to download a copy.

			For Linux/OSX users you'll need to allow
			your web-server user to start/stop
			OOo Server so go to the admin page and under the "Run as User" heading enter the username
			to run OpenOffice.org as.

- **which admin page?** I went to [http://localhost/docvert/admin.php](http://localhost/docvert/admin.php) and there's nothing on "Run as User" in there ...
- what is the username i should enter here?

			Then ensure that the admin page's
			"Super User Method" is "sudo",

- I guess this depends on knowing that the admin page is in the first place ...

			and then you'll need to configure permissions
			with the "visudo" command (from the command line)

			to add some lines to sudoers,
			Add this line,

- add this line where?

	www-data ALL=(NAMEOFUSER) NOPASSWD: /var/www/docvert/core/config/unix-specific/openoffice.org-server-init.sh

			Replace NAMEOFUSER with... the name of the user but
			leave the brackets () because sudoers wants them.
			And replace www-data with the web server user if it's
			something else.
			For example, it might look like this,

	www-data ALL=(docvert) NOPASSWD: /var/www/docvert/core/config/unix-specific/openoffice.org-server-init.sh

			if you wanted to run OOo Server under
			the system user "docvert".




OOo server in headless mode:
> 

pacific@mainbox:~$ soffice -headless -nofirststartwizard -accept="socket,host=localhost,port=8100;urp;StarOffice.Service"
pacific@mainbox:~$ ps aux | grep openoffice
docvert   8777  0.0  4.1 225604 86272 ?        Sl   13:00   0:05 /usr/lib/openoffice/program/soffice.bin -headless -norestore -nologo -norestore -nofirststartwizard -acc                                ept=socket,port=2002;urp; -splash-pipe=5
pacific  11326  1.3  1.1  95472 24152 pts/10   Sl   18:02   0:00 /usr/lib/openoffice/program/soffice.bin -headless -nofirststartwizard -accept=socket,host=localhost,port                                =8100;urp;StarOffice.Service -splash-pipe=7
pacific  11333  0.0  0.0   3008   764 pts/10   R+   18:03   0:00 grep openoffice
pacific@mainbox:~$















[http://holloway.co.nz/docvert/documentation/install](http://holloway.co.nz/docvert/documentation/install)

---

