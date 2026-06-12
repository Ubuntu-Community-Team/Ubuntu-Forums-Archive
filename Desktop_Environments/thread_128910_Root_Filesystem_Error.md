---
title: "Root Filesystem Error"
date: 2006-02-12
forum: Desktop Environments
---

### Post by Connollyir on 2006-02-12
I went to boot my laptop today after using it all last night and I'm now getting a root filesystem error straight out of the blue. I haven't installed anything in days and now its saying: 

Checking the root file system...
/ containst a file system with errors, check forced.

*fsck failed. PLease repair manually and reboot. Please not that the root *filesystem is currently mounted read-only. To remount it as read-write:

*   # mount -n -o remount,rw /

* CONTROL-D will exit from this shell and REBOOT the system.

bash: lesspipe: command not found
bash: dircolors: command not found
root@(none):~#


What is up with that? I shut it down and restarted it and now I am getting this error. What do I do about it?

Help would be really appreciated.... I have a paper due tuesday that is on this thing and I need to know wether I should start writing A LOT or if its salvageable.

Thanks

-Ian

---

### Post by zxee on 2006-02-12
Have you tried to use the install cd in rescue mode? You could also use a live cd and run fsck on the partition that your ubuntu is installed to. Hope that helps.

---

### Post by angkor on 2006-02-12
Try to fix it manually like it says:

e2fsck /dev/hda2  (change hda2 if your root partition is different)

Had the same problem once, after typing 'y' (it asks "fix manually?" or something) a zillion times the errors on the partition were repaired.

---

### Post by Connollyir on 2006-02-12
[QUOTE=angkor]Try to fix it manually like it says:

e2fsck /dev/hda2  (change hda2 if your root partition is different)

Had the same problem once, after typing 'y' (it asks "fix manually?" or something) a zillion times the errors on the partition were repaired.[/QUOTE]

Well I ran e2fsck on /dev/hda1 which was my boot partition and I think it broke a lot of stuff. After doing this I could no longer mount/unmount drives or volumes, I couldn't access man pages and then when I went to reboot it wouldn't accept telinit as a command. BIG ouch. The Install wasn't that old so I think I might just redo it.... I kinda wanted to use the Kubuntu factory disk anyway. Is there any way I could repair it now? 

And what do you mean use the Live cd in repair mode.... I didn't see anything like that in the special uses (F2-F7 or F8 ).

If I can't repair it can I get my files off it using the live cd and how would I do this? 

Thanks

-Ian

---

### Post by jbraum on 2006-02-12
[QUOTE=zxee]Have you tried to use the install cd in rescue mode? You could also use a live cd and run fsck on the partition that your ubuntu is installed to. Hope that helps.[/QUOTE]

Has anyone done this with success?  I have the same problem.  I wonder if the manual fix it tells will work and how long did the process take.

---

### Post by VCSkier on 2006-02-12
lol, i too am having the same problem...  seems like its contagious!

[my thread]("http://ubuntuforums.org/showthread.php?t=128674")

my problem is that i can't figure out how to remount my root file system read-write.  i couldn't get the provided line to do anything.```
# mount -n -o remount,rw /
```

---

### Post by cwaldbieser on 2006-02-12
[QUOTE=Connollyir]Well I ran e2fsck on /dev/hda1 which was my boot partition and I think it broke a lot of stuff. After doing this I could no longer mount/unmount drives or volumes, I couldn't access man pages and then when I went to reboot it wouldn't accept telinit as a command. BIG ouch. The Install wasn't that old so I think I might just redo it.... I kinda wanted to use the Kubuntu factory disk anyway. Is there any way I could repair it now? 

And what do you mean use the Live cd in repair mode.... I didn't see anything like that in the special uses (F2-F7 or F8 ).

If I can't repair it can I get my files off it using the live cd and how would I do this? 

Thanks

-Ian[/QUOTE]

Sometimes, you can use a LiveCD (Ubuntu, Knoppix, etc.) to recover data.  What you do is boot up under the LiveCD and then mount the hard drive partition that is acting flaky read-only.  You then attempt to copy files off the flaky drive to some other storage.

Also, when running fsck on a drive to try to repair it, you generally don't want to have that drive mounted, and you want to be in single-user (recovery) mode.  This ensures that the various services and programs running in the background don't try to do anything to the drive while fsck is attempting to repair it.  Booting from a LiveCD is one of the best ways to repair a root partition, because otherwise, you would need to have your root partition mounted.

---

### Post by VCSkier on 2006-02-13
thanks cwaldbwiser, you were right.  i booted from a live cd, and ran e2fsck /dev/hda1 in the terminal, hit "y" everytime it found an error, and then rebooted, this time w/o the live cd.  it worked fine.  thanks so much

---

### Post by Connollyir on 2006-02-13
[QUOTE=cwaldbieser]Sometimes, you can use a LiveCD (Ubuntu, Knoppix, etc.) to recover data.  What you do is boot up under the LiveCD and then mount the hard drive partition that is acting flaky read-only.  You then attempt to copy files off the flaky drive to some other storage.

Also, when running fsck on a drive to try to repair it, you generally don't want to have that drive mounted, and you want to be in single-user (recovery) mode.  This ensures that the various services and programs running in the background don't try to do anything to the drive while fsck is attempting to repair it.  Booting from a LiveCD is one of the best ways to repair a root partition, because otherwise, you would need to have your root partition mounted.[/QUOTE]

How would I go about copying files off the hard disk? I only need a select few, small enough I could email them to myself, but I don't know how I would access the hard drive though the live disk and copy stuff off of it?
What commands would I use to do it?

I figured I could just mount the partition and be able do view the contents... but I was wrong. I can't mount it even though I can see it in disk manager. The device is /dev/hda1 but its status is inaccessable and I can't enable it or mount it.

Any help?

-Ian

---

### Post by VCSkier on 2006-04-29
[QUOTE=VCSkier]thanks cwaldbwiser, you were right.  i booted from a live cd, and ran e2fsck /dev/hda1 in the terminal, hit "y" everytime it found an error, and then rebooted, this time w/o the live cd.  it worked fine.  thanks so much[/QUOTE]
does anyone know of a way to accomplish this (reparing root file system inconsistencies) without booting from the live cd?

btw, [here]("http://ubuntuforums.org/showpost.php?p=725430&postcount=1") is the original post where i originally explained my problem in detail.  it has happened a handful of times since i originally posted, and i'm kinda getting tired of booting to a live cd everytime...  thanks

---

### Post by VCSkier on 2006-05-04
bump.  does anyone have any ideas?

---

