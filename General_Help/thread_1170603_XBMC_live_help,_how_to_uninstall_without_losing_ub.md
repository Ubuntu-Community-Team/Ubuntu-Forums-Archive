---
title: "XBMC live help, how to uninstall without losing ubuntu 9.04"
date: 2009-05-26
forum: General Help
---

### Post by keypox on 2009-05-26
So I wanted to try xbmc and the regular version wasnt working so i tired xbmc live. Not knowing it would get rid of ubuntu. 

How do i uninstall this xbmc live?  I dont want to have to reinstall ubuntu... again.

---

### Post by aeiah on 2009-05-26
the name kind of suggests its a livecd and hasnt touched your hard drive.. what exactly did you do? format your harddrive and install it over ubuntu or what?

---

### Post by keypox on 2009-05-26
> **aeiah said:**
> the name kind of suggests its a livecd and hasnt touched your hard drive.. what exactly did you do? format your harddrive and install it over ubuntu or what?

installed via synaptic

---

### Post by mediajunkie on 2009-05-30
Hi Keypox,

I also installed the xbmc live on my son's computer with the same result, 
a working XBMC , impressive and nice, but no way to boot to his normal computer system again.

This is what I did to fix it. 
Stay with me as it involves a few command-line commands, as Xbmc-live was so friendly to de-install gnome-desktop-manager (gdm) 

[open terminal screen] [ctrl + alt + F1]

log in with user that has sudo rights (the first installed user account during installation) 

then the following:

```
sudo apt-get remove xbmc xbmc-live xbmc-skin-* xbmc-*
```

```
sudo apt-get autoremove
```


Now you might want to change your sources list, and remove the 2 lines you've added earlier, to installed XBMC.


```
sudo nano /etc/apt/sources.list
```

delete these lines:

```
deb http://ppa.launchpad.net/team-xbmc/jaunty-ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/team-xbmc/jaunty-ppa/ubuntu jaunty main
```


Optionally: rebuild your list index by:

```
sudo update-apt-xapian-index
```

Remove xbmc-live from your /etc/init.d directory

```
sudo rm /etc/init.d/xbmc-live
```

Re-install your Gnome Desktop manager 

```
sudo apt-get install gdm
```

Optionally: Re-install guest sessions

```
sudo apt-get install gdm-guest-session
```

Optionally: Re-install fast user switch applet

```
sudo apt-get install fast-user-switch-applet
```

Finally: Reboot:

```
sudo reboot
```

your system should now boot normally and ask for your user name and password. 

hope it works for you.

---

### Post by rightasrain on 2009-09-22
Thanks for posting this. I had the same problem and it worked perfectly.

---

### Post by daveisearly on 2010-02-27
those instructions work fine.  Tvm to MediaJunkie.

for those who do not know, the alternative way to execute these command is to choose 'Recovery mode' when first boot up, then choose the enter root with internet access option. 

You can then execute all of these commands as root (without the sudo command).

Also fast-user-switch-applet is now part of the core gdm package - so no need for that option.

---

