---
title: "One Newbies Sorry Story of Misery and Defeat"
date: 2006-01-08
forum: Desktop Environments
---

### Post by Tominator on 2006-01-08
I really like Ubuntu, unfortunately I don't know code so I am trying to use it as I would use  Windows, point and click. Not having much luck, my latest frustration is trying to  save a file to a floppy, doing research but have not figured it out yet. Anyways, I started out with a decent machine and loaded Ubuntu 5.10 beside a copy of Windows 2000. Every thing worked wonderfully so I decided to to get rid of the hated Windows. That turned out not well. In my naive innocence I decided that the best way to totally rid myself of Windows would be to use a 98 start up disk and I fdisked and formatted away. Then I reloaded Ubuntu and all was definitely not well. Lo and behold I had lost my wireless connection. Still ain't got it back.
There are some other things I have been trying to do unsuccessfully, I barked up a bunch of trees trying to get yahoo, Java has been no fun at all, I have cut and pasted more gibberish than a 4 year old in kindergarten. I figured all of the worthless commands I have used could cause problems in the future, so a fresh install is a good idea. So, like a dummy, I wiped the hard drive again so I could re-install Ubuntu. Huge mistake, the system no longer recognizes my cdrom and  it is not shown as an option at setup. Can not reinstall from my ubuntu disk. Of course I have tried my "trusty" Windows 98 start up floppy, repeated tries have led to repeated frustrations. Still no cdrom.
Now, it occurs to me that a Ubuntu boot disk would be valuable to me in this instance, From my research, Ubuntu seems to feel that a cdrom is sufficient, not for me for the aforementioned reason. I have surfed and downloaded something that claims to be a good boot up disk, I dragged it to my home folder and did hours of searching trying to figure out how to point and click it onto a floppy, no luck as of this time. Help file not much help on this subject. I think i figured it out  but for some reason the file is not of all things, "mountable" lol. Simply tragic I tell ya. Any concise non code advice would be much appreciated. Thanks in advance for your attention and I will log in again tomorrow. Good night all.

---

### Post by Michael Steinberg on 2006-01-08
Your BIOS doesn't allow booting off a CD-ROM?

If it doesn't, have you checked out the instructions at [https://wiki.ubuntu.com/SmartBootManagerHowto](https://wiki.ubuntu.com/SmartBootManagerHowto)?

That should give you a real Ubuntu startup floppy.

And then forget about Win 98, it's bad even by Microsoft standards...

---

### Post by aysiu on 2006-01-08
Sounds to me like a combination of:

1. You rushed in too fast before really knowing what you were doing
2. You were given the impression that Ubuntu is a point-and-click installation/configuration distro--it is not, which is why you were copying and pasting "silly commands."

In the future, I'd recommend...

1. Backing up all data before doing anything.
2. Trying live CDs until you're comfortable with Linux--then installing later.
3. Using a more point-and-click distro that comes with a lot of non-free codecs; perhaps Mepis or PCLinuxOS might be more your cup of tea. Both, by the way, are live CDs that also install.

---

### Post by towsonu2003 on 2006-01-08
As you are able to boot from floppy, I think (as the previous poster suggested) you'll need to enable booting from cd-rom in your BIOS... I am not very good at this but when you boot up your computer, it will say "press <something> to go to options" or something similar. Press that keyboard button as fast as possible (it may be F12, ESC, F1 or something else) to go to your BIOS options. Be very careful as that's a risky place... you need to find an option where it talks about the booting order. It usually is 
floppy
cd-rom
hard disk

you need to change it so that it is
cdrom
floppy
had disk

meaning cd-rom is the first... save and exit from BIOS and it will reboot. put in the cd-rom and it should now work -hopefully. Also, post your exact specs (make and model) of your computer, so if someone else has the same computer & see this post, may be able to better help you...

Also, I strongly suggest that you dual boot until you figure out more about linux (will take very long ;) )

Edit: I was still writing this when aysiu poste, so I will add openSUSE as a good choice for a newbie installation although I dont remember how it performes when it comes to codecs...

---

### Post by dueY on 2006-01-08
How did you install Ubuntu the first time?  I'm guessing you booted from CD-ROM if you had Windows installed as well.  Which makes no sense why it won't boot now, unless you or someone else has changed your boot order in BIOS.

---

### Post by Tominator on 2006-01-09
[QUOTE=Michael Steinberg]Your BIOS doesn't allow booting off a CD-ROM?

If it doesn't, have you checked out the instructions at [https://wiki.ubuntu.com/SmartBootManagerHowto](https://wiki.ubuntu.com/SmartBootManagerHowto)?

That should give you a real Ubuntu startup floppy.

And then forget about Win 98, it's bad even by Microsoft standards...[/QUOTE]
No, it doesn't show a cdrom installed anymore. Thanks for the very helpful tip. By the way, the guy that runs that site is protesting google and will not allow access if you are using Mozilla or Firefox. He makes a good point. 
Also, it was windows 2000 that I was using on that computer, I just happened to have a 98 boot disk handy. Thanks again, tom.

---

### Post by Tominator on 2006-01-09
You are absolutely correct. I have already checked out mepis and prefer Ubuntu, and the computer in question is not needed so I'll keep playing with it. I am using ubuntu on this system as well. What is your estimate as to when Ubuntu will become "ignorant user" friendly? Thanks, Tom.

---

