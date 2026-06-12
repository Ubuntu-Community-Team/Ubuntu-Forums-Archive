---
title: "Error with Computer and Network icons"
date: 2009-06-09
forum: General Help
---

### Post by new2GNU on 2009-06-09
I am running Ubuntu 9.04 - Jaunty, and I have a problem when I click on the Network or Computer icons I get the following error.

"Could not display "computer:///".

Error: DBus error org.freedesktop.DBus.Error.NoReply:
Message did not receive a reply (timeout by message bus)
Please select another viewer and try again.

I have searched around on the some other forums, but I haven't been able to locate an answer that worked, Or even a current post from 2009. At some point I seem to have found a bug or two in launchpad but they were both marked "resolved fix pushed" and there wasn't any useful steps to fix it in the ticket.

If anybody has any ideas I would greatly appreciate it.

Thanks

---

### Post by Soul-Sing on 2009-06-09
```
sudo aptitude reinstall nautilus
```
to solve this error: "Could not display "computer:///"

---

### Post by Soul-Sing on 2009-06-09
the other errors: do you use bluetooth?

---

### Post by new2GNU on 2009-06-09
I'll try reinstalling nautilus when I get home. As for bluetooth, my computer is set to always hidden and I have never paired a device with it.

Out of curiosity, why do you think reinstalling nautilus fs will solve the problem?

---

### Post by new2GNU on 2009-06-10
> **leoquant said:**
> ```
sudo aptitude reinstall nautilus
```
to solve this error: "Could not display "computer:///"

This did not work. I still get the error when I click on computer or network.

---

### Post by sebushi113 on 2009-06-10
Hello, I am new to ubuntu (and linux :) ).

FIrst of all, THANK YOU!!! to everybody for this amazing operating system! [-o<

It is amazing that I installed ubuntu on this old Japan-only Fujitsu laptop, and everything seemed to work great right out of the box!
I really wanna be done with windows by the time windows 7 rc1 expires in March. Ubuntu and Linux ROCKS!!! =D>  
...a very exciting time..


I am trying out ubuntu studio 9.10 karmic daily (the May 30, 2009 build),
and I am having the exact same problem as new2GNU.

At first there was no problem at all. Then when I updated the system using the Update Manager the problem started.
 - I updated the system many times and it was ok. The problem started a few days ago (last week) when I did a system update (so it seems some update caused the problem)

Also, at the exact same time this happened, my floppy drive started clicking every 2 seconds exactly (I believe).
 - it sounds the same as a floppy drive when it tries to access a floppy
 - a floppy is displayed on the little laptop led display

Thank You for your help!

PS
 I also tried
```
sudo aptitude reinstall nautilus
```
but it didn't work for me either.

---

### Post by new2GNU on 2009-06-11
bump. 

This is a really annoying error as it would seem that certain "not supported" USB devices (ie my phone) do not put an icon on the desktop meaning the only way to access them is through the "computer" icon.

Mike

---

### Post by sebushi113 on 2009-06-11
> **new2GNU said:**
> bump. 

This is a really annoying error as it would seem that certain "not supported" USB devices (ie my phone) do not put an icon on the desktop meaning the only way to access them is through the "computer" icon.

Mike

I am not at my computer now and I don't remember exactly, but even though I cannot access the "computer", I can access all my USB drives through the Menu/Places/Removable Drives (or Media?)

---

### Post by new2GNU on 2009-06-12
So this is really irritating. The USB device I'm trying to connect to is my Palm Pre phone. It doesn't display a USB icon on the desktop. As mentioned in the first post I can't access the computer icon. However when I click on System->Administration->USB Startup Disc Creator it recognized that a palm pre is plugged in and references it as an available device. 

If we can't fix the computer problem. Does anybody know how I can access the device by another method.

---

### Post by sebushi113 on 2009-06-12
> **new2GNU said:**
> So this is really irritating. The USB device I'm trying to connect to is my Palm Pre phone. It doesn't display a USB icon on the desktop. As mentioned in the first post I can't access the computer icon. However when I click on System->Administration->USB Startup Disc Creator it recognized that a palm pre is plugged in and references it as an available device. 

If we can't fix the computer problem. Does anybody know how I can access the device by another method.

Hey Mike,

Did you read my reply to your post?
That is how I can access all my removable drives so see if that works for you too. :)

