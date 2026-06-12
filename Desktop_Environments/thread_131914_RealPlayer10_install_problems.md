---
title: "RealPlayer10 install problems"
date: 2006-02-17
forum: Desktop Environments
---

### Post by JungleBeast on 2006-02-17
Hello all! I'm new to Linux and Ubuntu and I'm trying to install Realplayer10 on Breezy, as it's the only way to listen to bbc. I'm following the FAQs and i've done the download a couple times, only to find that Firefox no longer works.

So I just started again, reinstalling Breezy.. So rather than going through the whole install every time I get it wrong to be able to get back online to find more info, I'd like to get it right first time (this time!)
So far I've got:

```
cd ~/Desktop
sudo apt-get install libstdc++5
chmod +x RealPlayer10Gold.bin
sudo ./RealPlayer10Gold.bin
```

and it all seems to install fine - I got this from the Ubuntu wiki [https://wiki.ubuntu.com/RealplayerInstallationMethods]("https://wiki.ubuntu.com/RealplayerInstallationMethods")
the icon appears in applications and everything, but Realplayer does not launch and Firefox no longer launches.

So (also in ubuntu wiki) I found that RealPlayer and Breezy sometimes have SCIM conflicts and that to fix this to:

```
sudo gedit /usr/bin/realplay
```

and then to edit the line after the bash declaration statement:


#!/bin/sh

GTK_IM_MODULE=xim ; export GTK_IM_MODULE


I followed all this, but it still hasn't resolved the problem.

So has anyone got any ideas? I'm just trying to install realplayer on a fresh breezy install on an amd64, surely everyone else doing this should have the same conflict?  
well thanks for any help!

---

### Post by K.Mandla on 2006-02-17
Hi. I just followed the same wiki instructions for my laptop (Pentium M), and didn't have any problems. Could this be an AMD64 issue?

---

### Post by joplass on 2006-02-17
Maybe you should try automatix especially if you consider yourself a noob.

---

### Post by K.Mandla on 2006-02-17
[QUOTE=joplass]Maybe you should try automatix especially if you consider yourself a noob.[/QUOTE]
I don't know if that would solve it; I don't think RealPlayer is included in the Automatix setup, and I don't think it's intended for an AMD64 installation (which I assume is being used, since it's an AMD64 machine).

I can play the [BBC World Service's live stream]("http://www.bbc.co.uk/worldservice/ram/live_infent.ram") through Totem. Would that be an acceptable workaround?

---

### Post by JungleBeast on 2006-02-17
That would be a great work around!!!  \\:D/      
I was just about to risk it anyway and try putting it into 

 /opt/RealPlayer

as it suggests here:  [http://http://ubuntuforums.org/showthread.php?t=123370&highlight=realplayer]("http://http://ubuntuforums.org/showthread.php?t=123370&highlight=realplayer")

even though that seems very similar to the SCIM workaround.

So how do you get Totem to work there?    

:D

---

### Post by K.Mandla on 2006-02-17
[QUOTE=JungleBeast]So how do you get Totem to work there?[/QUOTE]
Ironically, I can't remember if that was part of the default install or if I installed it with Automatix. :p I'm sure there's a wiki about installing Totem if you want to avoid Automatix.

It's under Applications > Sound & Video > Totem Movie Player (I'm using Gnome). Hit CTRL+L and paste in the stream URL. 

I don't know if it will work off a *clean* -- as in, no RealPlayer -- install, since I just installed RealPlayer myself. :D  But see if it works for you. Cheers!

---

### Post by JungleBeast on 2006-02-17
Typical!  :rolleyes: 
I'm missing the "cook" codec for playing the world service  on Totem, but I do have a program called "streamtuner" instead. However, I'v realised that the world service isn't exactly what I want. It's the listen-again feature that only works with Realplayer. 
So I'm gonna try the Real install again..  Wish me luck!

---

### Post by K.Mandla on 2006-02-17
[QUOTE=JungleBeast]Typical!  :rolleyes: 
I'm missing the "cook" codec for playing the world service  on Totem, but I do have a program called "streamtuner" instead. However, I'v realised that the world service isn't exactly what I want. It's the listen-again feature that only works with Realplayer. 
So I'm gonna try the Real install again..  Wish me luck![/QUOTE]
OK, I think I probably installed that with Automatix as well. I didn't realize how reliant I was on that. 

Good luck!

---

### Post by JungleBeast on 2006-02-22
Well, I never did get round to doing it again yet.  Which was a good thing - I've done a bit more rooting around and it's an amd64 issue.   Apparently Realplayer just can't work on a 64 platform. As well as a few other programs such as Adobe Acrobat..

So nice to know I wasn't just being thick or something.

There is a workaround, which is to set up "chroot" which emulates a 32 bit environment, which would be good except that i'm running a 64 and i don't want to step down to 32. This does seem to be the most common workaround though.

And there's another, which I found in the forum by some clever chappy who seems to have sussed it and nicely posted it here: [http://www.ubuntuforums.org/showthread.php?t=128757&highlight=realplayer]("http://www.ubuntuforums.org/showthread.php?t=128757&highlight=realplayer")   

So i'll give that one a go, and get back on whether it worked or not. (in case there's any curious people out there who want to read about my struggles in getting my Ubuntu fully pimped and good to go :-D )

---

