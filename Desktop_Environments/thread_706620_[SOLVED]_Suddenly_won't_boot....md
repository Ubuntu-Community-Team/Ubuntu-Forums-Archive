---
title: "[SOLVED] Suddenly won't boot..."
date: 2008-02-24
forum: Desktop Environments
---

### Post by MikeyXX on 2008-02-24
So I have 7.10.

Been running it fine (more or less) over a few months. Suddenly today, I am showing pictures to some family and when I would click something it wouldn't open etc. So I tried to shut down and it wouldn't let me (does that every once in a while). I did a cntrl-alt-backspace, which normally lets it finish shutting down and it gave an error in text on the screen I hadn't received before and sat there. So I hard shut it down and tried to boot up. It boots up and only gets a couple seconds into the boot when my numlock light an d caplock lights blink. So I booted and got rid of the "quiet" and "splash" in my grub line and I see it freezing on this:

Kernel panic - not syncing: Attempting to kil init!

Before that it said it cannot open /root/dev/console

and a bit above that it mentions that there is "No resume image, doing normal boot"



I can boot up on my live cd (what I'm using now) and I can get at my files to backup my documents etc, but it doesn't seem to be able to see or act on the boot drive (I'm guessing).

If this was windows, I'd run an fdisk /mbr to reset the master boot record. I don't know why this is unhappy. Suggestions? I'd rather not having to reinstall as I customized this to my liking and actually got it to work (other identical installations seem to have one thing or other not work).

Can you direct me? I'll respond with anyting I can offer. I'm not overly knowledgeable so if you want results of  a command, you'll have to give me the complete string to enter.


Michael

---

### Post by MikeyXX on 2008-02-25
Well, I solved it.

Turns out that at some point I had hibernated my windows disk. Then put in my Ubuntu and booted up successfully. Don't know why, but after a hard unfriendly shutdown in that Ubuntu, the computer got stuck thinking it was rebooting from Hibernation.

So Ubuntu kept locking as it couldn't find the image then all heck broke loose. Even after reinstalling, the reboot (after you eject the LiveCD) locked. Same place, same error. 

So I put the Windows drive back in, booted up, hibernated. Then came back from hibernation and shut down properly. 

Then put in the Ubuntu hd and it booted just fine.


Wierd huh? Didn't know the computer knew the difference.

---

