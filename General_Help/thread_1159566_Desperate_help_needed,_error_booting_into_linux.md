---
title: "Desperate help needed, error booting into linux"
date: 2009-05-14
forum: General Help
---

### Post by Fernando Hernandez on 2009-05-14
Oh boy...I royally screwed up my linux.

I'm fairly new and i recently switched from gnoem to kde just to try a little something new.  in the process of finding potentially useful software I came across a program called "kleansweep" which...seemed like a good idea at the time...though I can't say the program didn't warn me I might screw things up if I didn't know what I was doing.  But I'm a fool and I did it anyway.  

What happened was after The Cleaning was complete, I got some error messages when I tried to run dolphin, whatever the image viewer default in kde4 is called, and the zip/tar/etc manager.  It was all the same error, and i can't quote it to you verbotim right now, but it had to do with missing mime files.  unfortunately I had some errands to run and decided I'd figure it out when i got home - after all, things were, despite the errors, still running and seeming to function well, and I ran firefox and Amarok without a peep.

But when i got home and decided to reboot, I found I couldn't even get to my desktop and try to tinker with things...on my OS selection screen (oh for the record i have a dell), I choose to boot into kubuntu, and it goes as usual until i get to the first kubuntu loading screen.  then my screen goes black again and the text output is as follows...

.:74: Can't open /etc/default/rcS
error: '/etc/init.d/rc' exited outside the expected code flow.
init: rcS main process (751) terminated with status 2
.:74: Can't open /etc/default/rcS
error: '/etc/init.d/rc' exited outside the expected code flow.
init: rcS main process (751) terminated with status 2

(Yes, it does show that same message twice like that)

I tried a few times and got the same result, and even on the 3 second interval where it says 'press esc for menu' I gave that a shot, but I'm not exactly an expert at running diagnostics outside an OS environment.  I don't know what I'm doing, and I'm scared i've ruined it all.

So my question has a few parts...

-Can I fix this enough to boot into kubuntu and try to replace those mime files I removed (kleansweep did make a backup .tar file of everything before wiping)?
     -If I get this far, how do I replace the files from the backup back to where they belong?  does linux have an equivalent to windows' "system restore"?
-Is there a way to fix this?!
-Do I have to uninstall kubuntu, if so, how do I do this?  I've never removed a partition before without formatting my entire harddrive.
     -If I uninstall and reinstall kubuntu, will I be able to keep my settings or have to completely start over?

I'm sorry for the newbie questions here, but i've royalled messed up, and I'm panicking.  I hope there's a way to undo what I've done.

Any help is appreciated, but please try to keep it in layman's terms, I don't wanna make things worse.

---

### Post by Fernando Hernandez on 2009-05-15
Bump?  Please, I don't know what to do, I've tried everything.

---

### Post by rukiaEnix on 2009-05-15
Well what you can do is try to recover those configuration files that you say they may have been deleted, recover them using a livecd, I don't know if your kubuntu can work as livecd but if it does start with it like livecd...and if it's not live then download a livecd (I recommend you knoppix) and recover the files you think that were backuped by kleansweep, when you have find them then copy them to the folder where this files should be, now start again with your kubuntu and see if the problem is solved if not use again your kubuntu as livecd (or any other livecd you have) and make a backup of all your stuff and yes..format your hardrive -.- but if you end with this option just post it and I will tell you how to do it without formatting the entire disk.

---

### Post by Fernando Hernandez on 2009-05-15
The problem is though that i can't even boot to where my linux is loading up.  so i can't get to where i can try to recover those files yet...I can still boot into Windows on my other partition but when I try to boot into linux it just stops at a black screen that says

.:74: Can't open /etc/default/rcS
error: '/etc/init.d/rc' exited outside the expected code flow.
init: rcS main process (751) terminated with status 2
.:74: Can't open /etc/default/rcS
error: '/etc/init.d/rc' exited outside the expected code flow.
init: rcS main process (751) terminated with status 2

I need to know how/if i can pass this and get linux to boot up first...because it was still functioning before my reboot, just telling me i was missing files...if i can get to my kubuntu i can try to recover those files, but if it's not possible i need to know how to delete the partition so i can start over...and doubtful but if there's a way to keep my files and settings and uninstall/reinstall kubuntu...

---

### Post by Fernando Hernandez on 2009-05-15
i'm starting to feel hopeless...i tried every option in the menu after booting into recovery mode...nothing has solved the problem, i still get .:74: Can't open /etc/default/rcS error: '/etc/init.d/rc' exited outside the expected code flow. init: rcS main process (751) terminated with status 2

Is there anything i can do?

---

### Post by Fernando Hernandez on 2009-05-15
I guess I just need to uninstall it...is there a way I can keep my files and fix this...?

---

### Post by rukiaEnix on 2009-05-15
You can recover your files using a livecd, what a livecd does is to provide you with a "temporal" operative system that you will be mounting from the cd you don't need to install it to your hardrive, that is the reason why I recommend you to start with a livecd so you can make a backup of your files and reinstall kubuntu. I tell you to reinstall kubuntu because what is damage is not a configuration file (I'm sorry I didn't pay attention to the folder where the rcS was) it is a script that runs when the system starts so you will have to reinstall to fix it.
You don't have to format all your hardrive, when you are installing kubuntu when the window that shows you to choose partitioning option (that's not the name but it is a windows where you choose how to partition the hardrive) select the option manually not automatically and then the installation will show you a window where you can manage all your partitions.

---

