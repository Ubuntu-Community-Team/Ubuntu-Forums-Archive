---
title: "kubuntu 5.04.5 LiveCD spawning problem"
date: 2005-07-29
forum: Desktop Environments
---

### Post by buster on 2005-07-29
Downloaded the new Kubuntu 5.04.5 LiveCD and checked MD5 - OK. Boots fine until trying to open Xserver. Get messages for each of the five run levels about spawning too quickly. Waited patiently and this was repeated. Cursed  quite a bit. Got on with life and wrote this. Anyone else experience this? 5.04.3 worked quite well by the way. Like to see what it looks like before a full install.

---

### Post by rogerhelmich on 2005-07-29
yes the new CD doesn't seem to be working too well for me either.I am receiving the same problem.  md5sum are correct for both the download, and the CD.  Tried burn a CD on a second machine to no avail.  Since it was a T42 that I was attempting to boot.  I tried several other machines and  all the same error messages occurred.

---

### Post by arjaybe on 2005-07-30
I get exactly the same problem.  I even burned the CD at 8x just in case, after reading these posts.

---

### Post by Kob on 2005-07-30
Same here. Downloaded it yesterday, burnt onto a CD, and tried on two different PC with different hardware configurations (one with Matrox 550 video card, the other with Diamond Multimedia Viper 330 card). Both got stuck in the "respawning too fast" messages when getting into the kdm section. I give up on this.

---

### Post by buster on 2005-07-30
Buster here again. Does this mean if I install Kubuntu with 5.04 install, and update/upgrade I will end up with a broken install?  Or is the problem in the LiveCD only? Anyone know?

---

### Post by JuanC on 2005-07-30
this LiveCD include KDE 3.4.2 and KOffice 1.4.1?

---

### Post by tflovik on 2005-07-30
Buster you will not end up with a broken system if you install Kubuntu 5.04 and then upgrade to KDE 3.4.2 .
My laptop is running happily with Kubuntu upgraded to KDE 3.4.2 .

---

### Post by derrick1985 on 2005-07-30
[QUOTE=tflovik]Buster you will not end up with a broken system if you install Kubuntu 5.04 and then upgrade to KDE 3.4.2 .
My laptop is running happily with Kubuntu upgraded to KDE 3.4.2 .[/QUOTE]
And so is my Desktop PC

But I am thinking about going back to Gnome. I do so love the Gnome-Desktop.

---

### Post by pja on 2005-07-30
Like everyone else, I have just downloaded K 5.04.5 and it fails on both my PCs at the following point:

* Id "6" responding too fast: disabled for 5 minutes
* no more processes left in this runlevel

How disappointing!

Hope there is a fix soon.

Regards,
Peter   ](*,)

---

### Post by buster on 2005-07-30
Thanks for the reassurance. I'll see if I can get time next week to put Kubuntu on.

---

### Post by 1c3d0g on 2005-07-31
Any updates on what can fix this problem? I really want to try out the live-cd! ;)

---

### Post by news4doug on 2005-07-31
Couldn't find anything useful under Google or Google Groups about this, but
did see references to this problem at the Debian Forum:

         [http://forums.debian.net/viewtopic.php?t=952&highlight=repawning+fast](http://forums.debian.net/viewtopic.php?t=952&highlight=repawning+fast)

Still looking at online forums for a "quick fix".       Doug ](*,)

---

### Post by buster on 2005-08-09
For anyone still following this thread - I put Ubuntu on and am very happy with Gnome! Surprised me. Used KDE for years.

---

### Post by curtdodds on 2005-08-30
I had this problem with 5.04 on 03/30/05. I decided to wait for the next release. 
I have the same problem with 5.04-5.
Obviously many others have the same experience.
I've often wondered why kubuntu does so poorly on distrowatch,
as I believe kde is more popular than gnome. Now I know why.

Ubuntu boots fine on my computers, kubuntu never has.
I boot to 15 other distros, none of them have this problem.
I've been unable to get the Kubuntu live CD to boot to level 3,
I thought I might help debug it, if I could get a console.
I get the same "respawing too fast: disabled for 5 min" no matter 
what level I try. I've tried many of the boot options like
live noapic nolapic pci-noacpi
and others. I tried various modes with live-expert. 

