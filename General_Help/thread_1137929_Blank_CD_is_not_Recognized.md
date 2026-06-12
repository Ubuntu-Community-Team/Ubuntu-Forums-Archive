---
title: "Blank CD is not Recognized"
date: 2009-04-26
forum: General Help
---

### Post by Jescrib2 on 2009-04-26
I am trying to made an audio CD using either K3B or Brasero. Once I am ready to burn the CD and place a blank CD in the drive, it is not recognized. I can seem to make the computer recognize the Blank CDs. I have used different brands and both CD-R and CD-RW and no luck. I search and it seems others are having same problem but I have not found a solution. Thanks

---

### Post by Tipped OuT on 2009-04-26
Have you tried DVD's? Have you tried non blank CD's/DVD's? Also, do you have all your hardware drivers installed? Check: System< Admin< Hardware Drivers

Also you might not have auto mount on, I don't know much about that stuff. Try going to your filesystem and look in the Media folder for your CD/DVD Drive.

:(

---

### Post by nikgare on 2009-04-26
Are you using KDE or Gnome - which version of Ubuntu?
What happens when you put tzhe CD in the drive - does the OS notice it?
Is the drive able to reed other CDs?

---

### Post by Jescrib2 on 2009-04-26
I am able to load disc that do have music or movies on them. 
I am using 9.04.

---

### Post by Jescrib2 on 2009-04-26
It does not recognize when I place the blank CD in

---

### Post by lukjad on 2009-04-26
This reminds me of a problem I had with 8.04. For some reason I couldn't use blank CD/DVDs. It was fixed in Intrepid though. If you need to burn something use a Slax CD. Of course, you can't burn one yourself, but try to get a friend to. ;)

---

### Post by Seventh Reign on 2009-04-26
Can you tell us what CD Burner and Blank Media (Manufacturer etc) you are using?

---

### Post by Jescrib2 on 2009-04-26
I have a Sony vaio VGN-FS940
I am trying to burn a CD on Magnavox compact disc recordable 52X 700MB 80min

---

### Post by grantjohnston on 2009-04-26
I'm having the exact same problems.


It will recognize media with information on it (on both drives), but won't see ANY blank media, whether it be CD OR DVD. Tried different brands, no avail.


I check /etc/fstab and it only had one DVD drive in there, even though when I put in a disk (that had information on it)

So, me being me, I went ahead and changed things around, trying to **** with it and added it to /etc/fstab

i put

```
/dev/sr0        /media/cdrom1   udf,iso9660 user,noauto,sxec,utf8 0       0
```

Pretty much verbatim copied what the other drive had, just changed /dev/sr1 to /dev/sr0

Still nothing, it's quite frustrating as well. 


Anyone have any clues? If I need to post more info, please, let me know and I will.



grant

---

### Post by grantjohnston on 2009-04-28
Anyone? This is driving me nuts. I'm having to transfer files to my Macbook to do ANY burning over the network, which takes a lot of extra, unneeded time.

---

### Post by bach on 2009-04-28
I am having the same problem. I have also noticed that the Gnome software (Rythmbox, Totem, Sound Juicer) do not recognize the CDs and DVDs I insert in the CD ROM, but I can play CDs and DVDs using vlc and Kaffeine. 

In /etc/fstab I have 

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Any hints?

---

### Post by bach on 2009-04-28
More info: 

cribari@jsbach:/etc$ dmesg | tail -n10
[28497.372840] Buffer I/O error on device sr0, logical block 4
[28497.372845] Buffer I/O error on device sr0, logical block 5
[28497.372851] Buffer I/O error on device sr0, logical block 6
[28497.372856] Buffer I/O error on device sr0, logical block 7
[28497.396847] end_request: I/O error, dev sr0, sector 0
[28497.396860] Buffer I/O error on device sr0, logical block 0
[28497.420821] end_request: I/O error, dev sr0, sector 4
[28497.420832] Buffer I/O error on device sr0, logical block 1
[28498.368784] end_request: I/O error, dev sr0, sector 0
[28498.394009] end_request: I/O error, dev sr0, sector 0
cribari@jsbach:/etc$

