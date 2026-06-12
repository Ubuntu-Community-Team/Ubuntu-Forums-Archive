---
title: "Standalone www BLAST setup on Feisty help"
date: 2007-06-21
forum: Education &amp; Science
---

### Post by jpopesku on 2007-06-21
Hey all,
I had been using Edgy to run a BLAST server but recently upgraded to Feisty.  Something during that switch caused my standalone www BLAST server to break.  I tried to reinstall wwwblast (v2.2.16 downloaded from the NCBI ftp server) but to no avail.  

The error I get when I try to BLAST is:
```
#!/bin/csh -f

#
# $Id: blast.cgi,v 1.1 2002/08/06 19:03:51 dondosha Exp $
#

echo "Content-type: text/html"
echo ""

#setenv DEBUG_COMMAND_LINE TRUE
setenv BLASTDB db

./blast.REAL
```
(I've tried to uncomment "setenv DEBUG_COMMAND_LINE TRUE" to nothing different happened...)

The .cgi script is supposed to pass off the query request from the .html page to blast.REAL, which does all the work and returns the output.  But the script doesn't seem to be working.  So I thought it was something related to cgi.  The "old" way that I knew how to enable cgi was to edit the httpd.conf file, but now this file is empty.  The "cgi.load -> /etc/apache2/mods-available/cgi.load" is present in the mods-enabled directory, so I'm assuming that the problem is not with cgi.  Is this a good assumption?  What else could I do to rescue my BLAST server??  Anyone have any ideas?

---

### Post by meatpan on 2007-06-21
Can you post the error messages?  I think you might have forgot it in the original post.  The problem is most likely a missing dependency, or related to apache config.  The error messages will help sort it out.

---

### Post by jpopesku on 2007-06-21
Hi meatpan,
It's not so much an error I'm getting, it's just that I'm not getting _anything_.  When I enter a sequence into the appropriate box in the blast.html form, and hit "search", a page appears that has printed:
```
#!/bin/csh -f

#
# $Id: blast.cgi,v 1.1 2002/08/06 19:03:51 dondosha Exp $
#

echo "Content-type: text/html"
echo ""

#setenv DEBUG_COMMAND_LINE TRUE
setenv BLASTDB db

./blast.REAL
```
And then nothing happens;  it just sits there.  I tried checking the running processes using the 'top' command, but blast.REAL is not listed (as it used to do in Edgy when blast was running a query).

I'm unsure of what it could be.  Something with new security settings in Feisty?  Something not setup up correctly with apache/cgi??  My Edgy -> Feisty upgrade was done through the graphical package manager (sorry;  can't remember the name of it (aptitude!?)), so I thought my settings would remain intact...

---

### Post by jpopesku on 2007-06-26
Fixed!
For those interested, I needed to edit /etc/apache2/apache2.conf:

Added
```

   <Directory /path/to/my/blast>
       Options +ExecCGI
       AddHandler cgi-script .cgi
    </Directory>

``` within <IfModule alias_module></IfModule> (~line 260)

And I had to remove the # from # AddHandler cgi-script .cgi (~line 510)

Hope that helps someone else!
JP

---

### Post by ywurm on 2011-06-15
An [alternative local BLAST server]("http://www.sequenceserver.com") may be easier to set up...

cheers

---

### Post by Sef on 2011-06-15
Locked. Necromancing.

---

