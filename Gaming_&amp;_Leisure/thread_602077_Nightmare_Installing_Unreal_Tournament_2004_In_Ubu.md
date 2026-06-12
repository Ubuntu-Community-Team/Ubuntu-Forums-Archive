---
title: "Nightmare Installing Unreal Tournament 2004 In Ubuntu 7.10"
date: 2007-11-03
forum: Gaming &amp; Leisure
---

### Post by OmNiPoTeNcE on 2007-11-03
I,ve installed ubuntu 7.10 in order to free myself from windows, the installation ran amazingly smooth (shocked) installed drivers etc. however trying to install ut2004 on my pc led me to an unsolved problem. I have tried all forums,articles and stuff... none works.

im asking for desperate help.

1.)some tell me is a supermounter problem
2.)some say is an sudo export stuff
3.)some say is the automounter.

any help would be appreciated

---

### Post by Cappy on 2007-11-03
If you already installed UT2004 run ```
ut2004
``` in a terminal and post the output.

Did you run the installer with sudo and install to the default location? Have you installed it?

If you need to install it what is your error when you run
```
sudo sh /media/cdrom/linux-installer.sh
```

What is the problem?

---

### Post by Vitamin-Carrot on 2007-11-04
I would recomend copying the linux-installer.sh from the first CD onto your desktop and then running it from there otherwise you wont be able to mount or unmount the disks

"sudo sh /home/vitamin-carrot/desktop/linux-installer.sh"

---

### Post by OmNiPoTeNcE on 2007-11-04
ive already done that. The problem is not runnning the installer, the installer runs perfectly, however when the install starts it prompts me "mount the unreal tournament 2004 play disc", it seems that it cant read the cd or such.

---

### Post by Pevichaey5 on 2007-11-04
when i installed ut2004 it all went ok

when i play ut2004 now it doesn't ask for a cd at all

just seems weird yours is asking for a disc when mine doesn't

---

### Post by Vitamin-Carrot on 2007-11-04
legit disk?
dont have any other windows open on the /media/UT2004_CD1/

---

### Post by PLiNkO on 2007-11-04
Did you install patch 3369
[URL="http://download.beyondunreal.com/fileworks.php/official/ut2004/ut2004-lnxpatch3369-2.tar.bz2"]
 Linux Patch 3369[/URL]

Do you have anything to do with the Omnip)o(tence  ONS clan?

---

### Post by OmNiPoTeNcE on 2007-11-04
Nope,they always confuse me woth some guys from there

anyways,i haven't installed it yet,because it prompts me to mount the play disc in the cd drive,when i insert it and press "yes" it still says that message,it keeps telling me to mount the cd in drive,when it's insrted

this happens next when i insert cd key

help me please

---

### Post by PLiNkO on 2007-11-04
I have a stupid question. Are you running UT2004 natively in Linux or through Wine?

I know when UT is installed under Windows it wants the play disc to run the game every time, until you install the patch, then it works without the play disc.

If you are running UT under Wine it would act like that until you apply the patch.
It should not want the play disc if it's installed natively in Linux. And actually the play disc isn't even needed in the Linux install. Just for the heck of it put CD1 in instead, and see what happens.

Or reinstall UT
[URL="http://ubuntuforums.org/showthread.php?t=231533"]
http://ubuntuforums.org/showthread.php?t=231533
[/URL]

---

### Post by OmNiPoTeNcE on 2007-11-05
well ive posted a screenshot, as u can see i haven't installed it yet.

When i insert the cd it keeps saying me this.

---

### Post by Vitamin-Carrot on 2007-11-05
do you right click on your UT2004_CD1 icon on your desktop and select eject from the drop down menu? and then insert the play disk wait for a bit till your prompted for an action?

I dont understand why is the installer asking for the play disk right after disk 1?

---

### Post by OmNiPoTeNcE on 2007-11-05
you r right after placing # 1 disc and placing the key it says that, so im thinking it cant read the cd contents whatsoever, ive read that is a supermounter or automounter issue i really dunno.

---

### Post by OmNiPoTeNcE on 2007-11-06
I've done that it does not work. One question have u installed ut2004 in ubuntu 7.04? does it prompt u for disc #1 or #2?. I have tried it all by now.

---

### Post by jamesb2147 on 2007-11-09
i'm having the same problem only i'm going through graphically instead of command line.  tried several directories and ejecting/remounting/etc. but to no avail.  seems like somebody's gonna have to come up with a roundabout solution to this.  a real shame too as i remember playing this on 5.10 a while back and probably a release or two before that without any problems (honestly i don't remember).  it was actually way faster in ubuntu than windows, which was a real surprise to me!  anyway, i at least hope the new unreal iii will mean i won't have to worry about it anyway as it will hopefully support the new ubuntu release fully...

