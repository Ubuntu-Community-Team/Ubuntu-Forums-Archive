---
title: "GUI for 8.10 Server"
date: 2009-02-25
forum: General Help
---

### Post by JR-XXL on 2009-02-25
I'm trying to install a GUI for my 8.10 server, but i am having no luck.

I tried :

sudo aptitude install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl

(that went through with no problems)

then I ran :

wget [http://garr.dl.sourceforge.net/sourceforge/webadmin/webmin_1.441_all.deb](http://garr.dl.sourceforge.net/sourceforge/webadmin/webmin_1.441_all.deb)

And I get : 
Resolving garr.dl.sourceforge.net....
then it fails and says, failed: name or service not known.

any ideas ?

---

### Post by kerry_s on 2009-02-25
sudo apt-get install xorg

then you need to decide what kind of gui you want, than apt-get it.
example:
sudo apt-get install lxde
or
sudo apt-get install fluxbox

then just> startx

---

### Post by JR-XXL on 2009-02-25
kerry_s

Thanks for the reply

when I run:
sudo apt-get install xorg

i get:
reading package lists : Done 
Building dependency tree
Reading state infornmation...Done
E: Couldn't find package xorg

---

### Post by HydroModeler on 2009-02-25
After I do a new server install I run the following.  This does not make the desktop start by default because I prefer that it not be running most of the time.

sudo apt-get install ubuntu-desktop
sudo apt-get install gdm
sudo /etc/init.d/gdm start
sudo dkpg-reconfigure xserver-xorg

---

### Post by kerry_s on 2009-02-26
> **JR-XXL said:**
> kerry_s

Thanks for the reply

when I run:
sudo apt-get install xorg

i get:
reading package lists : Done 
Building dependency tree
Reading state infornmation...Done
E: Couldn't find package xorg

have you run> apt-get update
post your /etc/apt/sources.list sounds like you don't have all your repos on.

---

