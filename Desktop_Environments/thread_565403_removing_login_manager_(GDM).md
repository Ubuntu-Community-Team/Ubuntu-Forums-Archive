---
title: "removing login manager (GDM)"
date: 2007-10-02
forum: Desktop Environments
---

### Post by jimmywu013 on 2007-10-02
Hi,

I'm relatively new to Ubuntu, and I have 7.04 installed on a rather old machine 
Specs are Pentium 3, 433? MHz, 256 M RAM, ~1 G swap
It runs well, but it can get sluggish at times.
I read in the Ubuntu community documentation that not using a login manager can decrease load on system resources.  
I take this to mean sudo apt-get remove gdm, right?
Before I go and type that though, I want to make sure I know what I'm doing.
Will removing gdm have a significant improvement on performance, and will it break anything?
Also, I assume that if I do get rid of gdm, I will have to do a console login and then run startx, and then I should be at my usual gnome desktop.  Is that right?

Thanks for the help

Jimmy

---

### Post by kerry_s on 2007-10-02
gnome is dog slow. i have just about the same specs. if you want to get that rig up to speed you should go debian. i would say debian custom, but you sound like your still learning. so->

[http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso)

will help, for now.

---

### Post by Rui Pais on 2007-10-02
> **jimmywu013 said:**
> Hi,

I'm relatively new to Ubuntu, and I have 7.04 installed on a rather old machine 
Specs are Pentium 3, 433? MHz, 256 M RAM, ~1 G swap
It runs well, but it can get sluggish at times.
I read in the Ubuntu community documentation that not using a login manager can decrease load on system resources.  
I take this to mean sudo apt-get remove gdm, right?
Before I go and type that though, I want to make sure I know what I'm doing.
Will removing gdm have a significant improvement on performance, and will it break anything?
Also, I assume that if I do get rid of gdm, I will have to do a console login and then run startx, and then I should be at my usual gnome desktop.  Is that right?

Thanks for the help

Jimmy

it's not GDM that it's heavy (although there are lighter options as login managers...), it's X itself and DE (Gnome/Kde) that can be heavy. As long as you are logged, gdm will not be running.

You don't need to install a full other distro. You can try xfce4 from your already installed system:
```
sudo apt-get install xubuntu-desktop
```

or even lighter:
```
sudo apt-get install fluxbox
```

There are a thousand others light DE/WM, the most used, OpenBox, enlightenment, e17, WindowMaker. Just pick one. :)

