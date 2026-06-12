---
title: "Trouble with data CD ROMs"
date: 2009-01-24
forum: General Help
---

### Post by Xica_da_Silva on 2009-01-24
I bought a Dell Studio laptop last week with built-in Ubuntu 8.04 but unfortunately am having problems with any data CD ROM that I try to run, including the Ubuntu CD that came with the computer! I tried these on my other pc and the disks themselves seem fine. It appears like the CD is mounted(can see the icon on my desktop), but can't get it to run. I love the concept of Linux but I have to say I am a bit worried that I have really gotten way in over my head...I'm just a person of average intelligence, not a whiz kid! 

Anyhow, when I insert any CD, it says: "This medium contains software intended to be automatically started. Would you like to run it?" After saying yes to this question, I'm getting a message that says "Error autorunning software-cannot find the autorun program". Before this, I was trying to fix a 'failed to mount the cd rom'problem, based on some similar posts and advice, but I fear I may have inadvertantly made things worse by typing in some commands that may not have been appropriate. I already tried to upgrade to the 8.10 version to see if that would fix it but no luck. Any  help would be greatly appreciated.

---

### Post by dcstar on 2009-01-25
> **Xica_da_Silva said:**
> 
........
Anyhow, when I insert any CD, it says: "This medium contains software intended to be automatically started. Would you like to run it?" After saying yes to this question, I'm getting a message that says "Error autorunning software-cannot find the autorun program".
........

CDs with Windows programs will not auto-run in Linux, so that message means little (unless you have wine installed).

If you get that message then the CD is mounting ok, and you will see an icon on the desktop representing the mounted CD.

---

### Post by mb_webguy on 2009-01-25
Can you browse the CD?  If so, then your problem is likely that you're trying to run Windows software, which as dcstar said, won't work.  It's like trying to put diesel fuel in a car that runs on gasoline.  You have to use the right fuel (software) for the right engine (operating system).

Of course, you can install Wine, which lets Windows software run on Linux.  While not all Windows applications will run with Wine, many will, and those that do often run faster on Linux than on Windows.

If this is the case, you can install Wine by adding the [Wine repository]("http://www.winehq.org/download/deb") to your software sources.  You can check on the compatibility of your Windows software on the [Wine AppDB]("http://appdb.winehq.org/").

---

### Post by Xica_da_Silva on 2009-01-25
Thanks for your responses, dcstar and mb_webguy.

   My problem has been partially solved because one of my data CDs is for an HP scanner...and as it turns out, I just needed to plug the thing in and let my system detect it(duh, I feel kind of stupid for not trying it first), without the CD. I didn't realize it would be that simple, sorry! 
  But on the other hand, I'm not sure why the Ubuntu CD would be giving me that same error message. And yes, I can see it on the desktop which seems to mean that it's mounted, but it seems to just drop dead after a second or two of revving up. Not a big deal since I don't really need to do anything with the CD right now, but it bugs me to know there's something not quite right, in case I ever do need it to work. 
  I've also got a Soundblaster X-Fi card with a CD for install but I've read some other threads and I think I can fix the problem. But if you have any suggestions about why the Ubuntu CD won't run I would still be eager to hear. Thanks again.

---

### Post by didac on 2009-01-26
Insert the Ubuntu CD and post the final lines of dmesg, thelines that have to do with the CD.

---

### Post by Xica_da_Silva on 2009-01-26
Thanks, didac. I entered dmesg and this was the only part I could discern that pertained to the CD Rom. Just fyi...I forgot to mention earlier that when I play audio CDs or DVDs there's not problem, it's only data CDs that won't run:  

 6.038357] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
[    6.038363] Uniform CD-ROM driver Revision: 3.20
[    6.038501] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    6.326640] PM: Starting manual resume from disk
[    6.326644] PM: Resume from partition 8:5
[    6.326646] PM: Checking hibernation image.
[    6.326922] PM: Resume from disk failed.
[    6.409268] kjournald starting.  Commit interval 5 seconds
[    6.409279] EXT3-fs: mounted filesystem with ordered data mode.

---

### Post by didac on 2009-01-27
> **Xica_da_Silva said:**
> Thanks, didac. I entered dmesg and this was the only part I could discern that pertained to the CD Rom. Just fyi...I forgot to mention earlier that when I play audio CDs or DVDs there's not problem, it's only data CDs that won't run:  

 6.038357] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