---

### Post by grantjohnston on 2009-05-13
I've been neglecting this thread. I really need to get this issue figured out.. Does ANYONE have a clue as to what's doing this on this distro?

---

### Post by grantjohnston on 2009-07-22
bump bump bump. Still having this problem and just been neglecting it and going end around on it. Even in retarded ways (like sending gigs of information to another computer to burn on it via wifi).


Does anyone have ANY idea why this thing is doing this ****? It's driving me INSANE and I'm tired of having to wait an hour plus just to burn something because this damned thing doesn't recognize blank media...

---

### Post by curtis0432 on 2009-07-23
I still cant believe that no body has been able to fix this problem. if i cant get it fixed in a week I think I might aswell just switch back to Microsoft or etheir try a different linux.

---

### Post by ub40d on 2009-07-23
I have ubuntu 9.04.

Arrived into this thread from google because I could not burn a data dvd with the default app (Brasero). Went through the motions, did the project and then it said "please insert blank media in the drive". But I already had a disk in there!

Drive is a Pioneer DVD-RW  DVR-112. I have successfully burned iso images with it under ubuntu many times (simply by double-clicking on the .iso and feeding the drive a blank disk).

I could see no way of making Brasero believe that a blank disk was in the drive.

Following one of the posts above I went for k3b.

sudo apt-get install k3b

and it kind of worked: it saw the drive, even started writing to it. Now however I got a write error (on verbatim disks that are usually reliable) so I'm still not home free; but that's a different story...

Hope this helps someone

---

### Post by ub40d on 2009-07-23
Update on k3b:

I did a "simulate instead of writing". Went ok.

With another blank dvd-r, I managed to record the project, up to "writing successfully completed". Then the disk was ejected. At that point the verification was supposed to happen, but the disk drawer was never closed by the program. After waiting for a long while I closed it manually. Still, nothing happened. After another couple of minutes I aborted it.

So now I've got a disk that was (in theory) written to, but that wasn't verified. I shall now try verifying it by hand with diff but it's a bit of a pain.

Hmm, if I go to places / computer and double-click (in nautilus) on cdrw/dvdrw drive, I get "unable to mount location; no media in drive".

Not good...

---

### Post by ub40d on 2009-07-23
Verified the disk with diff and all was ok. Nice.

Then found a possible culprit: in the various virtual desktops there were open windows for brasero and other junk. Maybe that's what prevented k3b from doing its job properly. Closed everything.

Now, on inserting the written dvd, it would appear on the desktop with its volume title. Good.

And now if I put in a blank disk, it also appears on the desktop saying "blank dvd-rom disk". That's more like it!

I am currently recording another data dvd with k3b, hoping that this time verification will work. If it does, I'll give brasero another try too.

---

### Post by ub40d on 2009-07-23
Ho-hum. Still got a problem.

K3b: 
writing succesfully completed. 

Then it ejects the disk and sits there saying "verifying written data", which of course it won't do since the disk isn't even spinning.

I close the drawer by hand. Now the written disk appears on the desktop with its volume name. But k3b still sits there idle, saying "verifying written data" and the bar stuck at 0%, with the drive not spinning. I have to abort. I have to cancel.

---

### Post by ub40d on 2009-07-23
OK, once again the manual verification with diff went ok, so the disk had been written correctly, but it's still a nuisance. Never managed to successfully verify a disk with k3b yet.

Now I always get a "blank dvd-rom disk" icon on the desktop (GOOD) when I insert one in the drive, which I didn't when I started posting, and I'm not sure what caused this. No reboots between then and now. I did close those few windows but hey.

Now trying Brasero again, for the moment a SIMULATION of writing to a fourth dvd...

---

### Post by ub40d on 2009-07-23
Brasero simulation not good... reason unknown but it was taking ages and had got down to 0.5x writing speed (on a drive that can do 18x or perhaps more).

Now writing with k3b again but I guess I won't be able to verify.

I don't think there will be much new to report so I'll probably stop here with these updates. 