Edit: To login to a new environment use GDM (it's useful after all ;)) to choose the one by clicking on 'Sessions'

---

### Post by jimmywu013 on 2007-10-02
Thanks for the replies
I think I'm going to go install fluxbox as soon as I get a chance to get back to my ubuntu box, but I still have a few questions

I know that there are some apps that depend on gnome libraries - including (correct me if i'm wrong) openoffice, firefox, and all the gnome administration apps that begin with gnome- whatever.  My understanding is that since I have the gnome libraries installed, I will still be able to use these apps in fluxbox, but does that defeat the purpose of having a lighter desktop environment, since gnome (or pieces of it) will be running anyway?  Is this right or I am way off base?

Also, I want to remove GDM anyway, as I'm trying to move as much towards bare minimum as possible.  Are there any caveats to watch out for before I go ahead and sudo apt-get remove it?  It would suck if I uninstalled it and found out I had broken my graphical desktop.

Thanks again,

Jimmy

---

### Post by Rui Pais on 2007-10-02
> **jimmywu013 said:**
> ...
I know that there are some apps that depend on gnome libraries - including (correct me if i'm wrong) openoffice, firefox, and all the gnome administration apps that begin with gnome- whatever.  My understanding is that since I have the gnome libraries installed, I will still be able to use these apps in fluxbox, but does that defeat the purpose of having a lighter desktop environment, since gnome (or pieces of it) will be running anyway?  Is this right or I am way off base?
Yes, you will be able to run any installed app from fluxbox. 
The economy in resources came from not have constantly running gnome-session, gnome-daemons, gnome-panels, etc. that are heavy. 
The boring part is that some applications (not firefox or openoffice, but nautilus or other gnome applications) will load gtk/gnome libs or even bring back some gnome-daemons.
Thats for me one of the boring aspects of the extreme-light WM. They are fast to load but then the time to load some apps may be (or at least feels) much longer, because the lot of stuff not loaded or cached.

Because of that, I prefer the medium sized DEs like xfce4 or (better to my taste) enlightenment. 
A good choice is trying to replace heavy apps for lighter equivalents. 
Like: rox, pcmanFM, thunar,etc. for nautilus; sylpheed or thunderbird instead evolution; opera, kazehakase, dillo, etc. instead of Firefox, etc... 
Some gnome apps are still lighter then the main used by Ubuntu, abiword+gnumeric is lighter then OpenOffice, epiphany is lighter then Firefox, etc...

> 
Also, I want to remove GDM anyway, as I'm trying to move as much towards bare minimum as possible.  Are there any caveats to watch out for before I go ahead and sudo apt-get remove it?  It would suck if I uninstalled it and found out I had broken my graphical desktop.


Doing such a thing is healthy and it will teach something on how things work. 
But keep in mind that an app that is installed but not running only waste space disk, not resources. 
GDM is a special case of app that runs when user is not logged (so he/she don't need any resources) and stops when user log in, releasing resources it take it. 

If you still want try alternatives, there are the base (very complete anyway) xdm, wdm (a dead project but still in repos), slim, beauty and light but you must install manually ([see here]("http://slim.berlios.de")) and there is [entrance]("http://www.get-e.org/Themes/Entrance/") for enlightenment that can be used without it but required some of its libs ([check here]("http://www.get-e.org/Resources/Applications/System/Entrance/")).

GDM could be simply uninstalled (and/or reinstalled) with apt-get/aptitude/synaptic. 
But login manager are boot services that need to be turned on to start (or manually type startx for gnome, startfluxbox for fluxbox, etc).
I recommend an light app from repos, sysv-rc-conf, very useful to check available services and turn them on/off boot.

hth,

---

### Post by RedSquirrel on 2007-10-02
> **jimmywu013 said:**
> Thanks for the replies
I think I'm going to go install fluxbox as soon as I get a chance to get back to my ubuntu box, but I still have a few questions

I know that there are some apps that depend on gnome libraries - including (correct me if i'm wrong) openoffice, firefox, and all the gnome administration apps that begin with gnome- whatever. My understanding is that since I have the gnome libraries installed, I will still be able to use these apps in fluxbox, but does that defeat the purpose of having a lighter desktop environment, since gnome (or pieces of it) will be running anyway? Is this right or I am way off base?

Yes, it won't be as light as it could be, but it will still be a little better if you run Fluxbox and use GNOME applications rather than running the whole GNOME environment. If you're just experimenting at this point, you might want to try installing Fluxbox and using it with applications you already have just to see if it feels any better.

If it's still not fast enough for you, then I would advise a minimal installation with Fluxbox or another light window manager.

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)
[http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/](http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/)

On my minimal system, I avoid using any applications that are tied to a desktop environment (GNOME, KDE, or Xfce). When I want to install something, I have a look at its dependencies first to be sure I'm not pulling in too much extra junk. ;)

By the way, if you decide to install Fluxbox, be sure to run the following command after you install it so that you will have the default menu when you login:

```
sudo update-menus
```

---

### Post by jimmywu013 on 2007-10-02
> **Rui Pais said:**
> Yes, you will be able to run any installed app from fluxbox. 
GDM could be simply uninstalled (and/or reinstalled) with apt-get/aptitude/synaptic. 
But login manager are boot services that need to be turned on to start (or manually type startx for gnome, startfluxbox for fluxbox, etc).
I recommend an light app from repos, sysv-rc-conf, very useful to check available services and turn them on/off boot.


Thanks for the reply, but could you clarify that comment a bit?  Can I just remove gdm with apt, or do I need to something with sysv-rc-conf first?

I would prefer to continue using OpenOffice.org for its odt format, and I take it openoffice does not depend on gnome - at least apt-cache depends openoffice.org doesn't seem to list anything with gnome in it.  Is this right?
I'm also thinking of switching to Dillo instead of Firefox, but I was wondering if anyone had other suggestions for light browsers? Specifically, I'd like to know if anyone who has used links2 or lynx for a while has had any problems with web pages being rendered poorly or improperly.  

EDIT: Also, does anyone have comments on the various merits/disadvantages of openbox/icewm/fluxbox?  I know all three are relatively lightweight, but I'm most concerned with compatibility - will these wm's run any ubuntu application?  The apt-cache show  for openbox seems to emphasize "standards compliance" and support for gnome and kde.  

EDIT (again): Just tried installing and using Dillo.  It seems a bit unrefined in its GUI, but I'm perfectly fine with that.  However, when trying to access my email, it told me error: unsupported protocol, so I guess I'm not going to use that.  

Thanks again for all the help.

Jimmy

---

### Post by kerry_s on 2007-10-02
> **jimmywu013 said:**
> Thanks for the reply, but could you clarify that comment a bit?  Can I just remove gdm with apt, or do I need to something with sysv-rc-conf first?

I would prefer to continue using OpenOffice.org for its odt format, and I take it openoffice does not depend on gnome - at least apt-cache depends openoffice.org doesn't seem to list anything with gnome in it.  Is this right?
I'm also thinking of switching to Dillo instead of Firefox, but I was wondering if anyone had other suggestions for light browsers? Specifically, I'd like to know if anyone who has used links2 or lynx for a while has had any problems with web pages being rendered poorly or improperly.  

EDIT: Also, does anyone have comments on the various merits/disadvantages of openbox/icewm/fluxbox?  I know all three are relatively lightweight, but I'm most concerned with compatibility - will these wm's run any ubuntu application?  The apt-cache show  for openbox seems to emphasize "standards compliance" and support for gnome and kde.  

Thanks again for all the help.

Jimmy

**sudo apt-get purge gdm**

dillo is okay for bouncing around the web, firefox is king.

like i said with those specs you don't really need to go really light, you just need a faster distro that works better on the old stuff.

i use a debian custom + xfce4, 450mhz 256ram 1gig swap. everything is fast on mine. i have no gdm, mine's set to autologin straight to the desktop.

pic, main app's on the left, system info on the right in conky.

---

### Post by jimmywu013 on 2007-10-02
That pic looks pretty cool
I've got fluxbox loaded right now, and it does seem a little faster, but am going to try xfce4 next.
I don't like how fluxbox is missing many of the handy shortcuts that I got used to in gnome, like Ctl+Alt for switching workspaces etc. (Never mind: Alt+Fn keys switch workspaces) Also, why isn't the apps menu in the main toolbar?  I finally found it after right clicking everywhere I could, before realizing that it was accessible by right-clicking the desktop.  I haven't found a way to add the menu or any launchers/shortcuts to the toolbar yet.

About purging gdm - afterwards what would happen upon reboot?  Would the system still switch to tty7 automatically, but with a textual login similar to the one on the other tty's?
Also, I think startx is for gnome, startfluxbox for fluxbox, but what about xfce4?  And do I need to manually start the xserver.  The reason I hesitate to actually remove it is because I have work to get done and not much time to break my system so I can go fix it again.  

Thanks,

Jimmy

---

### Post by kerry_s on 2007-10-03
i wouldn't worry about gdm right now, just leave it alone. just try to learn your way around. like i said try the debian xfce4 i linked to, you'll be surprised. when you get use to things you can try a custom install, which is just installing what you want.

linux is nice in that it only takes a short time to install. on top of that you can have it any way you want.

---

### Post by TeaSwigger on 2007-10-03
> **jimmywu013 said:**
> That pic looks pretty cool
I've got fluxbox loaded right now, and it does seem a little faster, but am going to try xfce4 next.
I don't like how fluxbox is missing many of the handy shortcuts that I got used to in gnome, like Ctl+Alt for switching workspaces etc. (Never mind: Alt+Fn keys switch workspaces) Also, why isn't the apps menu in the main toolbar?  I finally found it after right clicking everywhere I could, before realizing that it was accessible by right-clicking the desktop.  I haven't found a way to add the menu or any launchers/shortcuts to the toolbar yet.

About purging gdm - afterwards what would happen upon reboot?  Would the system still switch to tty7 automatically, but with a textual login similar to the one on the other tty's?
Also, I think startx is for gnome, startfluxbox for fluxbox, but what about xfce4?  And do I need to manually start the xserver.  The reason I hesitate to actually remove it is because I have work to get done and not much time to break my system so I can go fix it again.  

Thanks,

Jimmy

Hi Jimmy, I have a lousy old Celeron with 256mb mem. It runs commendably, like you say but is sluggish with full-on Ubuntu or Kubuntu (Gnome or KDE). Xfce (via Xubuntu) was a little better but was not as much of an improvement as using Fluxbox or IceWM on a Kubuntu or Ubuntu install. So if you do like Ubuntu/Kubuntu's applications and features but want to lighten things as easily and safely as possible until you learn more, I suggest you use IceWM or Fluxbox, or another light wm that suits.

IceWM is more traditional in having a "start menu" in the taskbar and things like that. Fluxbox is unorthodox and may take more getting used to. But fluxbox is amazingly customizable. If you stick with Fluxbox, you may want to visit us in these threads:
[http://ubuntuforums.org/showthread.php?t=371144](http://ubuntuforums.org/showthread.php?t=371144)
[http://ubuntuforums.org/showthread.php?t=483613](http://ubuntuforums.org/showthread.php?t=483613)
where there are lots of things like making fluxbox menu items and other good bits you may like to know.
If you want IceWM, you may enjoy this very useful thread:
[http://ubuntuforums.org/showthread.php?t=263710&highlight=IceWM](http://ubuntuforums.org/showthread.php?t=263710&highlight=IceWM)

You could also try a super fast distro like Puppy Linux, or Damn Small Linux. But you may find using IceWM or Fluxbox or another light wm with a careful selection of apps on Ubuntu may allow you to enjoy the big full featured modern distros with reasonable enough speed on your old PC. 

Enjoy :)

---

### Post by TeaSwigger on 2007-10-03
Oh another tip for you Jimmy; if it isn't set up so already, check in OpenOffice's options that the Java feature is not checked. It will load much faster without it. Removing the rulers (if using print view) may also help a teensy bit. You may try AbiWord if you haven't already. :)

---

### Post by Rui Pais on 2007-10-03
> **jimmywu013 said:**
> ...
I'm also thinking of switching to Dillo instead of Firefox, but I was wondering if anyone had other suggestions for light browsers? Specifically, I'd like to know if anyone who has used links2 or lynx for a while has had any problems with web pages being rendered poorly or improperly.  

...

EDIT (again): Just tried installing and using Dillo.  It seems a bit unrefined in its GUI, but I'm perfectly fine with that.  However, when trying to access my email, it told me error: unsupported protocol, so I guess I'm not going to use that.  

...

Have you tried kazehakaze.  It's much faster and lighter then FF and much more complete then dillo. It's a pitty that this browser is so less known.

Opera is nice too. Heavier but runs faster and winner when came to render pages, either in quality as speed.

---

### Post by jimmywu013 on 2007-10-03
Thanks again for all the replies
I think I'll leave gdm alone for now and play around with both fluxbox and xfce4 and see works better.
Thanks TeaSwigger for the links

EDIT: have been trying kazehakase and am very satisfied in terms of  speed and functionality.  Imported my firefox bookmarks w/o problems
The only thing I'm wondering is does it have any addons/extensions.  I used adblock and noscript in firefox, as well as WOT, gmail manager and forecastfox (and more), and I would like to be able to have something similar in kazehakase.  BTW, I can never spell 'kazehakase' correctly the first time around - it's such an unusual name.
Also, how is IceWeasel in terms of performance?  I'm guessing it won't be much better than firefox, since the only thing significant difference, afaik, is the artwork and the name. 

EDIT 2: Have been trying swiftweasel, and I like it for being free, as opposed to swiftfox, but faster than firefox.  It's not lightning fast, but still, better than firefox.

Jimmy

---