[    6.038363] Uniform CD-ROM driver Revision: 3.20
[    6.038501] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    6.326640] PM: Starting manual resume from disk
[    6.326644] PM: Resume from partition 8:5
[    6.326646] PM: Checking hibernation image.
[    6.326922] PM: Resume from disk failed.
[    6.409268] kjournald starting.  Commit interval 5 seconds
[    6.409279] EXT3-fs: mounted filesystem with ordered data mode.

These lines are dmesg result at boot. Now insert Ubuntu CD and do dmesg again. The last lines may tell us something.

---

### Post by Xica_da_Silva on 2009-01-27
Hi didac, 

 This is with the CD inserted again. I just pasted the last bunch of lines, as per your instructions. Thanks again. I'll check back later.


[   32.821068] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   32.821076] tg3: eth0: Flow control is on for TX and on for RX.
[   35.987253] NET: Registered protocol family 10
[   35.988122] lo: Disabled Privacy Extensions
[   46.036185] eth1: no IPv6 routers present
[   46.436186] eth0: no IPv6 routers present
[   85.673405] CPU0 attaching NULL sched-domain.
[   85.673421] CPU1 attaching NULL sched-domain.
[   85.676147] CPU0 attaching sched-domain:
[   85.676153]  domain 0: span 0-1 level MC
[   85.676158]   groups: 0 1
[   85.676166]   domain 1: span 0-1 level CPU
[   85.676170]    groups: 0-1
[   85.676177] CPU1 attaching sched-domain:
[   85.676182]  domain 0: span 0-1 level MC
[   85.676186]   groups: 1 0
[   85.676192]   domain 1: span 0-1 level CPU
[   85.676196]    groups: 0-1
[  545.634049] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[  710.703196] UDF-fs: No VRS found
[  710.718465] ISO 9660 Extensions: Microsoft Joliet Level 3
[  710.809805] ISO 9660 Extensions: RRIP_1991A
kristi@dell-desktop:~$

---

### Post by didac on 2009-01-28
'Googling' a little bit I found that "no VRS found" means no volume recognition sequence found in your dvd or cd. Have a look a /etc/fstab and check how your dvd reader is mounted. Mine says:

```
/dev/scd0  /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0 0

```

If yours looks alike, I would edit it with 

```
sudo gedit /etc/fstab
```

and change it to:

```
/dev/scd0  /media/cdrom0   iso9660,udf user,noauto,exec,utf8 0 0
```

Reboot and check again.

I don't see any other problems.

---

### Post by mcduck on 2009-01-28
> **Xica_da_Silva said:**
> Thanks for your responses, dcstar and mb_webguy.

   My problem has been partially solved because one of my data CDs is for an HP scanner...and as it turns out, I just needed to plug the thing in and let my system detect it(duh, I feel kind of stupid for not trying it first), without the CD. I didn't realize it would be that simple, sorry! 
  But on the other hand, I'm not sure why the Ubuntu CD would be giving me that same error message. And yes, I can see it on the desktop which seems to mean that it's mounted, but it seems to just drop dead after a second or two of revving up. Not a big deal since I don't really need to do anything with the CD right now, but it bugs me to know there's something not quite right, in case I ever do need it to work. 
  I've also got a Soundblaster X-Fi card with a CD for install but I've read some other threads and I think I can fix the problem. But if you have any suggestions about why the Ubuntu CD won't run I would still be eager to hear. Thanks again.
The Ubuntu CD doesn't contain any Linux program you could run. It only contains the Ubuntu's live environment (which you need to boot with to use) and the Windows installer (which runs in Windows).

(Alternative-CD can be used as a repository, but that's still nothing you could autorun from the CD)

Actually I have never really seen a CD with any auto-runnable content for Linux.. Probably because Linux software rarely comes on install CDs.

---

### Post by Xica_da_Silva on 2009-01-28
*The Ubuntu CD doesn't contain any Linux program you could run. It only contains the Ubuntu's live environment (which you need to boot with to use) and the Windows installer (which runs in Windows).*

Ok...so it seems like that's basically a non-issue for me. Good. Thanks for the info. It seems like most things I want I can just download from the internet, anyhow(assuming internet continues working nicely as it has).

  Meanwhile, I've discovered that the particular version of Soundblaster that Dell sells w/ the pc is not compatible with Linux(there are several Creative soundcards for which you can download drivers to make them work w/ Linux, but mine is not one of them!). Fortunately, I must not have been the only one to have had this problem since Dell cust serv was quite willing to give me a refund on the card. Not really a big deal either since my sound is actually pretty decent once I connect with speakers or headphones.
  Thanks again to both of you for your assistance. Best regards!

---

