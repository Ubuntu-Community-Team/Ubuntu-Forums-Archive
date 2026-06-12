---
title: "Just installed Kubuntu, misc questions..."
date: 2007-01-26
forum: Desktop Environments
---

### Post by Boule on 2007-01-26
Hi,

I recently installed Kubuntu (first time trying ubuntu-linux), and I would really appreciate it if you guys could clarify some things for me:

1. I'm considering installing ubuntu instead, but I like KDE. I found several ways to do so, and apparently the best one is to install kubuntu-desktop. What's the difference betwenn ubuntu+kubuntu-desktop and kubuntu (other than gnome being available in the 1st) ?

2. I want to install a 3D desktop. I know that these questions has been asked several times, but I found lots of contradictory replies. I have a nvidia geforce fx5600 video card. I installed the nvidia drivers (the regular, not the beta), and "$ glxinfo | grep direct" returns "direct rendering: Yes".
So what should I choose, XGL or AiGLX or nvidia beta ? and compiz or beryl ? And which guide should I follow to install, I found sooooo many ?!
I found a howto about 3D desktops ([https://help.ubuntu.com/community/3ddesktopHowto]("https://help.ubuntu.com/community/3ddesktopHowto")) that mentions none of the above. What is it about ?

3. After I installed the drivers, I still couldn't change my screen resolution, the only choice I had was 640x480. I had to reconfigure X using "sudo dpkg-reconfigure xserver-xorg" to solve the problem. Why was that ? Do I have to do it everytime I install the OS ?

4. What are gksudo and kdesu ? And what's the difference with sudo ?
"sudo kate" and "kdesu kate" seem to have the same result...

Thanks for your help...

---

### Post by Insomniac20k on 2007-01-26
If I understand your first question right, they're the same. It's just more work to install Kubuntu and then add gnome.

As for your second question, look up a guide for installing the drivers on your particular graphics card and follow one.

Third, yes you'll probably have to until maybe a new version is released.

---

### Post by Boule on 2007-01-26
Thanks for your reply,...

I decided to go with AiGLX and Beryl...
As I said, the rendering is enabled (direct rendering: Yes).

Is [this]("https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy") the first step I have to take ?

And would [that]("https://help.ubuntu.com/community/BerylOnEdgy") be the second ?

Also I still can't understand what the [3DDesktop]("https://help.ubuntu.com/community/3ddesktopHowto") will install...

---

### Post by meng on 2007-01-26
3ddesktop is a separate creature from Beryl/Compiz. It's simply a daemon that allows you to show off your desktops as though they were sides of a cube. Some folks like it, some think it's rather useless.

---

### Post by Boule on 2007-01-26
Well throw in the visual effect and that's what Beryl/Compiz is about, right ?

---

### Post by zubrug on 2007-01-26
Try ultimate ubuntu here, it comes installed  [http://www.ubuntuforums.org/showthread.php?t=309704](http://www.ubuntuforums.org/showthread.php?t=309704)
It is a big iso 1.8gigs so hope you have a fast connection and a dvd burner.

---

### Post by dabl on 2007-01-26
You might like to review other Kubuntu users' experiences here:

[http://kubuntuforums.net/forums/index.php](http://kubuntuforums.net/forums/index.php)

:D

---

### Post by Boule on 2007-01-26
Thx, I didn't know about it :)

---

### Post by rsambuca on 2007-01-27
Personally I wouldn't bother with the super iso.  Why don't you just install both the ubuntu (based on gnome) desktop and the kubuntu (based on KDE) desktop.  Then you will have them both and you can just flip back and forth between the two whenever you wish by loging into a new session.  You don't even have to reboot your computer.  Maybe you will like them both!

See this [[COLOR="Red"]link[/COLOR]]("http://www.psychocats.net/ubuntu/gnome") for installing the gnome desktop on your kubuntu installation.

---

### Post by Boule on 2007-01-27
Yeah, I tried that... I think I like gnome better. But I don't like the 2 taskbars, I prefer the KDE way.

I think I'm gonna install ubuntu with kubuntu-desktop.

What's the differemnce betwen using apt-get and aptitude ? The guide says it's easier to remove, but I don't see why...

---

### Post by iRobt on 2007-01-27
theSituation:
I have almost an inverse of the question.  I installed ubuntu 5.01 way back when and added kubuntu.  They took up way to much space on my duel OS machine so I tried uninstalling all gnome apps. leaving the kde.

Even though I didn't uninstall grub, (unless it was done automatically thru dependancies) when I rebooted my system would only come up with the command line.  I couldn't get back to winDoze or the kde desktop.

I reinstalled a minimal v.5.01 in the ext.3 partition and got the upgrade notifications.  Although 6.10 is available the upgrade was to 6.06

theQuestion:
Is it best to just burn a DVD ISO with the most recent stable Kubuntu and install it in the place of ubuntu 6.06?

---

### Post by rsambuca on 2007-01-27
> **Boule said:**
> Yeah, I tried that... I think I like gnome better. But I don't like the 2 taskbars, I prefer the KDE way. I use the gnome desktop as well, but like you, I also prefer one taskbar as it saves on screen real estate.  I have put everything I need onto one taskbar in gnome and deleted the other.  It is quite easy.  Just right click on the taskbar, and you can add or remove what you want.

> What's the differemnce betwen using apt-get and aptitude ? The guide says it's easier to remove, but I don't see why...
Aptitude seems to keep a better handle on all of the associated libraries and dependencies. That is what makes it easier in theory, although with apt-get you can do the same with autoremove, but it does take an extra step.  Not a big deal either way.

---