---

### Post by new2GNU on 2009-06-12
> **sebushi113 said:**
> Hey Mike,

Did you read my reply to your post?
That is how I can access all my removable drives so see if that works for you too. :)

Oh yeah I meant to respond to that as well. I don't have a removable media option under places or system->preferences->removable media and devices (that doesn't exist either). 

And /media doesn't have anything in it other than a cdrom

---

### Post by sebushi113 on 2009-06-12
Okay, I'm home now.

On my Ubuntu Studio (Gnome), I have "Removable Media" under Menu>Places, right between "Computer" and "Network"

Menu>Places>Removable Media

I guess if your system doesn't detect your USB device, "Removable Media" doesn't even show up..

BTW... my USB drive is connected all the time. Did you try to connect your phone before you turn on your computer?

---

### Post by sebushi113 on 2009-06-13
Nobody knows what the problem might be?

I reinstalled ubuntu about 4 times now and always the same problem in gnome.

I also installed xubuntu 9.10 alpha 2 yesterday and it worked fine (no error).
However during installation grub install failed and I had to continue the installation without installing grub... funny thing is after the install was finished, grub was there, but it didn't show my Windows 7... so I had to fixmbr and try installing ubuntu again.

Now I installed ubuntu 9.10 alpha 2 and the same problem with the computer error and floppy drive clicking every 2 seconds returned... I'm kinda given up..:-(

Also...maybe useful info..
The other day when I tried to shut down, a black screen came up and this error was displayed everytime the floppy drive clicked every 2 seconds.

[(some numbers)] end_request: I/O error, dev fd0, sector 0

If anyone knows how to fix this or has any ideas please let us know..
Thank you.

---

### Post by Soul-Sing on 2009-06-13
dev fd0 is a floppy drive I believe.
Is it suppost to be active? Do you use it?

---

### Post by sebushi113 on 2009-06-13
There is a floppy drive in this laptop, but I've never used it..

---

### Post by Soul-Sing on 2009-06-13
> The other day when I tried to shut down, a black screen came up and this error was displayed everytime the floppy drive clicked every 2 seconds.

Can you disable that drive via bios settings? I believe its causing you trouble.

Is it on top of all bootoptions?

---

### Post by sebushi113 on 2009-06-13
> **leoquant said:**
> Can you disable that drive via bios settings? I believe its causing you trouble.

I see... ok, I'll see if I can disable it now and see if that helps.

Thank you.

---

### Post by sebushi113 on 2009-06-13
It seems there is no option to disable the floppy drive in bios..

