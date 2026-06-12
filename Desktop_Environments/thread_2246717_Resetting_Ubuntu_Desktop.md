---
title: "Resetting Ubuntu Desktop"
date: 2014-10-02
forum: Desktop Environments
---

### Post by Chirayu_Patel on 2014-10-02
How do I revert back to original desktop on my 14.04.1 

Testing new gnome doesn't work too well and icons get screwed along with lots of other glitches.

---

### Post by deadflowr on 2014-10-02
I moved your post to it's own thread.

But getting to the problem, when you login, at the login screen where you input your password, you should be able to switch desktop sessions.
Ubuntu's default logn screen will have a box with a username and a password in this box in the top right corner should be an icon, click on the icon and you should get options for the different desktops you have installed. Ubuntu's default is Ubuntu.

---

### Post by PratterFak on 2014-10-05
I ran into a Gnome desktop issue on Ubuntu 14.04 as well.

I did a clean install of Ubuntu 14.04 and got everything updated. I then installed the Gnome desktop which works; however, it took over as the default when you go to choose a desktop. I also now always get the gnome splash when rebooting- even after I entire deleted Gnome. Another issue it caused- once I boot to Ubuntu, my screen is totally black along with top bar (also causes issues with any window). I must log off and log back on using Ubuntu to resolve.

The only way I could get Ubuntu as the "default" on the login screen is to add user-session=ubuntu in the /etc/lightdm/lightdm.conf file. I also added greeter-session=unity-greeter, but I still get the gnome greeter and the desktop issue remains where I have to log off and log back on to fix.

Any help would be appreciated.

---

### Post by Frogs Hair on 2014-10-05
The login  session badge displays the last session used . For example if use Gnome that is what I will see it the next login unless it is changed maually by clicking the session badge.

---

### Post by PratterFak on 2014-10-05
That is understood, but mine is the gnome one no matter if I used Ubuntu last. It also remains after I have deleted Gnome along with the additional issues above. I never had an issue on 12.04, but apparently they don't play well together on 14.04 because there is definitely an issue.

---

### Post by BJones007 on 2014-10-05
Try this: 

```
 sudo dpkg --configure -a 
```

---

### Post by Frogs Hair on 2014-10-05
What gnome packages were installed ? I install the gnome-shell, extensions and tweak-tool and select the _lightdm_ option during installation and have never seen this problem before.

---

### Post by deadflowr on 2014-10-05
> **PratterFak said:**
> I ran into a Gnome desktop issue on Ubuntu 14.04 as well.

I did a clean install of Ubuntu 14.04 and got everything updated. I then installed the Gnome desktop which works; however, it took over as the default when you go to choose a desktop. I also now always get the gnome splash when rebooting- even after I entire deleted Gnome. Another issue it caused- once I boot to Ubuntu, my screen is totally black along with top bar (also causes issues with any window). I must log off and log back on using Ubuntu to resolve.

The only way I could get Ubuntu as the "default" on the login screen is to add user-session=ubuntu in the /etc/lightdm/lightdm.conf file. I also added greeter-session=unity-greeter, but I still get the gnome greeter and the desktop issue remains where I have to log off and log back on to fix.

Any help would be appreciated.

Lightdm in 14.04 does not work the same way that it does in 12.04
In 12.04 you could, as you did, simply edit the lightdm.conf file.
But in 14.04 you need to make a file and place it in the /etc/lightdm/lightdm.conf.d folder.
(You may need to make the lightdm.conf.d folder, I can't remember)
The file simply need to be called something like 50_myconfig.conf, But can be custom to your own, like 15_Trusty-Login.conf.
You would preface the file with the [SeatDefaults] line, and then add those lines you have to it.
Then save.
Form here
[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

As for the session reverting to gnome, I haven't had that, and I switch between unity, gnome-flashback(both compiz and metacity) and gnome-shell, a lot. And they always list the last session used as the one I see in the login. Is it loading the unity-greeter or another greeter; most likely the lightdm-gtk-greeter, which it tweaked by the various other flavors to fit their tastes, I presume gnome tweaks it as well.(Heavy on the presume)

---

### Post by Frogs Hair on 2014-10-05
Selecting the gdm rather than lightdm changes the login behavior  and is more like a full gnome installation but I have never selected gdm. I have also never  edited any file related to lightdm and have no suggestions.

Edit: see this post.  [http://itsfoss.com/switch-gdm-and-lightdm-in-ubuntu-14-04/](http://itsfoss.com/switch-gdm-and-lightdm-in-ubuntu-14-04/)

---

### Post by PratterFak on 2014-10-06
Thank you all for the responses!

All i installed was ***sudo apt-get install gnome-shell ubuntu-gnome-desktop*** and selected lightdm. It flaked out after that. 

Once that happened, I noticed that gnome desktop is now on the software center, but it didn't say I had it installed- odd. So, I uninstalled what I did and installed it from the software center- issue remained. After that I just went off, trying a bunch of different things.

I may try a couple more things when I get home, but at this point, I'm just considering doing another clean install of Ubuntu 14.04 and maybe trying to just install gnome desktop from the software center first- maybe that is the best option?

Thanks again for all the replies!

*The bummer is that I only need the gnome desktop to be able to use citrix to work remotely since it only has the top bar which I can hide. Unfortunately with unity, it off-sets the resolution doing a citrix remote computer login.

---

### Post by Frogs Hair on 2014-10-06
I'm wondering if that is the desktop environment package for official Ubuntu Gnome flavor which is very different than the  installations I've done for just the basic Gnome Shell + extensions. Like the difference between installing XFCE and the Xubuntu desktop.

---

### Post by PratterFak on 2014-10-06
When I installed it from the software center, it seemed to be the same as the shell and extensions. It just didn't fix my existing issue. However, I do remember having more in the login menu- like flashback.

---

### Post by Frogs Hair on 2014-10-06
I can't locate the package you installed because both computers are now running the development version, but it could explain why Gnome is now default. Flash-Back is now a separate session.  With the fall-back session, the  Gnome panel and related packages used to be a dependencies of alacarte/main menu and that is no-longer the case and installing the tweak tool would also install the gnome panel on older Ubuntu versions.

---

### Post by PratterFak on 2014-10-06
So, I did the clean install of Ubuntu 14.04, then installed the Gnome desktop from the software center. It now works perfectly! I'm still not used to so much being in the software center- sometimes even forget it's there. :) I only have a few things these days that I have to install via terminal- nice!

Thanks!

---

