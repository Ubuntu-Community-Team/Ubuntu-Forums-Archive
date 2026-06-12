---
title: "Using XAMPP"
date: 2009-02-12
forum: General Help
---

### Post by Wovaki on 2009-02-12
I just installed XAMPP yesterday, I got it running fine and everything, but I cannot use it to test my php file.

Whenever I try to move any of my PHP files into the htdocs or where ever it is supposed to go it says I don't have the privileges to do that.

I need to be root to do that it says, but I tried logging in with root and it always says "Authentication Failed".

Could somebody please help me out with this?
Thanks

---

### Post by Wovaki on 2009-02-12
Can't anyone help me with my problem?

Thanks

---

### Post by Dr Small on 2009-02-12
Assuming you are on Ubuntu with Gnome, run:
```
gksudo nautilus
```

And browse to the /opt/lampp/htdocs directory. Now you can create, edit, delete and move files to this directory because you have root privileges.

---

### Post by Wovaki on 2009-02-12
So will I have to do this everytime I want to add a webpage to XAMPP?

---

### Post by jerryrowe on 2009-06-23
This is monumentally inconvenient...Why can't I, without having to make any changes, just test some PHP files?

This is supposed to be easier, not more difficult.

---

### Post by Celauran on 2009-06-23
> **jerryrowe said:**
> This is monumentally inconvenient...Why can't I, without having to make any changes, just test some PHP files?

This is supposed to be easier, not more difficult.

Have you tried changing Apache's DocumentRoot to a directory where you have write access? Might make life easier.

---

### Post by jerryrowe on 2009-06-23
I didn't know that was possible, and XAMPP's documentation only tells you how to install it-- not one word about how to use it.

I would be very appreciative if you could tell me how to do that!

Also, I went in as root (using that nautilus command the Dr mentioned), and changed the ownership of every folder I could find to my user name.  Unfortunately, you do have to manually change ownership for each folder, one at a time, as far as I can tell, and subfolders do not inherrently change ownership.

---

### Post by Celauran on 2009-06-23
You can recursively change ownerships using chown -R, though I'd be _very_ careful doing this. I'm not sure what you've changed already but, to be quite frank, it sounds ominous.

As for changing the DocumentRoot, it's just a matter of editing one text file. I've never used XAMPP, as I just install Apache + MySQL + PHP on individually. The default location is /etc/apache2/sites-enabled/000-default

You may also want to consider creating virtual hosts and specifying separate DocumentRoots for each, depending on the numbber and magnitude of projects you'll be working on.

---

### Post by jerryrowe on 2009-06-23
Heh!  You're right about the dark forboding with the ownership permissions...I'm just giving Ubuntu a trial run as a developing environment (which is a really good experience with BlueFish).  I intend to reformat once this particular job is done, which won't be long at all.

I've done a lot of coding but not any (until now) stuff with servers and permissions and stuff...so I'm really not even sure what is going on with Virtual Servers.  The best tutorial I was able to find on it was written by some guy whose native language was obviously Russian, a language in which I am not capable of saying three words.

Do you know where I could find a good tutorial or primer on the subject?  I appreciate your patience, Celauran, and I apologize for both my verbose nature and general noobishness. :)  During school, I did great in symbolic logic and programming theory, but some of this stuff is really just not intuitive.

---

### Post by Celauran on 2009-06-23
[Here](https://help.ubuntu.com/community/ApacheMySQLPHP) is a great tutorial for setting up a LAMP server. [Here](http://httpd.apache.org/docs/2.0/vhosts/) is Apache's documentation for setting up virtual hosts. That should be enough to get you started in the right direction, at least.

---

