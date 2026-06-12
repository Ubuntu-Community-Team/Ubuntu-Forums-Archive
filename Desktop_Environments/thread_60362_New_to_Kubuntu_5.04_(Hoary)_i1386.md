---
title: "New to Kubuntu 5.04 (Hoary) i1386"
date: 2005-08-27
forum: Desktop Environments
---

### Post by OBnascar on 2005-08-27
Besides being new I am having other problems, the search function is not working for me today in the unubtu forums. I am only going to try to resolve just a couple of my problems now so I can get using it, I am excited to do so.

1. The first one is my resolution, I can not even navigate my desktop. Things are so big that like the apply button is covered up, ect.

The default must have been 640 x 480. I need it set to 1024 x 768. I don't have Kubuntu up right now so I am guessing on the following:
When I go into the control center > path > I can find the right tab where it shows what the currant resolution is but can not find an option to change it. How do I do that ?

2. Also a problem I have to resolve right now is when I go into System > user manager it crashes all the time.  Has anyone ever seen this happen ? I want to log in as root to make a Grub rescue disk. Or is there some way to get permission as a user to copy to disk ?

Ok, if I can get this accomplished I will be more than happy for today anyway. Another important one is trying to get my dial-up connected, but I have some good documentation to read on that first. Would the same procedures work for ubuntu as for Kubuntu for the dial-up KPPP tool ?

All comments and suggestion are welcome,
OBnascar

---

### Post by Dustin Wyatt on 2005-08-27
[QUOTE=OBnascar]Besides being new I am having other problems, the search function is not working for me today in the unubtu forums. I am only going to try to resolve just a couple of my problems now so I can get using it, I am excited to do so.

1. The first one is my resolution, I can not even navigate my desktop. Things are so big that like the apply button is covered up, ect.

The default must have been 640 x 480. I need it set to 1024 x 768. I don't have Kubuntu up right now so I am guessing on the following:
When I go into the control center > path > I can find the right tab where it shows what the currant resolution is but can not find an option to change it. How do I do that ?

2. Also a problem I have to resolve right now is when I go into System > user manager it crashes all the time.  Has anyone ever seen this happen ? I want to log in as root to make a Grub rescue disk. Or is there some way to get permission as a user to copy to disk ?

Ok, if I can get this accomplished I will be more than happy for today anyway. Another important one is trying to get my dial-up connected, but I have some good documentation to read on that first. Would the same procedures work for ubuntu as for Kubuntu for the dial-up KPPP tool ?

All comments and suggestion are welcome,
OBnascar[/QUOTE]
 I just got kubuntu going a few minutes ago, but I can answer your question about resolution.

You right click desktop and there's something there about Desktop Settings or the like.  Then you select the Display icon and then change resolution there.

---

### Post by OBnascar on 2005-08-28
[QUOTE=Dustin Wyatt]I just got kubuntu going a few minutes ago, but I can answer your question about resolution.

You right click desktop and there's something there about Desktop Settings or the like.  Then you select the Display icon and then change resolution there.[/QUOTE]

Hi Dustin, I appreciate your reply. That is the path I tried earlier but it only shows the resolution it is set up for now, no option to change it. That is why I am wondering if this is somethiing one has to set at install time, using the advanced install ?

---

### Post by OBnascar on 2005-08-28
[QUOTE=OBnascar]
2. Also a problem I have to resolve right now is when I go into System > user manager it crashes all the time.  Has anyone ever seen this happen ? I want to log in as root to make a Grub rescue disk. Or is there some way to get permission as a user to copy to disk ?[/QUOTE]

Ok, I got this number two resolved by doing a complete reinstall. Now I can get into Systems > User Manager and it works. Also my Konsole works which did not before either on the first install. 

No wonder nothing worked for me using the "Starter Guide", everything was corrupt on my first install.

