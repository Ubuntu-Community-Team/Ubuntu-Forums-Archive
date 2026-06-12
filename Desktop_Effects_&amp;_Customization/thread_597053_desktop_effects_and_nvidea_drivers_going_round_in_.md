---
title: "desktop effects and nvidea drivers going round in circles + driving me mad"
date: 2007-10-30
forum: Desktop Effects &amp; Customization
---

### Post by jonnywombat on 2007-10-30
I am trying to enable desktop effects on  gutsy.

Whenever I try i get an error message saying unable to enable...blah blah..

Did some searching on here and from the info I found I did the following..

Installed to xgl package, installed the desktop effects advanced manager..

Now every time I try to enable desktop effects I get a pop up saying I need to enable a restricted driver. I check the box to do this and then restart..

As the machine boot I get the "low graphics mode" box I select the appropirate settings and then continue..

The desktop tries to start a few times before eventually getting going, but the settings have defaulted back to 800x600 generic monitor and the vesa driver.

My spec is Athlon 64 3400+, 1.5 gb ram, gigabyte K8 mobo on "via" chipset, and pny 7600 nvidia grafix card.

typeing compiz in terminal produces

:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
 
Like I said abouve I have already instaled the xgl package and hence I go around in circles not getting any nearer a solution...

---

### Post by jonnywombat on 2007-10-30
OK.. I solved this myself...

I noted a few threads which spoke of various issues when upgrading from feisty to gutsy...which is what I had done also.
So I had an alternative cd with gutsy on (my laptop would not upgrade online or via live cd), and I did a fresh install..

Low and behold all works just fine...

:)

---

### Post by Blahzay on 2007-10-30
Thats weird cause i did a fresh install and got the exact same issue. And no solution yet....

---

### Post by Zorael on 2007-10-30
Um, okay.

Whenever there's issues with X (the graphical interface) not wanting to start with an ATI or an Nvidia card, Envy is your friend.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Download, install, run. It will download and install fresh drivers for you. You will need to run the script again if/when you upgrade to a newer kernel, though.

```
$ sudo dpkg -i envy*.deb
(if spam of missing dependencies ->) $ sudo apt-get install -f
```

---

### Post by dbtx on 2007-11-02
I've been having problems with nvidia since upgrading, and thought I'd try this Envy thing, but when I try the envy dpkg as suggested, I get:

dpkg: error processing envy*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 envy*.deb

What do I need to do?

---

### Post by KingWilliam on 2007-11-02
If you have troubles with a low resolution after installing the restricted nVidia drivers, check this link. It helped me out to with that problem. It seems that you have to add something manually to yoiur xorg.conf file. 

Watch out with envy and the nvidia driver. It is possible that it messes things up. You dont need it so better dont use it. ;)

 [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/91292](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/91292)

---

### Post by Zorael on 2007-11-02
> **dbtx said:**
> I've been having problems with nvidia since upgrading, and thought I'd try this Envy thing, but when I try the envy dpkg as suggested, I get:

dpkg: error processing envy*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 envy*.deb

What do I need to do?

You don't seem to be in the directory where your downloaded envy deb file is. :>

If you're running Ubuntu (or other flavours and you've installed Gdebi), you can just double-click on the file. Save it to your Desktop, double-click, and you should be on your way.

If it complains about "unsatisfiable dependencies" when you do it the graphical way, you don't have the univserse (I believe it's that one) repository enabled. You can fix this in Software Sources - from the Add/Remove Programs application, or from Synaptic.

If it  complains when you do it from a terminal, do this:
```
$ sudo apt-get install -f
```
Again, if it can't find one or more of the dependencies, you need to check your software sources.

---

### Post by Zorael on 2007-11-02
> **KingWilliam said:**
> If you have troubles with a low resolution after installing the restricted nVidia drivers, check this link. It helped me out to with that problem. It seems that you have to add something manually to yoiur xorg.conf file. 

Watch out with envy and the nvidia driver. It is possible that it messes things up. You dont need it so better dont use it. ;)

 [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/91292](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/91292)

Yes, Envy is not supported by Canonical, so it's one of those iffy deals. :)

For instance, if you upgrade your kernel, you **will** have to enter a command from the terminal. Only one, though. Write it down, if you wish.

Log in, and then do:
```
$ sudo envy -t
```
...then ask it to install your driver again.

---