I refuse to install gnome (ubuntu) just to see their version of kde.
All my computers are via based, kt266, kt400 etc. Is this a common
trait for the failures?
Anyone having this problem, with a chipset other than via?

---

### Post by t2kburl on 2005-08-31
same problem ... intel chipset

Kubuntu rocks as a full install

---

### Post by duffman25 on 2005-09-01
[QUOTE=t2kburl]same problem ... intel chipset

Kubuntu rocks as a full install[/QUOTE]


Same here. On my two machines: an acer laptop (centrino) & an amd64 3000+
It's a shame this hasn't been fixed because the other day I wanted to show the lastest stable kde to a windows user & I could do it with the livecd  :-x I had to go with klax cd.

---

### Post by drtvasudevan on 2005-09-08
sigh!
one more here!
intel chipset p3 800
i wish i had visited this site before downloading.
somehow i downloaded the live version instead of the instal version.must have been half asleep. used up 654 mb of the one gig limit my service provider gives!
wah... ](*,) 

tv

---

### Post by buster on 2005-09-08
Just a comment for those still wishing to try Kubuntu. I have Ubuntu installed as a very nice system. Have used it for everything I do on a computer, including lots of multimedia stuff.  (Had tried the Kubuntu LiveCD unsuccessfully. That's why I started this thread.) Yesterday decided to add the Kubuntu desktop using Synaptic. The install was effortless and Kubuntu looked beautiful. BUT my mouse cursor jumped around. ](*,)  Found no quick fix, and didn't want to ruin Ubuntu with config changes. Kubuntu seems everything Ubuntu isn't - like really annoying. I see no reason to keep trying a distro with such problems. If I want KDE I'll use Mepis or Suse. A lot of effort has been put into Kubuntu, but to me it seems not ready yet. And......

I don't wish to offend, but Ubuntu is so perfect - why mess with success? There are lots of mature KDE distros out there.

---

### Post by KnoaWyls on 2005-10-12
Curious!!

I had no problems when using the Live Version.  It did run terribly slow though.

This is what i got with my error:
Id "1" respawning too fast: disabled for 5 minutes
Id "1" respawning too fast: disabled for 5 minutes
Id "1" respawning too fast: disabled for 5 minutes

The number always stayed 1.  I got this during an actual disk installation after the point that the CD is kicked out and it initiates a reboot to complete the rest of the install.  

NOTE: I had had two previous installation failures with a different install disk and with 160MB of RAM.  Those attempts never made it as far as the disk being kicked out and a reboot being initiated.  I got various errors.  I burnt another disk from the same ISO, this time at a slower speed of 16MB/sec, and bumped up the memory in my system to 256MB.  Suddenly, it was smooth sailing until the point that it kicked the disk out and initiated a reboot.

After freaking out, I performed a Ctrl+Alt+Del and then fully powered down my PC.  Then I powered it up and this time the whole installation completion process completed without a single flaw and now it is running great!  Could it have anything to do with letting the system fully power down first?  I do not know.  Something to keep in mind though.

---

### Post by KnoaWyls on 2005-10-12
[QUOTE=KnoaWyls]Curious!!

I had no problems when using the Live Version.  It did run terribly slow though.

This is what i got with my error:
Id "1" respawning too fast: disabled for 5 minutes
Id "1" respawning too fast: disabled for 5 minutes
Id "1" respawning too fast: disabled for 5 minutes

The number always stayed 1.  I got this during an actual disk installation after the point that the CD is kicked out and it initiates a reboot to complete the rest of the install.  

NOTE: I had had two previous installation failures with a different install disk and with 160MB of RAM.  Those attempts never made it as far as the disk being kicked out and a reboot being initiated.  I got various errors.  I burnt another disk from the same ISO, this time at a slower speed of 16MB/sec, and bumped up the memory in my system to 256MB.  Suddenly, it was smooth sailing until the point that it kicked the disk out and initiated a reboot.

After freaking out, I performed a Ctrl+Alt+Del and then fully powered down my PC.  Then I powered it up and this time the whole installation completion process completed without a single flaw and now it is running great!  Could it have anything to do with letting the system fully power down first?  I do not know.  Something to keep in mind though.[/QUOTE]

Oops.  This was just with Ubuntu 5.10 though.  Not kubuntu.

---

