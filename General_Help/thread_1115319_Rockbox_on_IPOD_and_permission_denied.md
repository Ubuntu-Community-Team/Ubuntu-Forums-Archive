---
title: "Rockbox on IPOD and permission denied"
date: 2009-04-03
forum: General Help
---

### Post by tehrebo on 2009-04-03
I've been trying to install rockbox on my 5th gen 30 GB Ipod video, but I get the following error when I select the complete installation method: "No ipod detected, permission for disk access denied". After I got that error I did some research and tried to change my ipod's permission, the GUI wont event detect my ipod's permissions it just says: "The permissions of IPOD could not be determined". Then I tried the to change them with this command 
```
sudo chmod u+w IPOD
```
It doesn't give me any errors but still wont fix the problem. Oh and my ls -l gives this 
```

lrwxrwxrwx 1 root root     6 2008-12-31 08:32 cdrom -> cdrom0
drwxr-xr-x 2 root root  4096 2008-12-31 08:32 cdrom0
drwxr-xr-x 2 root root  4096 2008-12-31 08:32 cdrom1
drwxr-xr-x 2 root root  4096 2009-04-03 14:51 IPOD
drwx------ 8 rebo root 16384 1969-12-31 18:00 IPOD_

```
I've been googleing for a while and can't seem to find the answer, please reply if anyone got any idea of what could've been causing this error
Thanks in advance

---

### Post by CrazyMike on 2009-04-07
I'm having the same issue on the same version of ipod.  Won't autodetect the ipod in Rockbox but every other app will at least detect the device...

---

### Post by sideffects on 2009-05-25
I don't know if you guys are still having trouble with this or not, but what you need to do is download the Rockbox automatic installer from [http://www.rockbox.org/twiki/bin/view/Main/RockboxUtility#Download](http://www.rockbox.org/twiki/bin/view/Main/RockboxUtility#Download) and extract it. Then right click on the executable and click on "open with other application..." Instead of selecting a program, go down to the arrow where it says "use a custom command" and simply type in ```
gksu
``` That should install Rockbox successfully for you.

---

### Post by geodanny on 2009-06-18
Thank you. This worked for me when installing the Rockbox utility on a Sansa e280. I'll need to remember this command for the future when I need to run a gui app as root. :KS:KS:KS:KS

---

### Post by kidux on 2009-07-10
> **sideffects said:**
> I don't know if you guys are still having trouble with this or not, but what you need to do is download the Rockbox automatic installer from [http://www.rockbox.org/twiki/bin/view/Main/RockboxUtility#Download](http://www.rockbox.org/twiki/bin/view/Main/RockboxUtility#Download) and extract it. Then right click on the executable and click on "open with other application..." Instead of selecting a program, go down to the arrow where it says "use a custom command" and simply type in ```
gksu
``` That should install Rockbox successfully for you.
Confirmed to work on a 5th gen Color Video 30gb model. I'd give ya thanks if I could, but this is all I got, lol! :KS:KS:KS:KS:KS

---

### Post by Gaudentius on 2009-07-26
> **sideffects said:**
> I don't know if you guys are still having trouble with this or not, but what you need to do is download the Rockbox automatic installer from [http://www.rockbox.org/twiki/bin/view/Main/RockboxUtility#Download](http://www.rockbox.org/twiki/bin/view/Main/RockboxUtility#Download) and extract it. Then right click on the executable and click on "open with other application..." Instead of selecting a program, go down to the arrow where it says "use a custom command" and simply type in ```
gksu
``` That should install Rockbox successfully for you.

THANK YOU!

This worked GREAT!

GD:popcorn:

---

### Post by prawnpie on 2009-07-29
I ran 
> gksudo <program-name>
gksu didn't pop up the window

worked like a charm after that.

---

### Post by danceswithcats on 2009-10-03
Thank you, thank you, thank you.  I've been playing with my ipod all morning and it was just starting to not be fun any more.  Thank you.

(Thank you)

---

### Post by jaysonic on 2010-01-02
Thanks to all, the gk command saved the day. Oh just to read the manual....
One unbricked ipod down ... to go

---

### Post by stochasticjack on 2010-01-03
Hi.  I've got a Mac-formatted 5G 80G iPod.  I changed the formatting to FAT32, then loaded Rockbox.  It wasn't seeing the iPod, although my computer (9.10) was.  I tried your workaround and it worked, even the autodetect...

BUT...

When I reboot, it says it can't open Rockbox.  I can reboot and start it in Disk Mode, but that's it.  

Help!

---

### Post by james2c19v on 2010-01-14
> **sideffects said:**
> I don't know if you guys are still having trouble with this or not, but what you need to do is download the Rockbox automatic installer from [http://www.rockbox.org/twiki/bin/view/Main/RockboxUtility#Download](http://www.rockbox.org/twiki/bin/view/Main/RockboxUtility#Download) and extract it. Then right click on the executable and click on "open with other application..." Instead of selecting a program, go down to the arrow where it says "use a custom command" and simply type in ```
gksu
``` That should install Rockbox successfully for you.

Awesome! I was really scratching my head on this one... I was going to try to figure out how to add the binary to my PATH and all kinds of bizarre stuff, but fortunately I read your post! Worked like a charm, and it even made auto-detect work. (iPod 5th gen 30 GB)

---

### Post by rob22941 on 2010-05-28
Hello all, I'm having trouble with the complete installation. I have my found my ipod manually because selecting it off the list wasn't working. I have a 4th Generation 20gb I want to do a trial run on with rockbox first before I do anything with my 5th gen. 

When I select Complete Installation I get an error "could not open ipod: permission denied" where do I go from here? I can't seem to figure this out.

---

### Post by LacerdaPT on 2010-06-22
Hi! I had the same problem and found the answer! Here it is: [http://forums.rockbox.org/index.php?topic=24800.0](http://forums.rockbox.org/index.php?topic=24800.0)


Cheers

---

