---
title: "can i copy a cd under Ubuntu? if so, how?"
date: 2005-01-24
forum: Desktop Environments
---

### Post by wayover13 on 2005-01-24
I'd like to copy a CD under Ubuntu, but I'm having a hard time figuring out how. I have both a burner and CDROM in my machine, and both work fine. I'm able to read CD's and/or listen to music with the CDROM and am able to burn CD's with the burner--for example downloaded files or iso's. But now, I want to copy a bootable CD (OS installation disk) that sits in the CDROM to a CDR in the burner. I can't figure out how to do this. It seems Gnome lacks tools for doing this. So, what other options do I have? Is there other software I might install that will handle this sort of CD copying? I've install xcdroast and worked a bit with it, but the Gnome support for CD drives (e.g., automount) seems to interfere with it working properly. Must I resort to the CLI, copy the disk as an iso to the hard drive, then burn it from the created iso?

Thanks, James

---

### Post by ubuntu UsER on 2005-01-24
The best cd burning application under Linux (in my opinion of course) is K3b. This is KDE application so it probably won't look good under Gnome but what is better : look or power? ;)

---

### Post by farruinn on 2005-01-24
If you use hoary you might give gaveman a try.  Don't know if K3b or gaveman will do this sort of thing, but it's worth a shot.

~Farruinn

---

### Post by MarcDM on 2005-01-24
[QUOTE=farruinn]If you use hoary you might give gaveman a try.  Don't know if K3b or gaveman will do this sort of thing, but it's worth a shot.