The most puzzling part is that I started searching the web because my problem was that the system couldn't recognize I had a blank dvd in the drive, and now it does, but I don't know why! So I don't really have the feeling that I found a fix for anything, unless it really was that I accidentally had more than one brasero window open even from the start, without realizing it, and that was what stopped it all.

Anyway, good that I found k3b out of all that.

---

### Post by Maheriano on 2009-07-23
I don't want to read the whole thread to see if this has been posted but one time this happened to me and it was because my drive is CDR+ only and the CD I was using are CD- so it wouldn't recognize them. Once I bought some CD+, it worked fine.

---

### Post by ub40d on 2009-07-23
> **ub40d said:**
> Ho-hum. Still got a problem.

K3b: 
writing succesfully completed. 

Then it ejects the disk and sits there saying "verifying written data", which of course it won't do since the disk isn't even spinning.

I close the drawer by hand. Now the written disk appears on the desktop with its volume name. But k3b still sits there idle, saying "verifying written data" and the bar stuck at 0%, with the drive not spinning. I have to abort. I have to cancel.

More web searching gave me a fix for that: 
settings / configure k3b / advanced / do not eject medium after write process.

It worked. After checking that box, for the first time I could get k3b to successfully write and verify a data dvd.

---

### Post by ub40d on 2009-07-23
> **Maheriano said:**
> I don't want to read the whole thread to see if this has been posted but one time this happened to me and it was because my drive is CDR+ only and the CD I was using are CD- so it wouldn't recognize them. Once I bought some CD+, it worked fine.

You probably meant DVD---these are the ones with the plus and minus. CDs don't have that. 

Anyway, this was not my case, as the drive I have (like most ones made in the past few years) does both formats.

---

### Post by Maheriano on 2009-07-24
> **ub40d said:**
> You probably meant DVD---these are the ones with the plus and minus. CDs don't have that. 

Anyway, this was not my case, as the drive I have (like most ones made in the past few years) does both formats.
No, I meant CD as in compact disc, as in a disc that is compact....which is what a DVD is. I'm just going to start saying disc from now on so people don't get hung up on definitive acronyms and falsely believe that a DVD is not a compact disc.

---

### Post by mkvnmtr on 2009-07-24
I seem to be having the same problem. I first thought my hardware went bad but this seems to be a 9.04 problem. I am going to look through the known problems and if I do not find a solution I believe a return to 8.10 will be my fix. Everything worked good for me in 8.10. I guess I am a nut for always going for the latest distro.

---

### Post by Maheriano on 2009-07-24
> **mkvnmtr said:**
> I seem to be having the same problem. I first thought my hardware went bad but this seems to be a 9.04 problem. I am going to look through the known problems and if I do not find a solution I believe a return to 8.10 will be my fix. Everything worked good for me in 8.10. I guess I am a nut for always going for the latest distro.

