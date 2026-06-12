---
title: "KDE doesn't work, just displays a big ol' black screen!"
date: 2010-04-30
forum: Desktop Environments
---

### Post by netro_grant on 2010-04-30
Hey,

My main desktop environment is Gnome however being the curious little geek that I am I fancied messing about with KDE for a bit. I logged out, changed my session type to 'KDE' then logged in. it displayed the KDE splash/load screen then provided me with an ultra useful big black screen. No wallpaper, no menu's, no desktop. The computer runs fine and when I hit the power button a little window comes up with the option to log off etc, but the desktop just seems to have disappeared!

Any help would be appreciated.

Thanks,

Grant

-----System Info--------
Ubuntu 10.04 lucid lynx 32bit
intel dual core (NOT core 2 duo)
2Gb RAM
On board intel graphics GM945 (I think)

For any other specs needed you can look up the
specs for a Compaq Presario A935EM. Mainly
because thats what I have :):)
------------------------

---

### Post by netro_grant on 2010-04-30
should probably mention that the mouse is still visible, and still works. not much I can do with the mouse when I don't have a desktop tho :(

Ta,

Grant

---

### Post by pcrat on 2010-04-30
yep tried kde just loads a couple icons then thats it,, black screen,, mouse cursor,,, let it sit for about 12 minutes.. still no go..

---

### Post by jopojojo on 2010-05-01
Hi,

I had exactly the same problem when I tried KDE. GNOME works fine, but when I select KDE at login, the screen goes black and that's it. I can run an application by pressing ALT+F2, but that is not quite what I want. That shows anyway that the system itself is running but no graphics:confused:

My laptop is Dell Latitude D 620 with Genuine Intel(R) CPU           T2300  @ 1.66GHz and the Graphics Chip is Intel Corporation Mobile 945GM/GMS, 943/940GML Express  Integrated Graphics Controller

Unfortunately I can offer no help at this point. Anyway, you are not the only one who has had this issue.

J

---

### Post by jkbrennan77 on 2010-05-01
Same problem here.  Upgraded from Koala using the GUI upgrade and when the system rebooted I get no desktop.  alt+f2 does work (thanks for that) and even allows me to run Chrome and Dolphin at least.  alt+tab also brings up a 3D task switcher.

Maybe this is the ultra-minimalist version of KDE :)

---

### Post by nerdy_kid on 2010-05-01
> **jkbrennan77 said:**
> Same problem here.  Upgraded from Koala using the GUI upgrade and when the system rebooted I get no desktop.  alt+f2 does work (thanks for that) and even allows me to run Chrome and Dolphin at least.  alt+tab also brings up a 3D task switcher.

Maybe this is the ultra-minimalist version of KDE :)

lol

anyone try hitting altf2 and running plasma-desktop?

---

### Post by jkbrennan77 on 2010-05-01
Thanks!  Tried running plasma-desktop and it didn't run.  apt-get installed plasma-desktop (it also installed kdebase-workspace) and I have a desktop again.  My panel and other configuration settings all appear to still be there.

---

### Post by utnubuuser on 2010-05-02
Is this an issue when installing Kubuntu-Desktop, or when installing KDE?

---

### Post by Majik_420 on 2010-05-02
Same problem here. Dell Inspiron 1525. 

Just got my computer back a month ago and I was loving Karmic. Saw the upgrade for Lucid and thought for half a second that maybe I should wait a few days or a week to avoid any first run bugs. 

Ate that one. got that black screen like a few others, but I knew that something was still working cuz the volume control was still there and my Wallet still comes up at startup. 

First I couldn't figure anything out in the desktop, so i ran the onboard diagnostic from my boot menu and it said that theres something wrong with my hard drive so I thought that was the problem.

But there was that nagging feeling because the volume and my wallet still came up, so I started clicking every little menu button I could and navigated from my wallet to window behavior to help to kde.org and got some internet action going.

That alt f2 thing is cool thanks for that.

but as far as the plasma-desktop command I have nothing still, altf2 and konsole.

I'll keep reading and post anything I find out here, because I still have no desktop environment even after installing plasma-desktop...

*edit-damn guess I gotta run it after I install it. My bad. Hopefully it will automatically run from now on...

---

### Post by nerdy_kid on 2010-05-03
if plasma didnt get installed thats a kubuntu-desktop issue (i would think anyway).  try
```

sudo apt-get install kde-standard

```

---

### Post by CaptainPasty on 2010-05-03
Thanks nerdy_kid, I can confirm this has sorted it for me. Can't believe I never thought of reinstalling KDE myself, but hey ho...

---

### Post by jopojojo on 2010-05-03
Thanks nerdy_kid! I have also  tried the
 
sudo apt-get install kde-standard 

command and after restarting KDE works now:D

Hopefully it works for you guys and gals as well!

---

### Post by netro_grant on 2010-05-03
installed plasma-desktop and everything worked great. thanks very much for all your help :)

---

### Post by woofleboofle on 2010-05-31
Hey i used alt+F2 to enter application finder thing. I typed 'login', and it searched for the login settings, i entered into it, and changed back to the Gnome environment. Used ctrl+alt+dlt to log out. (For anyone who accidentally switched to KDE and got the black screen error).

---

### Post by john@ukgillies.com on 2010-12-10
I know that this is relatively old, but I have a similar problem with Maverick!

If I add desktops then all goes black! KDE is still running and all the apps can be activated from the CLI.

plasma-desktop brings the desktop back, but this is not permanent. Next login the same thing.

Anyone know if this has been sorted?

Thanks,

John

---

### Post by pbremner on 2011-01-30
Exactly the same happened to me (Presario CQ61) I battled to get gnome back and could not find any help on forums. I am a relative Ubuntu newbie and certainly not a command line jockey. I tried the Alt-F2 thing, selected Logon in the list and set it back to gnome instead of KDE, rebooted and Wallahhh! all worked fine - back in gnome. Moral of the story is if it aint broke dont fix it. Rather mess around on a non critical machine

---

