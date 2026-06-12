---
title: "Compiz - rotate cube flahes the screen AGAIN"
date: 2012-07-16
forum: Desktop Environments
---

### Post by sendittokeith on 2012-07-16
Hello,

I have that awful problem with rotating the cube where the screen flashes with all of the open windows from the previous screen.  I had applied the fix suggested here [http://ubuntuforums.org/showthread.php?t=1864278&page=2](http://ubuntuforums.org/showthread.php?t=1864278&page=2) and it WORKED GREAT.  

I must have done some other update/upgrade or something because all of the sudden the flashy is back.

Does anyone have any idea how i can fix this?

thanks you in advance...

---

### Post by Petro Dawg on 2012-07-16
Same thing happened to me, I updated my vid drivers and screen flash was back after working just fine before using the PPA you referenced.  Did you by chance install any new drivers or adjust any graphic settings?  

The only advice I got was to sit back and wait until the compiz bug gets fixed or revert back to the original drivers I used (which is not a valid option for me as other apps now work better with the new drivers, and I have my doubts if that would work anyways).  Hopefully they are working on a permanent fix for this.

I tried uninstalling and reinstalling unity3D and compiz and after many frustrating hours later I gave up on the cube.  Its cool, but its not really that critical of a utility, I'll just use desktop wall until someone gets around to a real fix. 

I too would be interested if anyone figured out how to RE-FIX compiz.

---

### Post by sendittokeith on 2012-07-16
Well i guess its good that its not just me ?  ... 

I had updated MANY things on my ubuntu, so not sure which one actually broke it.  :-(   I wonder if there is anyway to re-apply the fix from the post mentioned?  

While not critical at all, it was that eye candy that moved me from windows to ubuntu as an actual replacement (i was just using in vm) ...

oh wellz :-(

> **Petro Dawg said:**
> Same thing happened to me, I updated my vid drivers and screen flash was back after working just fine before using the PPA you referenced.  Did you by chance install any new drivers or adjust any graphic settings?  

The only advice I got was to sit back and wait until the compiz bug gets fixed or revert back to the original drivers I used (which is not a valid option for me as other apps now work better with the new drivers, and I have my doubts if that would work anyways).  Hopefully they are working on a permanent fix for this.

I tried uninstalling and reinstalling unity3D and compiz and after many frustrating hours later I gave up on the cube.  Its cool, but its not really that critical of a utility, I'll just use desktop wall until someone gets around to a real fix. 

I too would be interested if anyone figured out how to RE-FIX compiz.

---

### Post by stinkeye on 2012-07-16
Think there was an update to compiz recently
which would have updated your packages from the compiz-proposed ppa to the packages in the default repos.
I tried the compiz-proposed ppa a while ago but reverted to the 
default compiz because it brought in a couple of other bugs.

If I enable the compiz-proposed ppa now, there are no updates available.

Check in synaptic where your compiz packages are coming from...

---

### Post by jssilva on 2012-07-21
Hello,

Some time ago I had fixed the cube flashing with the ppa version 1:0.9.7.8-0ubuntu1vvpreproposed2.

Then, some weeks ago, inadvertently I let a repos upgrade to 1:0.9.7.8-0ubuntu1.2, the current repos version, that brought back the flashing.

So, I force installed again the referred preproposed and have absolutely no problems with it. My working display is Intel although I have a locked-off nvidia (Optimus). I also usr cairo-dock and gnome classic on precise, if it matters.

But, against what you say, I have to lock the version, otherwise apt wants to upgrade it again to the repos 1.2

---

### Post by sendittokeith on 2012-08-01
Thank you for the info - i am re-installing all partially because i think i had a bad image before. 

How do you lock a repo to a specific version? and how would i downgrade if it happens again?

thanks a lot for your help!


> **jssilva said:**
> Hello,

Some time ago I had fixed the cube flashing with the ppa version 1:0.9.7.8-0ubuntu1vvpreproposed2.

Then, some weeks ago, inadvertently I let a repos upgrade to 1:0.9.7.8-0ubuntu1.2, the current repos version, that brought back the flashing.

So, I force installed again the referred preproposed and have absolutely no problems with it. My working display is Intel although I have a locked-off nvidia (Optimus). I also usr cairo-dock and gnome classic on precise, if it matters.

But, against what you say, I have to lock the version, otherwise apt wants to upgrade it again to the repos 1.2

---

### Post by baker4real on 2012-08-19
> **sendittokeith said:**
> Thank you for the info - i am re-installing all partially because i think i had a bad image before. 

How do you lock a repo to a specific version? and how would i downgrade if it happens again?

thanks a lot for your help!

*I had the same problems with Lubuntu-12.04 Ubuntu-Xbuntu, I figured it must be my pc or graphics. Peppermint worked for a short time, then it froze. So I gave Soluse a try (gnome2) and it works absolutely perfect from the start. Eye-candy is back using 250mg of ram. Old school works for me.*

---

### Post by Cresho on 2012-08-19
its compiz and the way it communicates with your DE.  So cube effects don't work.  I had it working on kubuntu but after a reboot, it would revert to the flicker.  Im using xubuntu for now, I don't even use a lock screen as it causes a screen flicker.

---

