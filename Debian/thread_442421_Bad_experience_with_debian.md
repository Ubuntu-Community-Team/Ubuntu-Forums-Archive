---
title: "Bad experience with debian"
date: 2007-05-13
forum: Debian
---

### Post by juxtaposed on 2007-05-13
I wanted to try debian. Simple as that. So I downloaded the DVD, and I installed it. Installed fine. Then at the desktop I could only get 640*480 resolution. Fine... But the repositories didn't have fglrx. So I downloaded the ATI driver from the ATI website. I tried to install it, but I aparently wasn't put on the sudoers list. So I tried to log in as root to edit it... But it didn't let me log in as root. So I had to go back in and change the GDM settings (oddly enough, it let me sudo to do that). But navigating is hard on 640*480. Then I figured out that I could use ALT to move the windows around. So I let root log in from GDM, then I did that. Tried to edit the /etc/sudoers file but it wouldn't let me. So I said "pah, I can't do this at 640*480, ill just install the graphics driver as root instead of using sudo". So I did that. It then told me to do aticonfig and restart. I typed in aticonfig and there was a million options, so I tried the first one (aticonfig --initial). It said there was some error, so I rebooted. When GDM should have come up, my monitor had an error on the screen "Input not support".

So I guess I wasted a DVD on debian. What should I try next (since I uninstalled ubuntu to try debian, i'd might as well try something else). I was thinking Fedora Core, but the next release is coming out in a few weeks and I don't want to wait that long without linux. I'm thinking Slackware, or everyone seems to be talking about Zenwalk and Sabayon. Or maybe I should try to install debian again...

---

### Post by heimo on 2007-05-13
Try Mepis (I haven't):
[http://www.mepis.org/](http://www.mepis.org/)

Or any other major distribution:
[http://distrowatch.com/dwres.php?resource=major](http://distrowatch.com/dwres.php?resource=major)

---

### Post by juxtaposed on 2007-05-13
I decided to reinstall Debian, but I am very annoyed at the fact that although there is a massive ammount of documentation out there, very little of it is from the last year.

It installed with only security updates in the sources.list and I need to find out how to put in the lenny repos. Everything just says to change etch to lenny, but I need the actual repo names :/

---

### Post by Pobega on 2007-05-13
cat /etc/apt/sources.list

And post the output here.

---

### Post by kerry_s on 2007-05-13
I would say you did not enable all your repos, i see the drivers in synaptic. My guess is you were only looking at the app's available on the dvd. I'm using the xfce4 version.

net installer-> [http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-netinst.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-netinst.iso)
kde installer-> [http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-kde-CD-1.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-kde-CD-1.iso)
xfce4 installer-> [http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso)

My sources->

deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) etch main contrib non-free  

deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) lenny main contrib non-free  

deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) sid main contrib non-free  

deb [http://security.debian.org/](http://security.debian.org/) etch/updates main contrib non-free 

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) unstable non-free 

deb [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) testing main

---

### Post by juxtaposed on 2007-05-13
> cat /etc/apt/sources.list

And post the output here.

I found some french site that had a list of repos to use, so I put them in and commented out the ones that were there already (the last 4 lines uncommented are the ones I added in, and I commented out the first 4).

Then I did a dist-upgrade, and it downloaded 200MB of stuff, so I guess I am running lenny right now.

> patrick@debian:~$ cat /etc/apt/sources.list
#
# deb cdrom:[Debian GNU/Linux 4.0 r0 _Etch_ - Official i386 DVD Binary-1 20070407-11:40]/ etch contrib main

# deb cdrom:[Debian GNU/Linux 4.0 r0 _Etch_ - Official i386 DVD Binary-1 20070407-11:40]/ etch contrib main

# deb [http://security.debian.org/](http://security.debian.org/) etch/updates main contrib
# deb-src [http://security.debian.org/](http://security.debian.org/) etch/updates main contrib

deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) lenny main
deb-src [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) lenny main

