---
title: "apt-get install mod_python?"
date: 2009-03-20
forum: General Help
---

### Post by newbie.poster on 2009-03-20
I am trying to get mod_python installed on my heron server, and am running into a problem. The specific error I get when starting apache is:

apache2: Syntax error on line 185 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/mod_python.load: Cannot load /usr/lib/apache2/modules/mod_python.so into server: /usr/lib/apache2/modules/mod_python.so: cannot open shared object file: No such file or directory

And sure enough, browsing to the that dir reveals it is not there. Now I think it used to be there but I cannot be sure. The mod_python.load in sites-available references it and I know my server used to start. 

So my first question is:

is mod_python installable with apt-get? something like apt-get install mod_python?  If it is not this easy, what is the next easiest way to get mod_python working with apache?

---

### Post by snova on 2009-03-20
> **newbie.poster said:**
> is mod_python installable with apt-get? something like apt-get install mod_python?  If it is not this easy, what is the next easiest way to get mod_python working with apache?

Yes. It's in the **libapache2-mod-python** package.

---

### Post by newbie.poster on 2009-03-20
Thanks for the post.  I googled that's where it was so I reinstalled that just a little while ago.  That fixed my problem of not being able to start the webserver but now IO am running into a different problem.  When I go to:

[http://localhost/test.py](http://localhost/test.py)

I am prompted to either save the file or open it in a text editor. What I need is for the results of that file to display in the web browser.

---

### Post by Tibuda on 2009-03-21
Make sure the module is enabled and restart apache server```
sudo a2enmod python
sudo service apache2 restart
```

---

### Post by newbie.poster on 2009-03-23
Thanks for the help.  Both of those suggestions helped me out and the test page loads correctly now. Thanks again.

---

### Post by Megalomania on 2009-04-28
I was just trying to get a Django server back running and ran into this thread - however, I tried to install mod_python and got this:

# apt-get install libapache2-mod-python
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libapache2-mod-python is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libapache2-mod-python has no installation candidate

My sources.list is the default 9.04 install sources.list except that after a complete inability to find any packages with it drove me to look online I took the "us." off of all the "us.archive..." repos.  Is there a repository I'm missing?  Also noticeably absent according to apt is "make", so I'm guessing that I'm missing something.

---

