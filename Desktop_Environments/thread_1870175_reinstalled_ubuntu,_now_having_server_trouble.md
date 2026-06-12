---
title: "reinstalled ubuntu, now having server trouble"
date: 2011-10-26
forum: Desktop Environments
---

### Post by stunet on 2011-10-26
hi,

I upgraded my ubuntu to 11.10 and found it was not what i hoped it would be so, so i went  to 10.04 LTS

thats all fine, but my issue is my web server setup, which even though i renamed the computer, i can still access my server by the old computer name. This has seemed to caused some issue with a few pages on my server as they now are not working correctly(possibly a cache issue somewhere.

my question is, is there a way to clear the DNS cache? i know how to do it in windows, but never has to do it for linux.

thanks :)

---

### Post by collisionystm on 2011-10-26
> **stunet said:**
> hi,

I upgraded my ubuntu to 11.10 and found it was not what i hoped it would be so, so i went  to 10.04 LTS

thats all fine, but my issue is my web server setup, which even though i renamed the computer, i can still access my server by the old computer name. This has seemed to caused some issue with a few pages on my server as they now are not working correctly(possibly a cache issue somewhere.

my question is, is there a way to clear the DNS cache? i know how to do it in windows, but never has to do it for linux.

thanks :)


Just to clarify things... The Ubuntu 10.04 you just installed is your Web Server? Or another box is

---

### Post by stunet on 2011-10-26
yes the 10.04 is my web server

---

### Post by collisionystm on 2011-10-26
> **stunet said:**
> yes the 10.04 is my web server

Okay.

So you just copied your /var/www directory back to the 10.04 and re-installed LAMP?

What kind of router do you have? Is that at your house?

---

### Post by stunet on 2011-10-26
i backed up everything and reinstalled fresh. though i dont use the default directory, i just use the home directory, seeing as its just a dev server and all.

the setup is at my house, i just have a regular AT&T router, nothing fancy.

---

### Post by collisionystm on 2011-10-26
if you can still access the server by its old name, ( I assume in a web page? ) There is some kind of DNS record somewhere pointing to it.

Check inside your AT&T router.

---

### Post by stunet on 2011-10-26
I'll do that, I figure its something like that.

thanks for your help.

---

### Post by collisionystm on 2011-10-26
> **stunet said:**
> I'll do that, I figure its something like that.

thanks for your help.

Yup... no problem. When you figure out what it is, just mark this thread solved!

---