### Post by aysiu on 2006-01-09
[QUOTE=Tominator]What is your estimate as to when Ubuntu will become "ignorant user" friendly? Thanks, Tom.[/QUOTE] Is the ignorant user checking [the hardware compatibility list](https://wiki.ubuntu.com/HardwareSupport) before installing Ubuntu? If so, it's ready now. Otherwise, it'll probably never be ready.

---

### Post by Tominator on 2006-01-09
Yes, I checked and the computer in question is a Pentium III. But really, can you tell me what to click to send a file to the floppy drive, because I'm not finding it anywhere.

---

### Post by aysiu on 2006-01-09
What do you mean by "send a file to the floppy drive"?

You have Ubuntu installed, and you want to copy a file (what file?) to a floppy drive (internal? external?)...?

---

### Post by Tominator on 2006-01-09
As per the other gentleman's suggestion, I wish to download a boot disk and then put that on an internal floppy drive disk. I see that a right click would let me burn things to a cdrom/write drive, but not, apparently, to a floppy drive.

---

### Post by Zimmer on 2006-01-09
[QUOTE=Tominator]As per the other gentleman's suggestion, I wish to download a boot disk and then put that on an internal floppy drive disk. I see that a right click would let me burn things to a cdrom/write drive, but not, apparently, to a floppy drive.[/QUOTE]
Go to   Places>Computer  and there will be an icon for your Floppy drive (hey, I have an icon, and I don't even have a drive !!)
right click and mount the volume...you should be able to access it...(but as I don't have a floppy drive, I can't be totally sure ;) )
regards

---

### Post by Tominator on 2006-01-09
I agree that it makes no sense. I am familiar with set up and know how to use boot order. I'm not saying it's so, but it looks to me like I lost the cdrom when I wiped Ubuntu.

---

### Post by Tominator on 2006-01-09
Thanks Zimmer, I have actually been there before, it's just I let the whole "mount" business stymie me. I have been studying the subject and think I may be able to handle it now. It does seem awkward at best and I wish more were done automatically and without needing my input. Oh well, "wishes ain't fishes", Thanks Again!

---

### Post by Zimmer on 2006-01-10
[QUOTE=Tominator]Thanks Zimmer, I have actually been there before, it's just I let the whole "mount" business stymie me. I have been studying the subject and think I may be able to handle it now. It does seem awkward at best and I wish more were done automatically and without needing my input. Oh well, "wishes ain't fishes", Thanks Again![/QUOTE]
I came across this in my travels
[http://www.codecoffee.com/tipsforlinux/articles/035.html](http://www.codecoffee.com/tipsforlinux/articles/035.html)
One of the better explanations for mounting devices...
Sometimes the versatility of Linux can prove to be an enemy for the beginner..
..in the Windows world I 'genuinely ' have an aquaintance who wants me to go round and install a new mouse for him on XP !!  The thing that daunts new Windows computer users is answering all the Wizard questions, then not knowing what has happened if it does not work. At least with Linux you get a fighting chance to back up a text file, change an entry and sort it...or restore the original and start again...backing up and altering the Windows registry always gives me palpitations.... ;)
Regards

---

### Post by L Campbell on 2006-01-10
[QUOTE=Tominator]Yes, I checked and the computer in question is a Pentium III. But really, can you tell me what to click to send a file to the floppy drive, because I'm not finding it anywhere.[/QUOTE]
..........................

I had a problem with my floppy recently and ' Sef ' was good enough to send me this information:-
...............
 There is a bug in Breezy, so often the floppies won't automount. To get them to automount, go to this site:

[http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/](http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/)

1) Download pmount_0.9.6-1~breezy1_i386.deb

2) Install --> sudo dpkg -i pmount_0.9.6-1~breezy1_i386.deb

3) enter password

4) After it finishes installing, your floppy should mount and umount automatically.

I found that bug and fix from this thread: [http://ubuntuforums.org/showthread.php?t=93139&page=2](http://ubuntuforums.org/showthread.php?t=93139&page=2)

.......................................

This worked perfectly for me.

If you need more help, write again, there will always be someone here to try to help you.

---

### Post by Tominator on 2006-09-29
Now this is humorous, I posted this thread in Jan. I have not had to use the floppy drive since, (I did get it mounted back in Jan). I downloaded a file to my desktop, that is the only option I was offered. I intend to use this file to update my Bios. I have spent a couple of hours trying to get this file onto a floppy disk. It is definitely not an intuitive process. I've looked on the forum and in help, I must be looking in the wrong places. I guess I should have made notes, lol. ](*,)

---

### Post by Zimmer on 2006-09-30
Did you ever check your fstab file to see if the device was being mounted at boot? Did you eventually get (do you still have) an icon for it in Places>Computer  ?

if yes, then why not right click on the icon and click the option to mount volume .....

The entry in the fstab file should read something like

/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

(The last 8 months cannot have been too miserable  , you are still using Ubuntu :)  )

---

### Post by Tominator on 2006-10-01
Hey Zimmer, 
The floopy drive is recognized and works fine, It's just that I am trying to find a point and click method to use it. I had an exe. file that was only on my desktop, i.e. not in home or desktop. I was able to drag that into the file browser and at that point the media tab appeared and I did the whole thing point and click. I cannot get a file to the floppy at all if the file is anywhere other than the desktop only. I can get the media tab to appear, but just cannnot figure what the next step is? I'm just playing around you understand, but it looks to me like there are extra steps involved that will have to be eliminated in the future. It is a long way from the simple process that it has been in MS for many years.
Best Regards, Tom 
P.S. I did find this to somewhat helpfull...
[http://dc.ubuntu-us.org/resources/tutorials/lab-tips.php](http://dc.ubuntu-us.org/resources/tutorials/lab-tips.php)

---

### Post by Tominator on 2006-10-01
Lol missed that bit about the last 8 months, no it has gotten better, I have learned to do a lot of research and look for second opinions, and up to date opinions, before i make a move, lol. It has been an interesting hobby. Cya

---