~Farruinn[/QUOTE]
 I just downloaded **graveman** from their website [[http://www.nongnu.org/graveman/](http://www.nongnu.org/graveman/). 

I downloaded the source ( 0.3.2 tar.gz), unzipped it
./configure 
make
sudo make install

graveman

and I was making an audio cd. Listening to that CD right now. Looking @ the options, it does do CD copy. It allows you to copy an ISO to a CD and vice versa. 

Oh and, I'm using warty.

---

### Post by wayover13 on 2005-01-24
I could always get graveman from Debian unstable (I think it's there, isn't it?). Forget k3b. I'm not about to install the entire KDE desktop just for one app. That said, I've heard many good things about k3b. My own preference would be for bashburn. I love its simplicity. But again, it won't work for the same reasons xcdroast wasn't working. Somehow, the Gnome disk automounting interferes. For example, I've told bashburn my mount point for the CDROM is /media/cdrom0. But when I try to make an iso from the disk there, it tells me /media/cdrom0 isn't mounted. But when I issue the command "mount" the system tells me that /media/cdrom0 is, in fact, mounted. It's kind of screwy that the Gnome folks would allow users to be trapped like this: it's a choice of either using the Gnome desktop or being able to copy CD's--one or the other. Can't have both. I hope there's a simple solution I'm overlooking.

James

---

### Post by wayover13 on 2005-01-25
Well, here's a temporary workaround. It involves going to the command line. Hopefully someone will have a suggestion for a program that will work where those I've tried have failed, or a solution to get the programs I do have (Gnome's CD burner, xcdroast or bashburn) working.

To copy a CD, we'll take the extra step of making an iso from the CD, storing it on the hard drive, then burning it with our CD burning prog of choice. Though it involves some convolution, it's still fairly simple.

Insert the CD to be copied into your CD drive. Gnome will automount it, which we'll have to undo. To unmount the CD you've just inserted, open a console and issue ```
 umount /media/cdrom0 -l
``` That will leave your CD in the drive, but with its filesystem unmounted--which is what we want. Then, you create the iso from the CD. In this case, we need to give the device file name for the CD drive, and use the command line program dd (disk dump). dd requires root/superuser privileges (most likely), so we'll sudo to use it, like so: ```
sudo dd if=/dev/hdc of=piratedM$OS.iso
``` This will make an iso of the CD called piratedM$OS.iso in the pwd (present working directory) where you issued the command from. Now, use your favorite burning app--including Gnome's lousy excuse for a burning prog--to burn your iso to a CD. Worked fine for me.

Notes:

1) /media/cdrom0 happens to be the mount point for the CD reader in my machine. Yours may be different: issue the mount command from the CLI to find out the mount point for yours and substitute accordingly.

2) /dev/hdc is the device file for my CD reader. Yours may be different. Again, use mount to find out the device file name for yours and modify my example code accordingly.

3) feel free to substitute sunos, os-2 or the name of the proprietary OS you're pirating in place of piratedM$OS in my example :)

4) you can name the iso file you're creating whatever you want (within Unix file naming conventions), and it doesn't matter what the extension is--or even whether there is one at all. It might be more coherent for you (or your dippy M$ burning software) if you give it an extension like .iso or .img or the like, but it's not necessary.

James

---

### Post by az on 2005-01-25
Graveman has an ubuntu version:
[http://www.grawert.net/ubuntu/dists/warty/universe/binary-i386/graveman_0.2-ubuntu2_i386.deb](http://www.grawert.net/ubuntu/dists/warty/universe/binary-i386/graveman_0.2-ubuntu2_i386.deb)

I found this on the graveman website.

---

### Post by RunningWild on 2005-01-25
[QUOTE=MarcDM]I just downloaded **graveman** from their website [[http://www.nongnu.org/graveman/](http://www.nongnu.org/graveman/). 

I downloaded the source ( 0.3.2 tar.gz), unzipped it
./configure 
make
sudo make install

graveman

and I was making an audio cd. Listening to that CD right now. Looking @ the options, it does do CD copy. It allows you to copy an ISO to a CD and vice versa. 

Oh and, I'm using warty.[/QUOTE]

I've just tried this... clear, fast ... bye bye k3b :D

---

### Post by shmonkey on 2005-01-25
Excuse my ignorance but why can't you do this with nautilus-cd-burner, i.e. drag the files from the cdrom to cd creator ?

---

### Post by matid on 2005-01-25
[QUOTE=shmonkey]Excuse my ignorance but why can't you do this with nautilus-cd-burner, i.e. drag the files from the cdrom to cd creator ?[/QUOTE]
CD copied this way will not be bootable.

---

### Post by wayover13 on 2005-01-25
Well, I don't know what I'm doing wrong but graveman won't detect my CD drives. There being no way to enter them manually (not via the UI anyway), the program is doing me no good at all. Looks interesting, but if it won't help me burn or copy CD's as things presently stand. Why am I the only one that seems to be experiencing these wierd conflicts between Gnome's automount functionality and non-Gnome applications? (at least I asumme that's where my problems originate).

James

---

### Post by nuopus on 2005-01-27
[QUOTE=shmonkey]Excuse my ignorance but why can't you do this with nautilus-cd-burner, i.e. drag the files from the cdrom to cd creator ?[/QUOTE]
 Let me outline the things you CAN'T do with the nautilus CD burner:

* Create audio CD's ... no, a CD with ogg or mp3 music is not cd audio.

* Burn a downloaded iso image to CD. Yes, you can put is iso on a CD, but that is not quite the same as burning the image to the cd.

* Create an iso image out of a CD. Yes, you can take the files off a CD and put it into a folder, but this is not the same either. Will not be bootable if you try to burn it to a CD.


Not saying that nautilus cd burner isnt good ... i use it from time to time, but does not have ANY features I would say should be in a GOOD full featured burning software.

---

### Post by nuopus on 2005-01-27
[QUOTE=wayover13]Well, I don't know what I'm doing wrong but graveman won't detect my CD drives. There being no way to enter them manually (not via the UI anyway), the program is doing me no good at all. Looks interesting, but if it won't help me burn or copy CD's as things presently stand. Why am I the only one that seems to be experiencing these wierd conflicts between Gnome's automount functionality and non-Gnome applications? (at least I asumme that's where my problems originate).

James[/QUOTE]
 Mine wont detect the drive either. The error I keep getting is something to the effect of ... "cant get exclusive access to /dev/hda" which is my hard drive. Why it does not try to find anything outside of /dev/hda I do not know.

I did read on their web site though, that they are planning on the ability to manually add a device with the next release. I hope this happens soon.

---

### Post by saBrEwolf on 2005-01-27
[QUOTE=nuopus]Let me outline the things you CAN'T do with the nautilus CD burner:

* Burn a downloaded iso image to CD. Yes, you can put is iso on a CD, but that is not quite the same as burning the image to the cd.
[/QUOTE]

Excuse me,
Nautilus CD burner does have the capability to burn cd images. If you right-click an .iso nautilus gives an option of "Burn Image To CD" and it indeed does produce the image, not just put the iso on the cd.

O and I recommend gnomebaker. :)

---

### Post by jdodson on 2005-01-27
k3b is really, really good.  now would i like a gnome app that does the same thing, yes.  graveman looks really good and i am going to try that out, but when i want to make a video dvd, to k3b i turn.  

and BTW it does not install the entire KDE desktop, it only installs some QT libraries to run the app.  the footprint is pretty small too.

---

### Post by wayover13 on 2005-01-29
[QUOTE=saBrEwolf]Excuse me,
Nautilus CD burner does have the capability to burn cd images. If you right-click an .iso nautilus gives an option of "Burn Image To CD" and it indeed does produce the image, not just put the iso on the cd.[/QUOTE]

I second that. If I right click on an iso, and tell the system to burn it to disk (don't recall seeing "burn iso to CD" as an option though) it does, in fact, make a CD image. A bootable CD image burned like this results in a bootable CD.

That said, I'm still upset with Gnome about this. Once you go manually unmounting filesystems like I instructed to create an iso from a CD on your hard drive, the UI somehow can't recover from it. Music CD's stop autoplaying when you insert them, CD's mount only partially readable, and user cannot eject a CD. Gnome really painted users into a corner with this CD copying business. Couldn't they at least give some instructions for a stable workaround kludge for doing this? Why did they have to screw up an otherwise great UI with this stupidity? Exasperated cuz I now have to reboot my system to get sane operation of CD drives back (I'm *hoping* that's going to do it). Guess it could be worse: rebooting is fairly optional here: using M$ I think I would have alot less choice about how often I reboot :)

James

---

### Post by Buffalo Soldier on 2005-03-22
[QUOTE=nuopus]* Burn a downloaded iso image to CD. Yes, you can put is iso on a CD, but that is not quite the same as burning the image to the cd.[/QUOTE]If I may correct you sir. Nautilus is able to burn iso image to CD. Both in Warty and Hoary. If you're in Hoary, just right click on an ISO and click *Write to Disc...*

---

### Post by TjaBBe on 2005-03-22
[QUOTE=Buffalo Soldier]If you're in Hoary, just right click on an ISO and click *Write to Disc...*[/QUOTE]

I believe it also works that way under Warty. Don't pin me on it though...

---

