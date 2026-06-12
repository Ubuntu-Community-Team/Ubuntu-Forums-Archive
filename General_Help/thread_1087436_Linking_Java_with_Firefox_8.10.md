---
title: "Linking Java with Firefox? 8.10"
date: 2009-03-05
forum: General Help
---

### Post by jeff35 on 2009-03-05
I have installed Java as directed by Java. all went well, although learning sudo and linux file system took a afternoon tho.

I am following these instructions.

[http://java.com/en/download/help/5000010500.xml#selfextracting](http://java.com/en/download/help/5000010500.xml#selfextracting)

I am down to the enable and configure firefox.
 can someone explain this?

ln -s /usr/java/jre1.6.0/plugin/i386/ns7
/libjavaplugin_oji.so
 i am not sure i got it right.
 does a zip program come with ubuntu?

I cant get this to work:

cd /usr/lib/firefox-1.4/extensions
unzip /usr/java/jre1.6.0/lib/deploy/ffjcext.zip

This is my terminal screen:

jeff@ubuntu:/usr/lib/firefox-3.0.3$ cd extensions
jeff@ubuntu:/usr/lib/firefox-3.0.3/extensions$ unzip /user/java/jre1.6.0_12/lib/deploy/ffjcext.zip
unzip:  cannot find or open /user/java/jre1.6.0_12/lib/deploy/ffjcext.zip, /user/java/jre1.6.0_12/lib/deploy/ffjcext.zip.zip or /user/java/jre1.6.0_12/lib/deploy/ffjcext.zip.ZIP.
jeff@ubuntu:/usr/lib/firefox-3.0.3/extensions$ sudo unzip /user/java/jre1.6.0_12/lib/deploy/ffjcext.zip
[sudo] password for jeff: 
unzip:  cannot find or open /user/java/jre1.6.0_12/lib/deploy/ffjcext.zip, /user/java/jre1.6.0_12/lib/deploy/ffjcext.zip.zip or /user/java/jre1.6.0_12/lib/deploy/ffjcext.zip.ZIP.
jeff@ubuntu:/usr/lib/firefox-3.0.3/extensions$ unzip /user/java/jre1.6.0_12/lib/deploy/ffjcext
unzip:  cannot find or open /user/java/jre1.6.0_12/lib/deploy/ffjcext, /user/java/jre1.6.0_12/lib/deploy/ffjcext.zip or /user/java/jre1.6.0_12/lib/deploy/ffjcext.ZIP.
jeff@ubuntu:/usr/lib/firefox-3.0.3/extensions$ ls
[email]langpack-en-GB@firefox-3.0.ubuntu.com[/email]  [email]ubufox@ubuntu.com[/email]
jeff@ubuntu:/usr/lib/firefox-3.0.3/extensions$ 

ty jeff35 my ultimate goal is to get netzero dialup working
I got the dialer going, but need to link the netzero software somhow. any ideas?

---