I burned a CD (okay, this time it's a 700 meg CD) last night with K3B in 9.04 with validation and when I popped the CD back in, it did the validation on its own. It was a 32 bit 9.04 LiveCD I was using to install on a media box.

---

### Post by grantjohnston on 2009-07-26
> **ub40d said:**
> You probably meant DVD---these are the ones with the plus and minus. CDs don't have that. 

Anyway, this was not my case, as the drive I have (like most ones made in the past few years) does both formats.


Dude, try and contain your posts to perhaps one or two long ones.... Most people don't want to read a new post every 15 minutes with some small, relatively meaningless update, especially with your problem not exactly being the same as the rest of ours relating to this thread....


> **mkvnmtr said:**
> I seem to be having the same problem. I first thought my hardware went bad but this seems to be a 9.04 problem. I am going to look through the known problems and if I do not find a solution I believe a return to 8.10 will be my fix. Everything worked good for me in 8.10. I guess I am a nut for always going for the latest distro.

Not really. Many people go for the distro update right off the bat... I understand having troubles at the launch of it.. But this far into it?..

I WOULD downgrade, but my drive crapped out on my 'update' distro. So I did a base-install on this one, so I'm SOL, completely.

---

### Post by grantjohnston on 2009-09-04
Is there STILL no resolution for this issue, yet??

---

### Post by junglist313 on 2009-09-27
Bump, I just started having this problem yesterday. Used to work fine, still recognizes cd's and dvd's with data on them but will not recognize blanks at all. HPdvd740 drive running ubuntu 9.04 64bit fully patched. Drive works fine in windows. This is very frustrating and I hope it is fixed soon.

---

### Post by junglist313 on 2009-09-27
Has anyone filed a bug report at Launchpad on this?

---

### Post by meditatingfrog on 2009-09-28
Have you tried double clicking the cd rom drive in places, then trying to burn the cd?  I was able to burn a copy of Heron this way, using nautilus-cd-burner.

---

### Post by junglist313 on 2009-09-28
> Have you tried double clicking the cd rom drive in places, then trying to burn the cd? I was able to burn a copy of Heron this way, using nautilus-cd-burner.

That will not work because the drive thinks there is nothing in it. When I go to places and double click the drive it says "No media in drive". It's not that I don't know how to burn a blank, Ubuntu will not recognize a blank cd. Hardware polling is enabled and there is an fstab entry for the drive, Ubuntu recognizes the drive, recognizes disks with data on them but not blanks.

---

### Post by luiverco on 2009-09-28
Hi
I'm having the very same problem as you
I have 8.10 fully updated.

The funny thing is that this used to work. I have burnt lots of CD's in the past.I can't recall the last CD I burnt but the last DVD was 3 months ago
Non-blank CD's and DVD's still work.
Blank DVD-R's and DVD-RAM are still detected but for some reason CD's are not
This looks to me like some update may have broken it. 
BTW my CD/DVD unit is LG- Super Multi Drive

---

### Post by meditatingfrog on 2009-09-28
> **junglist313 said:**
> That will not work because the drive thinks there is nothing in it. When I go to places and double click the drive it says "No media in drive". It's not that I don't know how to burn a blank, Ubuntu will not recognize a blank cd. Hardware polling is enabled and there is an fstab entry for the drive, Ubuntu recognizes the drive, recognizes disks with data on them but not blanks.

The procedure I followed was as follows:

Double click iso.  nautilus-cd-burner would open.  Press burn.  Prompted to enter blank cd.  Blank cd already in drive.  Click burn again.  Same message.  Clicked places, optical drive.  Go back to nautilus-cd-burner, click burn.  CD burning occurs.  I didn't know that one had to open the drive in places to get the nautilus-cd-burner to burn.  This was the first disc I burned using nautilus-cd-burner.  

I'm using kernel 2.6.29.  Not sure why else it would work for me.

---

### Post by arvevans on 2009-09-28
I'm having the same problem.  Something happened (update software...maybe) in the past couple of months that seems to have made the CD write process unstable.  I usually use K3B (32-bit Ubuntu Gnome 9.10, AMD 2X64-3000, 2GB RAM, 160 GB HD, 4GB Swap, etc.) and am having problems recognizing a blank CD, and with "Error on Track-1" when doing write verification.
_._

---

### Post by eMJayy on 2009-09-28
I'm on 9.04 32-bit and I'm not experiencing this issue. I just inserted a blank CD-R (TDK brand) into my Lite-On DH-20A3P Multi drive and it was detected. The desktop now has a "Blank CD-R Disc" icon. I'm fully patched as well and am using the latest default Ubuntu kernel (2.6.28-15-generic).

I'm not convinced this is a Ubuntu issue at all. I'm seeing a large number of complaints spanning years by persons running Windows who encountered the identical problem with their drives. If my memory serves me correctly, it's actually the firmware that's responsible for detecting the type of disc that's in an optical drive, as well as for making all the laser adjustments necessary for reading from and burning to the disc. Neither the OS nor the burner software has control over this process. That information is supposed to be encoded on the blank disc itself in the form of a code of some kind that has to be matched to disc tables that the drive has stored within its firmware. If the firmware is not reading or recognizing this code, it won't be able to see the disc in the drive bay.

---

### Post by junglist313 on 2009-09-28
> **eMJayy said:**
> I'm on 9.04 32-bit and I'm not experiencing this issue. I just inserted a blank CD-R (TDK brand) into my Lite-On DH-20A3P Multi drive and it was detected. The desktop now has a "Blank CD-R Disc" icon. I'm fully patched as well and am using the latest default Ubuntu kernel (2.6.28-15-generic).

I'm not convinced this is a Ubuntu issue at all. I'm seeing a large number of complaints spanning years by persons running Windows who encountered the identical problem with their drives. If my memory serves me correctly, it's actually the firmware that's responsible for detecting the type of disc that's in an optical drive, as well as for making all the laser adjustments necessary for reading from and burning to the disc. Neither the OS nor the burner software has control over this process. That information is supposed to be encoded on the blank disc itself in the form of a code of some kind that has to be matched to disc tables that the drive has stored within its firmware. If the firmware is not reading or recognizing this code, it won't be able to see the disc in the drive bay.

I am starting to agree with you here. I have a hpdvd740b and when I google just the model number the first result is windows users having the exact same problem. I bought a new drive today and it seems to be working ok. The really weird part is I put the "malfunctioning" hpdvd740 in a old windows xp box and it seems to be working fine. Very strange.

---

### Post by Skilly on 2009-10-08
I disagree about this being a non-issue. Too many people are having the same problem, myself included (still unresolved).

---

### Post by grantjohnston on 2009-11-01
> **junglist313 said:**
> I am starting to agree with you here. I have a hpdvd740b and when I google just the model number the first result is windows users having the exact same problem. I bought a new drive today and it seems to be working ok. The really weird part is I put the "malfunctioning" hpdvd740 in a old windows xp box and it seems to be working fine. Very strange.

I have the same drive.


Everybody that's having this problem, please post the specific drive you're using while having this issue.

> **Skilly said:**
> I disagree about this being a non-issue. Too many people are having the same problem, myself included (still unresolved).

I agree, this is a huge issue, and it's plagued users spanning 2 new distros (since 9.04). I installed Karmic 2 days ago and am still having the same troubles I have been.

I'm tired of having to transfer files over my network or to an external HD and then to my MacBook to burn the software. Most of the time, the files are very large, and I'm not about to start doing all of my downloading on my MacBook, I don't want to leave it on all the time, that's what my Desktop is for. 


As I said, everybody please post up what drive you're using to have these problems, and we might get it figured out faster! In the mean time, if I don't find a firmware update for my HP740b DVD Burner, I have an extra DVD burner laying around I'm going to pop in and hope and see that that might fix it.


I'll keep you updated!



Thanks

Grant

---

### Post by grantjohnston on 2009-11-01
[SIZE=7]IT'S THE DRIVES!!!!!![/SIZE]



Guys, it's the f*cking drives!


Even after updating the firmware for the HPDVD740b(i) in a Doze environment, it still wouldn't work.

I had an extra DVD+/-DL laying around from a computer I had worked on that I pulled out. I threw it in, put it on cable select and put in a DVD and it popped right up! Even the disks that wouldn't work on this machine before worked great!


I started uncontrollably screaming when I found out it worked.


So, for all of you that have drives that aren't working, post them up in this thread and hopefully someone else that has that same drive can swap it out and try a different one to see if it can be added to the 'blacklist' of non-working drives.

I'll start it off.




[size=4]**HP740B(i)**[/size] 



Good luck everyone!



grant

---

### Post by j.m.wilson@earthlink.net on 2009-11-02
For what it is worth part of this problem isn't the drive hardware necessarily.  Different drives respond differently to linux distros.  In my case it is a mount problem.  Sounds like that is the case with many of the previous posts.  Install gnome-volume-manager will fix the mount isssue.  Sudo apt-get install gnome-volume-manager.  This will auto mount blank disks of all kinds.

---

### Post by grantjohnston on 2009-11-02
> **j.m.wilson@earthlink.net said:**
> For what it is worth part of this problem isn't the drive hardware necessarily.  Different drives respond differently to linux distros.  In my case it is a mount problem.  Sounds like that is the case with many of the previous posts.  Install gnome-volume-manager will fix the mount isssue.  Sudo apt-get install gnome-volume-manager.  This will auto mount blank disks of all kinds.

Had GVM installed, it's not it. Trust me, I've been dealing with this issue spanning the past 2 distros, and some people have had the problem before that.

Not only that, but it seems to be centered around a certain few drives, namely the HP740b(i) lightscribe burner. It's something either with the drive (not firmware, because as I stated, I did the firmware update in a Windows environment), and the drive worked before. Or it's something with the distro itself.

---

### Post by Logurt on 2009-11-03
[COLOR=#204A87]**[SIZE=3] [/SIZE]**[/COLOR][SIZE=3]I am having the same problem with my dvd burner in ubuntu. Using Brasero it fails to recognize blank discs for burning. The dvd player reads movies, audio, and data fine. 

It is a Tsstcorp dvd+-rw TS-L532B, it is a part of my dell e1505. 

The burner works fine in os-x boots and windows.


[/SIZE]

---

### Post by mickchilders on 2009-11-09
This is a new problem that has cropped up for me with ubuntu 9.10 and it involves automounting *anything*, USB drives, CDs, DVDs... And it is aparently a complex issue, meaning possibly the kernel and gnome-volume-manager from the stuff I have read that have fixed this problem. 

I have two ubuntu PCs that I just installed from scratch:

1. an older pentium 4 that has no CDROM, but automounts USB sticks perfectly. I actually installed 9.04 (32bit) and then added ubuntu studio. a few days later i upgraded it to 9.10 when it came out. never had a problem automounting. However, this is a recording machine and while using SOX, I have been getting ALSA over-run errors ever since I upgraded to 9.10 while using the generic kernel or the rt kernel. 

2. my laptop has had ubuntu 8.10(64bit) which automounted USB sticks and Blank CDs and DVDs fine. Then I upgraded it to 9.04 which also worked fine. When I was upgrading to 9.10, I accidently let the battery run down in the middle of the upgrade and rendered it unbootable. So I wiped the partition and installed 9.10 on a fresh clean partition. It still dual-boots Vista which works fine. After I installed 9.10, it will not automount anything. 

a guy called eschvoca traced the problem to this kernel patch listed here: [http://ubuntuforums.org/showthread.php?p=8127907](http://ubuntuforums.org/showthread.php?p=8127907)
...where he shows what he patched to fix his problem.  Still others insist that the problem is attached to the gnome-volume-manager verson 2.24 

I even read that nautilus is due to take over the automounting as of version 2.24 see here:   
[http://www.mail-archive.com/debian-bugs-closed@lists.debian.org/msg227164.html](http://www.mail-archive.com/debian-bugs-closed@lists.debian.org/msg227164.html)

Now that I stop to think about it, gnome-volume-manager had to be installed on my laptop as part of my troubleshooting, which didn't do any good. I will have to go look now and check my version of nautilus. not sure if this helped, but good luck!

---

### Post by paks.dreamer on 2009-11-16
I have the same problem.  My drive mounts perfectly fine, can open blank disc for burning, but won't burn -- it fails with any program (including k3b).  The programs seem to recognise my drive while I'm adding files for burning, but as soon as I start the process it either doesn't give me the burn option, pretends to work but doesn't, stops working, opens the drive, or "fails to write an ISO" (which I wasn't trying to do), depending on the program.  In the case of k3b it won't begin the burn process at all, instead asking me to "Please insert an empty or appendable Double Layer DVD+/- R medium" (which I have, and it was mounted).

Mine is a Lightscribe CD/DVD drive also, so I think grantjohnston is correct.

---

### Post by sparky64 on 2009-11-21
I am having same problem.
I have 2 drives a sony and a generic (no idea what make without taking it out, even dohicky just lists it as an ide device).
Neither will register a blank cd. cd's with data will work.
I know they worked up to a month ago as i used k3b to burn some pdf's to a blank cd using the beta version of 9.10.
I know the drives are ok as when i boot into suse 11.1 it works fine.
it also works using a live cd of suse and 9.10beta although a blank cd shows up as a d/layer dvd under suse.
dvd-/+ w/rw and rom all show up on device notifier with option to burn using k3b/brasero etc.
Have checked permissions and all are ok.
Closest bug reports I can find are.
[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/363323](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/363323)
[https://bugs.launchpad.net/ubuntu/+source/nautilus-cd-burner/+bug/220957](https://bugs.launchpad.net/ubuntu/+source/nautilus-cd-burner/+bug/220957)

will add my report to 363323 as i use kde4 but problem persists using gnome apps as well.

---

### Post by olpp on 2009-11-27
I've had the same problem with 9.10 and a Samsung DVD drive. Today I tried to run brasero with sudo - and it worked! I wonder if it has something to with permissions? At least in my case?

---

### Post by sparky64 on 2009-11-29
found this bug report.
[https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/397906](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/397906)
seems to be a kernel problem on 64 bit.
Also cropping up on suse11.2 (still ok on 11.1 with older kernel)
I have to use an older live cd to burn cd's . Lucky i still have 2 drives.

---

### Post by nirpius on 2009-12-21
I have the same problem. It is not the drives.

I am on Ubuntu 9.10 kernel is blahblahblah.31

Acer Aspire One
Liteon external drive

all of this worked fine originally when using the same hardware on 9.04. I assume it is a kernel issue but don't know how to downgrade my kernel...

---

### Post by sparky64 on 2009-12-22
I have just been faffing with several drives i have spare and some i borrowed.
The new drive i fitted is a sata connection and works perfect.
A older drive i borrowed with sata connections works fine.:)
I also tried an extra 3 drives with ide connectors non of which identified blank cd's and some dvd media. All of which when tried in a windows box worked.
My mob is an asus p5q pro set to AHCI mode.
If your drive is not recognizing cd's post if sat or ide and what mode it is , It might help sort it out.

---

### Post by grantjohnston on 2009-12-22
Hmmm.... Well, I have gotten it to recognize blank media when it is inserted, and it burned a dual layer DVD the other day.


But, now it doesn't want to burn EITHER of my blank single layer DVDs (haven't tried CDs yet).


Here's my log output in Brasero (it does the same type of error in other software, too.)

```
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/home/grant/Desktop/GARDEN_STATE_2004.ISO of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: :-[ PERFORM OPC failed with SK=2h/CANNOT WRITE MEDIUM - INCOMPATIBLE FORMAT]: Wrong medium type
BraseroGrowisofs stderr: /dev/sr0: "Current Write Speed" is 4.1x1352KBps.
BraseroGrowisofs stderr: :-[ WRITE@LBA=0h failed with SK=2h/CANNOT WRITE MEDIUM - INCOMPATIBLE FORMAT]: Wrong medium type
BraseroGrowisofs stderr: :-( media is not formatted or unsupported.
BraseroGrowisofs stdout: HUP
BraseroGrowisofs stderr: :-( write failed: Wrong medium type
BraseroGrowisofs stderr: HUP
BraseroGrowisofs process finished with status 124
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
```



Any thoughts?


Thanks


grant

---

### Post by JoelOl75 on 2009-12-23
CD?DVD drives for me never last more than a year usually manifesting with not being able to burn DVD's, to not being able to burn CD's to not recognizing blanks....

Of course I belive cigarette smoke destroys them in short order...  I like my slim external USB drive which allows me access to the lens so I can get some 99% isopropyl in there with a cotton swab to clean it.

---

### Post by ayumu on 2010-02-24
Hi there,

 I had same problem with Ubuntu 9.10 and Sony CD Burner. Think that is a Brasero bug because I installed GnomeBaker and now i can write/erase CD blank without problems. cdrecord ran perfectly too

---

### Post by rtimai on 2010-05-16
Ubuntu 10.04
Kernel 2.6.32-22-generic
Gnome 2.30
HP CD-Writer Plus 8200
11-year old Linux PC still works faster than XP stations at work, btw

I had the same results as Ayumu. Switched from Brasero to GnomeBaker, and blank CDs are recognized and burned. There appears still to be the issue of auto-detection, though. I have to eject and re-insert the newly-burned CD before it appears in the left window of Nautilus. May be related to Lucid switching from HAL to DeviceKit for hardware detection, and different optical media programs using different hardware detection calls. Anyway, thanks, Ayumu, for the tip.

I removed Brasero and dependencies with no issues, btw.

---

