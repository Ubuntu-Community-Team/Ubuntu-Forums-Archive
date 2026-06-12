---
title: "X server broken - driver problem"
date: 2007-03-23
forum: Desktop Environments
---

### Post by pillu on 2007-03-23
Hi all,

I installed Beryl on my kubuntu 6.10 laptop. The system is intel centrino duo 1.66 GHz, intel 945 GMA on board graphics, 1 GB RAM. I also configured to automatically run Beryl on startup. Now when I restart the machine kde refuses to start. I tried to uninstall beryl using 
```
apt-get remove beryl
```
I removed the beryl startup scripts that were supposed to start it up automatically. I replaced the xorg.conf with the backup copy. I installed gdm instead of kdm. All to no avail. I get the message that X server is broken. When I look up the log file at /var/something/Xorg.0.log (forgot the path) there is an error (denoted by EE) that the driver i810 is not configured for this screen depth. The next error is there is no screen for this depth and hence cannot start kde.

So I think there is a driver issue here. Is there any way I can salvage my desktop without reinstalling everything? I am sorry about the sloppy post but since I have no gui I just try to remember everything and then log back in to windows and post from there. 

Pillu

---

### Post by dfreer on 2007-03-23
Hmmm. I would try a *sudo dpkg-reconfigure xserver-xorg*. If that doesn't fix it, try booting from a Live CD, get online, and post your /etc/X11/xorg.conf
When you do, also post your monitor and video card information.

---

### Post by pillu on 2007-03-25
thank you so much...I did the dpkg-reconfigure of xserver-xorg and used all the default options....And now everything works !!!!
I feel like giving u a biiiiiiiig hug and treating u to beers or something

One other issue...Now my laptop resolution is 1024*760 instead of 1280*800...I had solved this earlier by installing the 915resolution patch. But that seems more like a hack....Do you know if there is a better solution ?

And a last question...Do I go about reinstalling beryl and try to see if it works ?

Thank you so much once again....

cheers
pillu

---

### Post by dfreer on 2007-03-25
You're welcome! Glad I could help ya out.

> One other issue...Now my laptop resolution is 1024*760 instead of 1280*800...I had solved this earlier by installing the 915resolution patch. But that seems more like a hack....Do you know if there is a better solution ?

Are you refering to [*_this_*]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_Correct_the_Graphics_Resolution_.28Intel.29")?
Well, I don't have an intel video card, so I've never had that problem before. The best thing to do would be google around, search the ubuntu forums, and then if you can't find anything make a new thread specifically about your resolution problem.

> Do I go about reinstalling beryl and try to see if it works ?


Beryl *shouldn't* mess up your xorg file, at least in my experience. If you do try to install it again, at least you know how to fix things if it goes downhill. How were you trying to install beryl (what guide did you use, what commands did you enter)? Backup your xorg.conf before you do anything, and take careful notes of what you do. If things get hosed up again, just post exactly what went wrong and I'm sure someone can help you out :D

---

