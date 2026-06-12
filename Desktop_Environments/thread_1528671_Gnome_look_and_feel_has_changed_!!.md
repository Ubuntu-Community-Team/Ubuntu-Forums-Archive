---
title: "Gnome look and feel has changed !!"
date: 2010-07-11
forum: Desktop Environments
---

### Post by chinmaya_n on 2010-07-11
Some how my whole /(root)  space has gone 0 !
Then after next restart it showed me that [COLOR="RoyalBlue"]"gnome-power-manger settings are not configured correctly"[/COLOR] and it didnt allowed me to login.
So I searched google and executed some commands to rescue it !: (not in order, but individually )```

sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get clean
sudo apt-get --reinstall install ubuntu-desktop

and also making /var/lib/gconf/defaults directory manually !!
```

After that I observed that my root space is 0 !! I was shocked and I removed many files and recovred around 17GB ! :)

Then It booted nicely into the OS but Now everything has changed:
1.No desktop background
2.AWN is not loading
3.Window manager is not selecting any themes,icons 

 Like this my system has got ruined !!
Note: After recovering I 've replaced the old defaults directory (/var/lib/gconf/defaults). [Thank god ! I 've taken a backup of that folder before changing]
Please see the attachments. You can see theme,wallpaper not being applied even after selection.
And AWN giving this error: 
```
$ avant-window-navigator 

(avant-window-navigator:3430): GConf-CRITICAL **: gconf_value_get_list: assertion `value != NULL' failed

** ERROR **: No panels to create! 
**  Please check that the gconf-schema is installed.
**  You might also try to run `killall gconfd-2`.
aborting...
Aborted

```And Compiz is working fine !

Thanx in Advance.

---

### Post by hansdown on 2010-07-11
Hi chinmaya_n.

Is this an upgrade?

If so, some of your apps may need to be installed.

One thing;

```
sudo apt-get --reinstall install ubuntu-desktop

```

does not reinstall ubuntu-desktop, if it is not removed first.

Try installing from synaptic.

If it appears to be installed, try,

```
sudo apt-get remove ubuntu-desktop && install ubuntu-desktop

```

---

### Post by chinmaya_n on 2010-07-11
Hi hansdown,

I 've done what you said. But no-use !!
Anybody help please !!

---

### Post by hansdown on 2010-07-11
I was just rereading your first post.

It says to try 

```
killall gconfd-2
```

---

### Post by chinmaya_n on 2010-07-11
Hey.... I did it, No use.... !
But I 've observed something interesting in gconf-editor.
See the attachment.
It has "defaults_old".. but all the values in it are 'novalue'
And it has my previous settings in rest of gconf-editor.
Is something we can do with this?

---

### Post by hansdown on 2010-07-12
O.K. I just installed avant window navigator, and the default install, should look like the screenshot.

I'm still trying to figure the navigation out, and it clashes with my cairo dock a little.

Can you look inside your

```
schemas
``` 

folder?

---

### Post by chinmaya_n on 2010-07-12
HI

Let AWN go...

Please help me with themes and also the worst look I 've now!!
I 've attached some images of gconf-editor.

Those in defautls_old is not present in the remaining.... 
You can see the attached images...

Plz help me...
Does anyone had similar problem before!!? :(

---

### Post by hansdown on 2010-07-12
There is a bug report, for this message:

```
 GConf-CRITICAL **: gconf_value_get_list: assertion `value != NULL' failed
```

[https://bugs.launchpad.net/awn/+bug/555963](https://bugs.launchpad.net/awn/+bug/555963)

Also this:

[https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/514134](https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/514134)

I don't know, if a fix is near.

More links.

[http://www.google.com/search?client=ubuntu&channel=fs&q=+GConf-CRITICAL+**%3A+gconf_value_get_list%3A+assertion+%60value+!%3D+NULL%27+failed&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=+GConf-CRITICAL+**%3A+gconf_value_get_list%3A+assertion+%60value+!%3D+NULL%27+failed&ie=utf-8&oe=utf-8)

---

### Post by chinmaya_n on 2010-07-13
Alright... :(

Can I reinstall my GUI ?? (HOW??)

Will this work....?

---

### Post by hansdown on 2010-07-13
> **chinmaya_n said:**
> Alright... :(

Can I reinstall my GUI ?? (HOW??)

Will this work....?



```
sudo apt-get install ubuntu-desktop
```

```
sudo apt-get install nautilus
```

---

### Post by chinmaya_n on 2010-07-16
> **hansdown said:**
> ```
sudo apt-get install ubuntu-desktop

sudo apt-get install nautilus
```

didn't work !! :(
Same thing continued !!

Any other Ideas ??

---

### Post by chinmaya_n on 2010-07-16
> **hansdown said:**
> There is a bug report, for this message:

```
 GConf-CRITICAL **: gconf_value_get_list: assertion `value != NULL' failed
```

[https://bugs.launchpad.net/awn/+bug/555963](https://bugs.launchpad.net/awn/+bug/555963)

Also this:

[https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/514134](https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/514134)

I don't know, if a fix is near.


Will this work it I degrade to the old version of "gconf"... I remember, that I upgraded system before this happened (gconf too) !! :(
How to do that??

---

### Post by hansdown on 2010-07-16
> **chinmaya_n said:**
> Will this work it I degrade to the old version of "gconf"... I remember, that I upgraded system before this happened (gconf too) !! :(
How to do that??

I would be guessing, at best, but I will find out, or my name isn't sam.:)

Seriously, could we go back to your root question?

Please post

```
sudo df -h
```

Would you consider a fresh install of 10.04?

---

### Post by infamous-online on 2010-07-17
So what's your theme there, it looks like windows vista/7 like a bit there? I was asking cause it looks pretty good, and I was thinking about trying it out?

---

### Post by chinmaya_n on 2010-07-17
> **hansdown said:**
> 
Seriously, could we go back to your root question?

Please post

```
sudo df -h
```
Sure ! Now I 've lots of space...
```
$ sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              37G   19G   17G  53% /
udev                  2.0G  264K  2.0G   1% /dev
none                  2.0G  548K  2.0G   1% /dev/shm
none                  2.0G  204K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sda7              54G   50G  3.5G  94% /media/Disk
/dev/sda5             184G  170G   11G  95% /home

```
> **hansdown said:**
> 
Would you consider a fresh install of 10.04?
Sure.. but I wonder If there is a way to have all my apps intact !! Can this be done !!??

---

### Post by chinmaya_n on 2010-07-17
> **infamous-online said:**
> So what's your theme there, it looks like windows vista/7 like a bit there? I was asking cause it looks pretty good, and I was thinking about trying it out?

Are you talking about that windows7 current programs bar ??
It is [dockbarX]("http://gnome-look.org/content/show.php/DockbarX?content=101604"). You can read how to install that in that page only!!
Download those extra themes too.... Basic dockbarX will not look great ! My favorite theme is "Tonky"

---

### Post by chinmaya_n on 2010-07-29
Finally....... I installed 10.04. !! 
(I don't like reinstalling an os, b'se it is a Mic' Sof' life)

---

### Post by hansdown on 2010-07-29
Glad you got things sorted, chinmaya_n.

---