also note, i have NOT tried on 7.04, but i am using an upgraded 7.04 install rather than a freshie.  pretty stock options though in terms of OS but i am using an intel graphics adapter (unlikely the culprit, but you never know).  just thought i'd throw in my two cents if it can help at all!  lata playas! :)

---

### Post by jamesb2147 on 2007-11-09
alright, a couple of quick notes too.  firstly, my CD drive doesn't even seem to spin up, even to a low speed.  this indicates (to me, a low-exposure linux user) it's not checking the appropriate directory for the disc at all and it's not some kind of data transfer protocol problem.  secondly, and i'm not even sure about this, but I seem to recall more graphical options for dealing with drives in previous ubuntu releases.  this one seems to severely lack in the mounting dept as i cannot even unmount a CD-rom drive w/o just ejecting the disc.  curious...

---

### Post by ericesque on 2007-11-09
Omnipotence, you're going to hate me for going here, but have you tried installing to a Win box since you started having issues with the disc?  I know the disc probably worked fine last time you installed it, and it's been protected in a cd wallet or jewel case since... but for the sake of covering all angles, see if gets past this point on XP.

If there's anything I've learned about fixing computers, it's that the problem is always the thing that was so stupid, you didn't bother to check. :)

---

### Post by OmNiPoTeNcE on 2007-11-17
ive installed successfuly on winxp not a glitch.

---

### Post by perdition79 on 2007-11-18
This is going to sound like a stupid question, but have you tried ejecting the CD by right-clicking on the desktop icon for the mounted CD and selecting eject?  I just installed UT2004 on 7.04 and that was the only way the linux-installer would let me change discs.  It wouldn't let me just hit the eject button on the drive.

---

### Post by OmNiPoTeNcE on 2007-11-19
yes ive tried it i doesnt work either.

---

### Post by pezplaya on 2007-12-19
i'm having the same problem, ever find a way around it?

---

### Post by turova on 2007-12-26
try

```
export SETUP_CDROM=/media/dvd/
```
replacing /media/dvd with your mounted dvd, obviously.

I got this from another forum and it worked

---

### Post by TB2 on 2007-12-29
I had the same problem, 

```
export SETUP_CDROM=/media/dvd/
```

fixed it indeed, but **make sure you run it before you run the installer.sh!** It wont work if you do it when it asks for the play cdrom.

Thanks turova

---

### Post by gaebriel on 2008-04-02
Awesome! Thanks guys. I have the DVD version and this worked for me as well. 

```
sudo ln -s /media/cdrom0 /media/dvd
export SETUP_CDROM=/media/dvd/
mount /media/cdrom0
sudo sh /media/cdrom0/linux-installer.sh
```

---

### Post by Gillen on 2008-04-03
Hi OmNiPoTeNcE,

Had the same problem of being asked to mount the Unreal Tournament 2004 Play Disc. It turned out that my backup DVD I had made in windows (I had cracked the original over the years) was named incorrectly, the DVD must be named  UT2004_DVD and the directory structure should be, AutoRun.inf  CD1  CD2  CD3  CD4  CD5  CD6  linux-installer.sh  Setup.exe (I left the windows files in place for no reason). I made a new DVD copied the linux-installer.sh to my desktop right click Properties ticked Allow executing file as program closed the properties then gave the linux-installer.sh the double click (sorry) and job done.
Hope this helps.

Regards. Steven.

---

### Post by aonegodman on 2008-04-14
> **gaebriel said:**
> Awesome! Thanks guys. I have the DVD version and this worked for me as well. 

```
sudo ln -s /media/cdrom0 /media/dvd
export SETUP_CDROM=/media/dvd/
mount /media/cdrom0
sudo sh /media/cdrom0/linux-installer.sh
```

[SIZE="6"][COLOR="Red"]OMG!!![/COLOR][/SIZE]  \\:D/

I haven't run this yet, but it looks like it will work so I wanted to get the documentation copied here before I forgot or lost the steps I used.

Here is copy of my Terminal input:

