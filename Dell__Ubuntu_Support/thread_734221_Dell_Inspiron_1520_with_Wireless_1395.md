---
title: "Dell Inspiron 1520 with Wireless 1395"
date: 2008-03-24
forum: Dell  Ubuntu Support
---

### Post by GForbes on 2008-03-24
Recently got a Dell Inspiron 1520
T5500 1.83GHz
1GB Ram
80GB HDD
8600GT 256MB
Dell Wireless 1395

Now the wireless isn't working with Gutsy.  Any ways to solve this?

---

### Post by drifter42 on 2008-03-24
Hello. 
In my limited experience with gutsy to get my wireless to work, you first must be on a wired connection.Then you install your updates in update manager.When that is done,go to system on you're menu
then on administration then restricted drivers manager.That should prompt you to enable broadcom chipset,click on box to enable click
ok or apply whatever is there  and then it may prompt you to download firmware from web from what i can remember.After that it will up date the software a should be good o go.I hope i didn't miss something,but that should get you in the right direction.
Hope that helps,but if not someone with more experience will or you can search the forums for help.

---

### Post by faithsnathan on 2008-03-24
I agree with Drifter42.  I have a Dell laptop with some kind of Dell WiFi card built-in.  I wasn't able to use wifi on Edgy or Dapper.  It works just fine on Gutsy, though.  

After downloading the restricted drivers or proprietary drivers or whatever they're called, I had to restart my computer for the change to seem to take effect.  I'm so glad the developers added that feature.  It has made a great difference for me!

---

### Post by GForbes on 2008-03-24
Alright, Thanks a lot... I'll be sure to try it out whenever I get a chance.

---

### Post by Karnach on 2008-04-07
Similar situation:  Dell Inspiron 1520 with 1 gig ram 120 GB hd  am dual booting with win xp home.  have tried numerous solutions posted on the forums (ndiswrapper foremost)  and am hitting a wall.  my wifi light is on but no one is home   My question is this:  one step of the procedure is blacklisting the broadcom bcm43xx driver by typing "echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist" should'nt that result in the driver no longer being listed in system>preferences>hardware information?  if so, why is it still showing up?  and as long as it is showing up, the rest of the fix doesn't seem to work.   HELP!!!  Complete noob to Ubuntu  so go really slow and basic with any suggestions please.

Karnach

---

### Post by Maputo on 2008-07-09
I also have Dell Inspiron 1520, and this worked for me:

[http://ubuntuforums.org/showthread.php?t=769990&highlight=wireless](http://ubuntuforums.org/showthread.php?t=769990&highlight=wireless)

---

### Post by stats on 2008-07-10
the driver is in the repo now

1.Update & upgrade using update-manager/synaptic/adept etc
2.
```

sudo apt-get remove ndisgtk ndiswrapper-common ndiswrapper-utils-1.9

```
3. Remove the ndiswrapper line from /etc/modules
4. Disable wireless from the network manager applet and then

```
sudo modprobe -r ndiswrapper
```

If it cribs about module being in use, it means you have not disabled wireless
5. Restart, if there were any kernel upgrades
6. System->Administration->Hardware Drivers
I see a wl driver here. Make sure it says enabled and is in use.

worked for me with dell 1395 on inspiron 1525

---

