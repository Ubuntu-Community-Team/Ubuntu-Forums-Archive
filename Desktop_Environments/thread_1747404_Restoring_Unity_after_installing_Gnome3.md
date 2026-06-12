---
title: "Restoring Unity after installing Gnome3"
date: 2011-05-02
forum: Desktop Environments
---

### Post by alphageek89 on 2011-05-02
Hi . I used this article to install gnome3
[http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3](http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3)

Then after much difficulty I was able to login in to gnome3. Soon i realized it was weird and wanted to go back to unity . So i followed the steps in that article namely:

```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:gnome3-team/gnome3

```

Then i did 
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

Now when i go to login the login screen looks like the default unity splash screen but my shell options are :

gnome openbox
ldxe
openbox 
default

How can i log in using unity again ?

---

### Post by alphageek89 on 2011-05-02
I'm currently logged in through the ldxe shell. The gnome openbox and openbox don't really work.

---

### Post by arcterex on 2011-05-02
I think you need to re-install the gdm session files in /usr/share/xsessions

I had the same issue (well, similar) when I did the same thing as you and luckily had a another 11.04 install on a VM that I was able to copy the files across from.  I will attach a tarball of /usr/share/xsessions for you, I just put them in that directory and re-logged in and voila, back up and working.

---

### Post by Nerotriple6 on 2011-05-02
Thanks for this.

3 reinstalls later and I was afraid to try Gnome 3 again. If this works I will make another effort soon. Last reinstall was today.. :p

I was left with no Gnome and no Unity after purging Gnome 3.

---

### Post by alphageek89 on 2011-05-03
I copied the files in the correct directory. When I restart I get the options but I get a error:No Session Options

---

### Post by alphageek89 on 2011-05-03
sudo apt-get install ubuntu-desktop 

This worked !

---