```

:~$ sudo ln -s /media/cdrom0/media/dvd
[sudo] password for user:
?-desktop:~$ export SETUP_CDROM=/media/dvd/
?-desktop:~$ mount /media/cdrom0
mount: No medium found
?-desktop:~$ mount /media/cdrom0
mount: block device /dev/hdd is write-protected, mounting read-only
?-desktop:~$ sudo sh /media/cdrom0/linux-installer.sh
Copying to a temporary location...
Verifying archive integrity... All good.
Uncompressing Unreal Tournament 2004 for GNU/Linux 3319......................................................................

```

I didn't insert my DVD until I got the error above, then continued.

Took about 5 min or more for the install to finish and it will ask you for you 'key'.

I made no prior installs or modifications before doing this. I'm running 'Gutsy' on a AMD Athlon XP CPU w/1GB Ram, Nvidia MX400, installed to an External WD USB HD.

Upon completion of install I got the following notification:

'UT2004 has been installed to  /usr/local/games/ut2004'

'Type ut2004 to start the program'

I will now attempt to run it and get back . . . .

---

### Post by aonegodman on 2008-04-14
OK!!![SIZE="6"][/SIZE]

[SIZE="4"][/SIZE]While a little slower on first start than I remember in Windows and an occasional glitch or hang on changing weapons, I am now running UT2004 on my Ubuntu 7.10 Linux O/S.

I have played through the first 5 Qualification Matches and the graphics are as good or better than Windows IMO.

I was worried that like many other games which I have tried to run, I would have to do a RESTART after playing to get my screen res back or reset mt system. Not this time. It went right back to my 1024x768 setting with no problems.

So far I'd have to say that I've got a successful install of UT2004 on Ubuntu and very happy. Again, there is an occasional slow down or hang during play for some reason, but it picks back up. Why? I don't know.

Thanks again.  Yahooo! \\:D/

---

### Post by papabean on 2008-04-26
I've had similar problems getting UT2k4 to install in both Gutsy and now in Hardy.

I've tried exporting the SETUP_CDROM variable.  I've tried mounting the DVD manually to a different location than the Gnome automounter and re-exporting the SETUP_CDROM variable.  I've tried starting the installer and THEN inserting the DVD.  None of these things worked.

A little investigation showed that GNOME kept automounting the DVD with a filesystem type of UDF (fairly standard for DVDs).  So, on a lark, I tried mounting it from the command line as filesystem type ISO9660 (CDROM).

```
sudo mount -t iso9660 /dev/scd0 /media/cdrom0
export SETUP_CDROM=/media/cdrom0
sudo sh ~/linux-installer.sh
```

That finally did the trick.

---

### Post by gaebriel on 2008-04-28
papabean, you rock. :) After spending the evening trying to install ut2004 on hardy, I had just begun to reinstall ut2004 on a virgin vmware instance with gutsy so I could try copying the /usr/local/games/ut2004 installation directory. I don't know if it makes any difference or not, but I also did everything I could to turn off automounting (see thread [http://ubuntuforums.org/showthread.php?t=771835]("http://ubuntuforums.org/showthread.php?t=771835")) including running ```
hal-disable-polling --device /dev/scd0
``` but I still couldn't get it to install. 

This worked for me on Ubuntu 8.04 as well.

---

### Post by Presariov5000 on 2008-07-19
Hey, I searched on Google how to install Unreal Tournament 2004 on Ubuntu. I am using 8.04. Actually, I bought the Unreal Anthology a couple of days ago. I have played it before but on Windows XP. I couldn't play online, because I installed the game and then put a No CD Crack into the folder so I could run it. So I figured I would buy the game so I could play with him. I installed the game using Wine, because for some reason all 3 linux install files did not work :(. So I installed it successfully, and then went to run it. When it maximized to full screen, it sat there with a black screen. There was sound, but no video. I am trying to install it agian, to see if it works. But I doubt it will. Any help on this??

---

### Post by Presariov5000 on 2008-07-19
Ok. New problem. lol. 
Well, I did not have the linux-installer.sh file. So, I copied the ENTIRE disc right to the desktop, and downloaded the file, and put the file in the disk1 folder. The problem is that it wont load. Now I know you guys have said that you need to run it in terminal, but im a noob right now with Ubuntu (I'm kinda new with it), so what code would I have to put in?
Its on my desktop, folder named Unreal Anthology.

---

### Post by EPOX123 on 2008-07-25
I cant get the textures to show up... any clues its almost like im missing some textures that have to do with the guns.. and i get no sound....

---