So I am still looking for a fix with my resolution (#1 on my original post) Now that my Konsole is working, is there a command to set the resolution ?

I have my external serial port modem partly working. It dials-up but then hangs up on “logging on to the network”. Does anyone know what might be set up wrong to do this. The same modem works fine on Mepis which I have set up on  a dual-boot with Kubuntu.

I don't know why I am not getting much for replies on this post, am I doing or saying something wrong ?

I wish I could get some help with Kubuntu, I would really like to get it going and be able to use it. Any help will  be appreciated..

---

### Post by incinerator on 2005-08-28
Please post some details about your hardware setup, what kind of gfx card do you use?

Also it would be useful if you could [pastebin](http://pastebin.com/) your /etc/X11/xorg.conf

Unfortunately, as a spoiled broadband user, I don't know much about modems.

---

### Post by OBnascar on 2005-08-28
[COLOR=Blue]incinerator wrote:
Please post some details about your hardware setup, what kind of gfx card do you use?

Also it would be useful if you could [[COLOR=orange]pastebin](http://pastebin.com/)[/COLOR] your /etc/X11/xorg.conf

Unfortunately, as a spoiled broadband user, I don't know much about modems.[/COLOR]

EMACHINES:  Model# T1742
1733 megahertz Intel Pentium 4
1024 mb DDR PC2100 CL2.5 184-pin DIMM 
MB: TriGem Computer Inc Imperial 1.03
Bios: Phoenix 6.00 08/26/2002
DX-ECDRW100  USB device [CD-ROM drive] CD-R/RW
HL-DT-ST  CD-ROM GCR-8481B
Sound Card - Avance AC97 Audi
ActionTec 56K External Serial Modem
HP 1315 PSC All-In-One 
Display - Intel(R)82845G/GL. Graphics Controller (Display adapter)

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/hdb: 60.0 GB, 60022480896 bytes
16 heads, 63 sectors/track, 116301 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes


I'll try to get the [COLOR=Red]pastebin[/COLOR] of my [COLOR=Red]/etc/X11/xorg.conf[/COLOR] later on today or sometime tomorrow. Thanks......

---

### Post by Darigaaz on 2005-08-28
I'm having a very similar problem to #1 using the Kubuntu Live CD. My xorg.conf file shows 1024x768 as the first resolution listed for every color depth option. It works for me using Knoppix (which uses XFree86), but not Kubuntu with X.org.

I'm not running on the Live CD right now because of the display issues, but I can reboot into it later and get my xorg.conf file.

This is using a Dell 1504FP monitor. Not sure about the graphics chipset, but I think it's an i810 series.

---

### Post by dbott67 on 2005-08-28
[QUOTE=OBnascar]Besides being new I am having other problems, the search function is not working for me today in the unubtu forums. I am only going to try to resolve just a couple of my problems now so I can get using it, I am excited to do so.

1. The first one is my resolution, I can not even navigate my desktop. Things are so big that like the apply button is covered up, ect.

The default must have been 640 x 480. I need it set to 1024 x 768. I don't have Kubuntu up right now so I am guessing on the following:
When I go into the control center > path > I can find the right tab where it shows what the currant resolution is but can not find an option to change it. How do I do that ?

All comments and suggestion are welcome,
OBnascar[/QUOTE]

What's the make & model of your video card and monitor, as well as supported resolutions & refresh rates?  Like you, I was having issues with refresh rates and also modelines and resolution. I got really lucky one time and happened to find a "needle in a haystack", so to speak, when I found someone's posted Xorg.conf file on another site and it worked for me.  Try googling the make & model of your video card, as well as xorg.conf (i.e. ati radeon 9700 xorg.conf).

However, I have since found a better trick:

1. Download & burn a copy of the Ubuntu "Live CD" (or kubuntu/knoppix) --- it seems to do a great job of finding the appropriate video settings (not sure why the installed version doesn't work quite the same way).

2. After booting from the live cd, try to adjust your video settings to your preferred refresh & resolution.

3. If it works, make a copy of the xorg.conf file and copy it to floppy/USB or e-mail it to yourself or print it out...

4. Boot back into your installed version, backup your existing xorg.conf file and then copy the xorg.conf file from the "live session".

5. Restart your x windows session (or re-boot) and you should be able to tweak your video settings to your desired refresh rate.

I've also used kubuntu live cd & knoppix with good results.

Good luck,
Dave

BTW, here is a link to a post I made about my [video fix](http://www.ubuntuforums.org/showthread.php?t=32651) and other problems.

---

### Post by OBnascar on 2005-08-28
[COLOR=Blue]incinerator wrote:
Also it would be useful if you could [[COLOR=DarkOrange]pastebin](http://pastebin.com/)[/COLOR] your /etc/X11/xorg.conf[QUOTE][/COLOR]

Well, I found out it may be some time before I can do that. My modem does not work within Kubuntu so I can not copy and paste directly into [COLOR=Red]pastebin[/COLOR].

And I have not figured out yet how to get permission to the files yet in Kubuntu. So, I'll have to hit the documentation again and see if I can learn anything.

Stay tuned, I'll be back,
Regards,
OBnascar

---

### Post by OBnascar on 2005-08-28
[COLOR=blue] Dave wrote:
What's the make & model of your video card and monitor, as well as supported resolutions & refresh rates?[/COLOR]

Oh boy, that might take me a year or two to figure that out. About the only info I know I posted earlier, ok ? I am no computer tech, but can the video card be built in to the MB ? If so, I think that is the deal.

[COLOR=Blue]Download & burn a copy of the Ubuntu "Live CD" (or kubuntu/knoppix)[/COLOR]

Yes I do have live CD's of ubuntu, Kubuntu, and knoppix, I'll try your suggestion when I get home tomorrow evening.

Just so everyone knows my background, years ago I had Red Hat and Mandrake installed but never got to do anything with them because of my work demand. In the last couple of years I have used Desktop/LX and Linspire for my main distros. So I am struggling here getting going with Kubunbtu, sorry I am such a pain.

Thanks for the tips Dave, we will see what happens.

---

### Post by dbott67 on 2005-08-28
Generally, I like to provide detailed instructions for a couple of reasons:

1. Most of the time, I don't know the experience level of the poster, so I try to offer a step-by-step set of instructions (so please don't be offended if you already know how to do all of this)
2. It serves as a "how-to" for newbies & other users who might come here searching for a resolution to their problem.

It must be the former teacher in me! :)

If you still have troubles on your installed version & you need to get a copy of your **/etc/X11/xorg.conf** file, try the following:

1. Boot into text mode

2. Check your fstab file for the mount point of the floppy drive (not sure if it's different for Ubuntu vs. Kubuntu).  On my machine I typed:
```
cat /etc/fstab
```
and looked for the following:
```
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```
This indicates that the floppy drive should automatically mount to /media/floppy0

3. Copy the xorg.conf file to floppy:
```
sudo cp /etc/X11/xorg.conf /media/floppy0
```
(not sure if you need the sudo or not, but just to be sure... :)

4. Bring it to a working computer and then paste the results here.

You could also use this technique to take a working xorg.conf file from the "LiveCD" and copy it to floppy (or USB, etc) and then copy the file from the floppy into the /etc/X11 directory (just back up your existing xorg.conf file first).  Assuming you've got a working xorg.conf file on floppy, perform the following steps:

1. Boot into text mode on the hosed kubuntu installation

2. Backup your existing xorg.conf file
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
3. Copy your "good" xorg.conf file from floppy to the /etc/X11 directory
```
sudo cp /media/floppy0 /etc/X11/xorg.conf
```
4. Cross your fingers & reboot! :)

The only issues you may face are that the floppy disk does not have an entry in the fstab file (this file basically auto-mounts any file system/hard drive/CD-ROM/floppy disk that is listed in the file).  If you do not see an entry with **/dev/fd0** that points to a mount point (such as **/media/floppy0** or **/mnt/floppy**, etc), you will have to mount the floppy disk manually:

1. First, create a mount point for the floppy:
```
sudo mkdir /mnt/floppy
```
2. Insert a blank disk in the drive
3. Mount the drive:
```
sudo mount /dev/fd0 /mnt/floppy
```

Hopefully, someone will double-check my homework and make sure I didn't make any typos or major errors! :)

-Dave

---

### Post by incinerator on 2005-08-29
Aha, so you have an Intel chipset motherboard and no gfx card, using the integrated (a.k.a. in-degraded) gfx chip on your motherboard. That generation of chips is usually referred to as Intel i810 or i8xx.

One try: edit your /etc/xorg.conf
If you find a line that looks like
**Driver       "vesa"**
change it to
**Driver       "i810"**

Also look for a line like **Section "Screen"**
In that section you will find Lines like
**Modes         "1280x1024" "1152x86" "1024x768"**
Make sure "1024x768" is present in these lines. If not, add it in front of the first mode (plus a space of course).

As for "getting permission to the files in Kubuntu", Kubuntu is not much different from all the other unix-philosophy operating systems. Go [here](http://kudos.berlios.de/kf/kisimlar/tipsntrix.html#rootedit) for an easy way to do it in kde.

---

### Post by OBnascar on 2005-08-29
Well ladies and gents, I “throw in the towel” ! I played with it all day today.....three days total and came to the conclusion that my computer is not compatible with Kubuntu 5.04 That happens, I see it all the time, doesn't mean that Kubuntu is a bad OS. When I installed it the second time it seemed at first I was getting around in it ok, but the more I used it, seemed most everything I needed started crashing again.

I have been Microsoft free for a couple of years now. So my opinion is, doesn't matter what [COLOR=red]Linux distro[/COLOR] one is using, long as it is not MS. Thanks to everyone that tried to help me. Its been great to see these forums are true to Linux forms, good people that want to make Linux work and are dedicated. Who knows, if I ever get a different computer or they come out with a new release, I may be back

Thanks all,
jerry

---