Also, I noticed now on the laptop led display, the CD icon and the Floppy icon are displayed.
The CD icon is flashing every 2 seconds (as if it's trying to be accessed) and the floppy icon just stays displayed the whole time.

Both the floppy and the cd drives are empty (no cd or floppy inside)

Still get the error trying to access "computer" and floppy drive still clicks every 2 secs..

This is just weird....:-s

---

### Post by sebushi113 on 2009-06-13
> **leoquant said:**
> Is it on top of all bootoptions?

Sorry, didn't notice this question..

It was the second in boot options right after CD ROM.

1. CD
2. Floppy
3. Hard Drive

Now I put it last.

1. CD
2. Hard Drive
3. Floppy

Still same problem...

---

### Post by Soul-Sing on 2009-06-13
Sorry I'am out of options....(You can place the hard drive on top, but that will imo not make a difference...)
It seems like a "loop" situation, where your computer searches for your cd rom and floppy drive.....and doesn't stop whith that activity.

---

### Post by sebushi113 on 2009-06-13
> **leoquant said:**
> Sorry I'am out of options....(You can place the hard drive on top, but that will imo not make a difference...)
It seems like a "loop" situation, where your computer searches for your cd rom and floppy drive.....and doesn't stop whith that activity.

Yeah, "loop" sounds like what is happening. Seems ubuntu keeps trying to access my floppy and my cd drives (and the hard drive too maybe since the icon flashes too, but it's hard to tell if the computer is reading or trying to access the hard drive).

Well, thank you very much for all your help leoquant!

If anybody else has any other ideas that might help please let me know.

---

### Post by Foaming Draught on 2009-06-13
I had the exact same problem as sebushi 113.  I could live without "Places/Computer", because navigating up from "Home" brought me to the file system, but the clicking floppy was driving me crazy (even though I'm half deaf  -  Heaven knows what someone with normal hearing would have been going through).  I think it's a gvfs problem which crops up with pretty well alternate upgrades.  Googling +"DBus Error" +ubuntu +computer +places brings up lots of instances, with the common strand that it's not fixed but a particular panjandrum always insists that it is and closes bug reports, only for another hundred bugged users to try to re-open them, and our single panjandrum re-closing them.  There's a loop for you.

ANYWAY!  Taking leoquant's suggestion as a guide, (thank you, leoquant :D  ), I've put the floppy at the bottom of the boot order in BIOS set-up (the usual F2 at boot), removed it altogether from the boot sequence, and turned it 'Off' in 'Drives'.  This has stopped the clicking (stopped anything to do with the useless floppy), brought back "Computer" and "Places/Computer" without the DBus Error, and even shows an unmounted Floppy icon in "Computer" which it never did before.  (Edited to add that the floppy doesn't show in palimpsest any longer).

This is a Dell Optiplex GX280 desktop with Karmic and all updates.

Thank you sebushi 113 for asking the question, and leoquant for solving it (for me, at least).

---

### Post by Soul-Sing on 2009-06-13
Foaming Draught great!:p

---

### Post by sebushi113 on 2009-06-13
> **Foaming Draught said:**
> I had the exact same problem as sebushi 113.  I could live without "Places/Computer", because navigating up from "Home" brought me to the file system, but the clicking floppy was driving me crazy (even though I'm half deaf  -  Heaven knows what someone with normal hearing would have been going through).  I think it's a gvfs problem which crops up with pretty well alternate upgrades.  Googling +"DBus Error" +ubuntu +computer +places brings up lots of instances, with the common strand that it's not fixed but a particular panjandrum always insists that it is and closes bug reports, only for another hundred bugged users to try to re-open them, and our single panjandrum re-closing them.  There's a loop for you.

ANYWAY!  Taking leoquant's suggestion as a guide, (thank you, leoquant :D  ), I've put the floppy at the bottom of the boot order in BIOS set-up (the usual F2 at boot), removed it altogether from the boot sequence, and turned it 'Off' in 'Drives'.  This has stopped the clicking (stopped anything to do with the useless floppy), brought back "Computer" and "Places/Computer" without the DBus Error, and even shows an unmounted Floppy icon in "Computer" which it never did before.  (Edited to add that the floppy doesn't show in palimpsest any longer).

This is a Dell Optiplex GX280 desktop with Karmic and all updates.

Thank you sebushi 113 for asking the question, and leoquant for solving it (for me, at least).

Hey, it's really great to hear you fixed it! (hope I'm next! :o)

Now, you said you turned the floppy off in "Drives"...
How did you do that? Where is "Drives"? I don't see it in my ubuntu... sorry..:|

And Thank You very much for your reply!

---

### Post by Foaming Draught on 2009-06-13
In your BIOS setup (the usual way is to hit F2 during machine power-up  -  after ubuntu starts loading, it's too late, do a restart and try again), there will be a Boot Sequence (for example, you can move CD-ROM, Hard Disk #1, USB stick, floppy, up and down in the Boot order).  On my Dell desktop, there's also an option to remove a floppy (or any other media) from the boot sequence altogether.   It will stay in the list, but without a number against it.

Again in my Dell desktop BIOS setup, your laptop might be different, there is an entry "Drives".  I can disable a drive completely, in my dialogue it can be turned "Off".  That's what I've done with the floppy.  That step might not have been necessary after I removed the floppy from the Boot sequence altogether, but I decided that I would kill any chance of the wretched thing being identified to the system.

Now I wonder what I can put into that floppy bay which is more useful than a floppy?  :)

I meant it when I said "Thank you" to you for asking the question, sebushi113.  If brave people like you didn't ask questions, folk like me wouldn't get the answer.  Good success in putting leoquant's solution into practice.

---

### Post by sebushi113 on 2009-06-14
> **Foaming Draught said:**
> In your BIOS setup (the usual way is to hit F2 during machine power-up  -  after ubuntu starts loading, it's too late, do a restart and try again), there will be a Boot Sequence (for example, you can move CD-ROM, Hard Disk #1, USB stick, floppy, up and down in the Boot order).  On my Dell desktop, there's also an option to remove a floppy (or any other media) from the boot sequence altogether.   It will stay in the list, but without a number against it.

Again in my Dell desktop BIOS setup, your laptop might be different, there is an entry "Drives".  I can disable a drive completely, in my dialogue it can be turned "Off".  That's what I've done with the floppy.  That step might not have been necessary after I removed the floppy from the Boot sequence altogether, but I decided that I would kill any chance of the wretched thing being identified to the system.

Now I wonder what I can put into that floppy bay which is more useful than a floppy?  :)

I meant it when I said "Thank you" to you for asking the question, sebushi113.  If brave people like you didn't ask questions, folk like me wouldn't get the answer.  Good success in putting leoquant's solution into practice.

Ah, I see. You did it in bios... I guess I'm out of luck then since there doesn't seem to be an option to disable drives in my old bios..:(
I was able to put the floppy as the last boot option but that was all I could do.

At the same time, it's not a very good thing that we have to disable a perfectly good working floppy drive to avoid this kind of problem. 

And of course I knew you were being sincere in saying thank you, as was I saying that it's great you were able to fix the same problem I am having. I was really happy, and a little relieved too I guess, that someone with the same problem as me was able to work it out. :)

Well, I guess I'll try installing kubuntu 9.10 as it seemed to have not given me this error when I tried the alpha 1 for a few days. 

I'm just getting tired of burning all those CDs...not too good for the environment.
Seems like burning disto CDs is almost as throwing the CD in the garbage, since you try out so many distros and never really use the CD more than once or twice.

---

### Post by sebushi113 on 2009-06-17
Okay, so I installed the kubuntu 9.10 alpha 2, and it worked fine for a few hours...
Then, the same exact problem started again..
The floppy started clicking (or "ticking" might be a better term?) every 2 seconds.

So, I'm back to the same error and the same question.

Can anyone help? Any ideas? It seems like this is a type of error that happens to many users.

I read an article about the new ubuntu 100 papercuts project at Ars Technica.
[http://arstechnica.com/open-source/news/2009/06/canonical-to-boost-ubuntu-usability-by-tackling-papercuts.ars](http://arstechnica.com/open-source/news/2009/06/canonical-to-boost-ubuntu-usability-by-tackling-papercuts.ars)
Should I report that there? I am new to ubuntu so I don't really have a good idea what would be a good candidate for a "papercut" problem. This is definitely a problem that makes using ubuntu just not possible (constant clicks from the floppy drive, not being able to access the "computer" and certain drives..), but I have no idea if this is easy to fix for the ubuntu guys or not.

Please please help! [-o<
I really wanna get away from windows by the time windows 7 goes on sale, and I'd really love to have a stable enough system to get it on my parents computers back home. Enough of windows.. #-o

Lets get open source out there! Let's make this happen!=D>
Come on all you linux gurus!!! :twisted:

---