deb [http://security.debian.org/](http://security.debian.org/) lenny/updates main
deb-src [http://security.debian.org](http://security.debian.org) lenny/updates main


> I would say you did not enable all your repos, i see the drivers in synaptic. My guess is you were only looking at the app's available on the dvd. I'm using the xfce4 version.

That's probably it, though I didn't have an option (that I remember) to either enable or disable them. There was an option to get the packages from the internet during install, but I didn't do that.

> My sources->

Should I just copy those into mine and apt-get update? One site that I read said that you are almost sure to run into problems with sid and it was only for bug testers.

EDIT: I just used those sources and I can see fglrx in the repos. I guess it's time to install it and see if it works... I've got 200+ updates available now, so I won't install them until later, if I do (or I might just take sid out of the sources list).

---

### Post by kerry_s on 2007-05-13
No you don't need to copy mine, just add " contrib non-free " to the end of yours.

No, i use etch(stable) but can grab apps from lenny(testing) or sid(unstable). I have my prefernce set up in synaptic to use stable. see pic

---

### Post by juxtaposed on 2007-05-13
Well, I just got rid of sid from it. I might do what you're doing later though...

So I did "dpkg-reconfigure xserver-xorg" and went through it. It detected that I should be able to do 1280*1024, and I put in everything that I knew... Then when it finished (or sometime inbetween, I don't know) it did this:

> 
patrick@debian:~$ sudo dpkg-reconfigure xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration   file; backup in /etc/X11/xorg.conf.20070513192425
patrick@debian:~$



But I can't change the screen resolution past 640*480. Ill restart to see if that does anything.

Wow, debian is hard. I'd hate for someone who has never used linux before to try it.

So, I restarted. I was so suprised that GDM was much better then 640*480. I'm not sure exactly, but it looked like 1280*1024 (the max of my monitor). But then I logged in and it went to the "input not support" thing. So, I don't know if I can do much from it now... I have a windows XP install I might be able to edit files on the partition through (through IFS or something), and I have the ubuntu 7.04 CD.

---

### Post by tturrisi on 2007-05-13
It sounds like the display driver that got installed was a generic or vesa driver.

change screen resolution use command:
dpkg-reconfigure xserver-xorg

select ati in the list of display adapters & set default resolutions

---

### Post by juxtaposed on 2007-05-13
Wow, I am very suprised :D

> 

It sounds like the display driver that got installed was a generic or vesa driver.

change screen resolution use command:
dpkg-reconfigure xserver-xorg

select ati in the list of display adapters & set default resolutions
Reply With Quote


Reading that made me remember the "ctrl alt f1" thing to open up a command line. So, even though I couldn't do the display thing, I could do that. So I reconfigured xorg. I thought there might be one of two problems... Either it was trying to go to a higher bit depth then possible, or it was trying to go with a higher refresh rate then was possible. I was pretty sure everything should work at 24 bit, so I went through the reconfigure thing and instead of choosing simple at a part, I choose intermediate or something. It let me choose my max monitor settings - I choose 1280*1024 at 60Hz (I think my monitor can do 75Hz, but I didn't see the option there, and it wasn't a big deal anyway, as I don't think there is a big difference).

I restarted the computer (forcefully... The shutdown command didnt seem to work). I went into GDM, logged in, and was presented with 640*480. I then changed it, and now I have 1280*1024 on Debian Lenny. Now to configure it, and... Yay :) Thanks everyone. The ubuntuforums are even great for debian =D

Now to find the restriced-drivers-manager and get it to enable my fglrx so I can have 3d acceleration (even if it isn't that great on an integrated ATI card).

---

### Post by tturrisi on 2007-05-13
well done.
There is no "restricted drivers manager" in debian, that's an ubuntu uniqueness.
enable non-free sources & do:
apt-get install fglrx-driver

To get 3d to work you'll have to compile the driver and all from source.  The above will work, but w/out 3d. 
[http://packages.debian.org/testing/x11/fglrx-driver](http://packages.debian.org/testing/x11/fglrx-driver)

to get 3d do:
apt-get install module-assistant fglrx-kernel-src 
next;
module-assistant and follow prompts

you may need to install other dependencies to be able to build the driver for your kernel (gcc, kernel-headers, etc).

here's all the available packages for lenny:
[http://packages.debian.org/testing/](http://packages.debian.org/testing/)

---

### Post by PatrickMay16 on 2007-05-14
juxtaposed, it looks more like you had a bad experience with ATI's linux drivers rather than Debian.

---

### Post by juxtaposed on 2007-05-14
> 

well done.
There is no "restricted drivers manager" in debian, that's an ubuntu uniqueness.
enable non-free sources & do:
apt-get install fglrx-driver

To get 3d to work you'll have to compile the driver and all from source. The above will work, but w/out 3d. 
[http://packages.debian.org/testing/x11/fglrx-driver](http://packages.debian.org/testing/x11/fglrx-driver)

to get 3d do:
apt-get install module-assistant fglrx-kernel-src 
next;
module-assistant and follow prompts

you may need to install other dependencies to be able to build the driver for your kernel (gcc, kernel-headers, etc).

here's all the available packages for lenny:
[http://packages.debian.org/testing/](http://packages.debian.org/testing/)


I've never been able to actually compile things, but I guess i'll have to learn for this. Thanks :) I do find it odd that I would need to compile it though.

> juxtaposed, it looks more like you had a bad experience with ATI's linux drivers rather than Debian.

That was some of the problem, but then there were some other little annoyances with debian. The biggest one being, I guess Xorg didn't configure right so I had to do it on my own.

But in the end, since I have it mostly figured out (just have to install the ATI drivers and/or get them working), I have nothing against debian. Just a learning experience - I'll keep debian, and use it as my main OS, until if something messes up that can't be fixed (which is unlikly), as the main point of all this was to install it to use (not just see how different it was from ubuntu).

---

### Post by nudnik on 2007-05-16
> **juxtaposed said:**
> I wanted to try debian. Simple as that. So I downloaded the DVD, and I installed it. Installed fine. Then at the desktop I could only get 640*480 resolution. Fine... But the repositories didn't have fglrx. So I downloaded the ATI driver from the ATI website. I tried to install it, but I aparently wasn't put on the sudoers list. ...

For anyone who might be reading this and experiencing a similar problem, you can achieve "super user" status in Debian by typing "su" in a terminal and then your password.

---

### Post by juxtaposed on 2007-05-19
> well done.
There is no "restricted drivers manager" in debian, that's an ubuntu uniqueness.
enable non-free sources & do:
apt-get install fglrx-driver

To get 3d to work you'll have to compile the driver and all from source. The above will work, but w/out 3d.
[http://packages.debian.org/testing/x11/fglrx-driver](http://packages.debian.org/testing/x11/fglrx-driver)

to get 3d do:
apt-get install module-assistant fglrx-kernel-src
next;
module-assistant and follow prompts

you may need to install other dependencies to be able to build the driver for your kernel (gcc, kernel-headers, etc).

here's all the available packages for lenny:
[http://packages.debian.org/testing/](http://packages.debian.org/testing/)

I know this was posted 5 days ago, but I just did it today.

I did that, went through module assistant (with it set to do fglrx), I installed some things, it said it was done and it was installed. I restarted but glxgears doesn't work well. It goes fine for a second, then gets really slow (exactly like before).

> patrick@debian:~$ glxgears
Xlib:  extension "XFree86-DRI" missing on display ":0.0".


I think I need to enable something, maybe in xorg, but I have no idea what.

---

### Post by tturrisi on 2007-05-20
~# dpkg-reconfigure xserver-xorg
there will be a screen where you can enable additional things.

---

### Post by juxtaposed on 2007-05-20
> **tturrisi said:**
> ~# dpkg-reconfigure xserver-xorg
there will be a screen where you can enable additional things.

I did that and changed it from ati to fglrx at what I think was the first screen, went through it all, rebooted, and it seems to have worked (glxgears goes normally now). Thanks alot =)

---

