---
title: "Start up error, I think Ubuntu is dead, Help Please!!!"
date: 2009-06-08
forum: General Help
---

### Post by crimlaw on 2009-06-08
I walked into my office this morning, opened my laptop, which was sitting on my desk, and my Ubuntu never started up from hibernation.  I am running the latest version.  Eventually the password prompt came up and I entered in my password, but I could not click on anything.  So, I forced the laptop to shut down, rebooted, and everything seemed to be working fine.  Then I had some trouble with firefox where I could not get it to open properly.  Instead of restarting, I attempted to close the lid, hibernate the computer, and start it back up.  When I opened the lid after a minute or two, there was a character on the screen, but before I could make out what it was, the computer shut down.  

At this point, I worried that there was something internally wrong, so I booted up in windows and decided to run a disk defrag and a disk cleanup.  I ran windows xp for the remainder of the afternoon, but when I attempted to reboot into Unbuntu, I received the following error:

fsck dies with exit status 4
                               [fail]
* an automatic file system check (fsck) of the root filesystem failed.  the fsck should be performed in maintenance mode with the root system mounted in read-only mode.
* The root filesystem is currently mounted in read-only mode.  A maintenance shell will now be started.  
After performing system maintenance, press CONTROL-D to terminate the maintenance shall and restart the system.
bash:  no job control in this shell
root@ubuntu:~#


Is my Ubuntu dead?  I warn that I am not very knowledgeable when it comes to Ubuntu, so if there is a solution, would you mind taking me through it step-by-step?  

Thanks!!!!!

---

### Post by Chronon on 2009-06-08
So, what was the result of running fsck from the maintenance shell?

---

### Post by crimlaw on 2009-06-08
it never ran one on its own, and I have no idea how to run one.  How do I run one???

---

### Post by crimlaw on 2009-06-08
has anyone else experienced this problem with the undated version?  is there a fix?  are there any commands I can run from the root to see what the problem is?

---

### Post by QIII on 2009-06-08
Not sure if this will work in Jaunty, but this guy seems to have found a solution.

[http://ubuntuforums.org/showthread.php?t=367644](http://ubuntuforums.org/showthread.php?t=367644)

---

### Post by joshh88 on 2009-06-08
I just made a post about this same problem and have not gotten a response yet. I'am using Jaunty; this is my only laptop and only distro I can log into. Thank god I have a live usb to use lol or I'd be screwed. The above may work if you can use the ubuntu terminal, but I'm stuck in Slitaz(not that I'm complaining if I wouldn't lose all my info if I just went anew with Slitaz) and those commands won't work :(

---

### Post by crimlaw on 2009-06-08
I will give the solution a try in the next few days.  I do not have a live cd because I am running on a netbook.  I used the jumpdrive install for 8.10 and upgraded when it asked me if I wanted to.  If I make a new jumpdrive for 8.10 do you think I will be able to follow the live cd option posted above?  

Is this a common problem?  Now that I am hooked on the features of ubuntu/compiz I really hate windows.  I have always thought ubuntu was the most stable/user friendly for those of us new to linux.

Should I just reinstall 8.10?

Thanks

---

### Post by QIII on 2009-06-08
I doubt it's common, but clearly it happens!

I'm not sure about the jump drive.  Can your netbook boot from a usb device?  (I'm thinking it can...)

I'd say it was worth a try.

Let us know if that works, and we'll all have a solution the next time this comes up for someone else.

---

### Post by joshh88 on 2009-06-08
:( fsck doesn't work in slitaz i just tried. i tried using gparted to use its fix feature; its simply says an error has occured and has not given any details.

---

### Post by crimlaw on 2009-06-08
seems like the last time I attempted to boot from a usb on my netbook it would not recognize the usb on startup.  so, I don't think my netbook (HP mini 1000) will do it.  

Last time I installed, I used a usb for a wubi install.

---

### Post by joshh88 on 2009-06-08
you couldn't get into the boot screen with F12? or control

---

### Post by crimlaw on 2009-06-08
no, it was weird, I tried everything.  Maybe I will try again.  I just remember that it would not recognize the usb plugged in on start up.

---

### Post by crimlaw on 2009-06-09
well, I attempted to boot from a usb this morning, and I could not.  How do I run the fsck scan from the root@ubuntu when I am prompted with it on start up?

---

### Post by joshh88 on 2009-06-09
When you get the error message type out Control-D be sure that you capitalize the c and d it is case sensitive. It will ask for root password. the give you regular terminal. type in sudo fsck then enter and will ask for password again.

---

### Post by crimlaw on 2009-06-09
PROBLEM SOLVED (so far anyway)

Ok, here is what I did.  After the explanation from Josh, I attempted to reboot into Ubuntu.  When I was made aware of the error and given the option to enter a command next to root@ubuntu: I entered sudo fsck. I tried starting with Control-D, but that did nothing.  So, I skipped right to sudo fsck.  The scan began and I just answered yes to all questions.  The scan finished, I rebooted, and Ubuntu started up with no apparent problems.  

I hope this helps others in the future.  Thanks to everyone who helped, especially Josh for telling me how to do what finally worked.

---

### Post by joshh88 on 2009-06-09
How long did you end up holding down Y? I didn't get past like 20min. O and I'm glad it worked out for you but i would still keep tabs because mine comes and goes.

---

### Post by joshh88 on 2009-06-09
Nevermind now ubuntu is gone...... so now I have to reinstall any help was a bit too late for me. This was not a planned loss either all information was lost.

---

### Post by crimlaw on 2009-06-09
Josh, sorry I did not get back to you earlier . . . at the gym.

I did not hold down "y."  I wait until I was prompted to push "y" and then pushed it.  Once I pushed y, it would run some check, then ask if I wanted to do something (I never understood what it wanted me to do), and I would hit y again.  

Luckily, I do not do too much on my laptop that requires me to save on the harddrive.  I just use a jump drive just in case it crashes.  

Sorry you lost everything.

---

### Post by joshh88 on 2009-06-10
No its not you I ran the fsck and it did nothing, but when I rebooted I booted into the usb and the partition for ubuntu was blank. The only only thing that made me mad was that I had alot of pictures stored that are poof gone. I havent found a backup programe to use yet so I had better start looking. See I had it all on a jump drive but I had to dump it to try out a new distro lol.

---

