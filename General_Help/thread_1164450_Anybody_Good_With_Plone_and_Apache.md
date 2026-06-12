---
title: "Anybody Good With Plone and Apache"
date: 2009-05-19
forum: General Help
---

### Post by wsonar on 2009-05-19
so my site is running apache I have mod_python installed. 
I guess I need to install zope also from what I've been reading.



Anybody use plone or can point me to any good tutorials for setting up under apache?

Thanks

---

### Post by wsonar on 2009-05-19
So I found some info here

[https://help.ubuntu.com/community/forum/server/Plone]("https://help.ubuntu.com/community/forum/server/Plone")

I guess from what I understand I don't need apache to run plone because it uses zope I'm a little confused on this part

Can I have both?

what is the recommended way?

---

### Post by wsonar on 2009-05-20
I guess all the info is here may take a while to get this going

[http://plone.org/documentation/how-to/plone-with-apache]("http://plone.org/documentation/how-to/plone-with-apache")

---

### Post by perlion on 2011-12-11
To install Plone on Ubuntu or any other linux distro is to go to plone.org and download the latest stable linux Unified-Installer. 

As far as using apache and plone:  Plone is a webserver/intranet app program that rest on top of zope: an object oriented database.  You can run only zope/plone but this not recommended for a production server as zope is not secure. 

So for a production scenario Apache>Zope>Plone.  Apache listens on port 80 for incoming request and rewrites urls to Zope port 8080 (or whatever you specify) .  

Writing the rewrite rules can have a learning curve but there are tools. Google "rewrite witch".

I'm trying to learn NGinx with Zope/Plone now.

---

