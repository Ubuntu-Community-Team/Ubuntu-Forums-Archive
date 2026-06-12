---
title: "problems with live cd"
date: 2007-05-26
forum: Desktop Environments
---

### Post by mrsempai on 2007-05-26
I'm new to linux and I'm trying to install ubuntu, but the live cd has problems loading... apparently the problem is GNOME...

I'm in  a 4025gz model gateway laptop... PLEASE HELP!

---

### Post by merlinus on 2007-05-26
Did you try safe (graphics) mode at the startup menu?

-merlin

---

### Post by meng on 2007-05-26
Running live CD with only 256 MB RAM may not work. It depends, if you have more RAM then that is probably not the problem although it could be that the CD doesn't recognize your video card. If you have any more details (error messages or more specific observations) then post away.

---

### Post by mrsempai on 2007-05-26
it has 256 RAM,my video card is an intel extreme graphics 2 (dont know much about this laptop since it was a gift and came without manuals)

im going to try the live cd again and see what i can write down

anyways is there a way to instal ubuntu without going in the live cd??

---

### Post by merlinus on 2007-05-26
You will have to download the alternate desktop cd .iso file from ubuntu.com.  It is a text-based installer, rather than GUI.

But it works pretty much the same.

-merlin

---

### Post by mrsempai on 2007-05-26
ook, here are some of the problems that i could write...

----in the black (ms-dos like) screen after the windows based OS loads 

FWH not found 

something about microcode and microcode5.fn

----when windows based OS starts to load (when the ubuntu "sign" appears in the middle of the screen)

There was an error starting the gnome settings Daemon.

some things such as themes, desktops etc may not work properly


then it just freezes


----about the text based installation

as i said erlyer im a noob to linux, so is it gonna be difficult to install? 

i have windows and would like to make a partition in my hard drive for ubuntu until im more experienced, will i have to do use some linux based commands or is it simple?


thanks :)

---

### Post by merlinus on 2007-05-26
I think the graphical problems are due to not enough RAM.  You can try the alternate install cd and see if that works.  Although it is text-based, there are still menus and choices available via your keyboard.

You can always bail out if you feel stuck.  No harm in trying.....

-merlin

---

### Post by ugm6hr on 2007-05-26
Or try Xubuntu LiveCD.

---

### Post by Ameet on 2007-05-28
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/control-center/+bug/61381](https://launchpad.net/ubuntu/+source/control-center/+bug/61381) [br].[/br] ---------------------------- [br].[/br] [br].[/br]                 I have the SAME problem, can't load the Live CD.  I have a:[LIST]
[*]Dell Inspiron 5100 laptop
[*]2.4 GHz Pentium 4
[*]256 MB RAM
[*]Preloaded with Windows XP in a single partition
[*]Mobility Radeon 7500C screen[/LIST]This problem was documented previously at: [http://ubuntuforums.org/showthread.php?t=290822](http://ubuntuforums.org/showthread.php?t=290822)
And at launchpad.net at:
[https://launchpad.net/ubuntu/+source/control-center/+bug/61381](https://launchpad.net/ubuntu/+source/control-center/+bug/61381)
And at debianhelp.org at:
[http://www.debianhelp.org/node/6711](http://www.debianhelp.org/node/6711)

...but here since we have a live CD it is impossible to edit any network settings or to futz with the OS parameters in any way that I know.

Any suggestions?

---

### Post by Ameet on 2007-05-31
My problem was solved, after I swapped out the hard drive, which I suspected of being buggy, with another hard drive.  I was able to load the Live CD for 7.04 and to install the system on the drive without difficulty.

I hope this helps others.  Maybe the error is primarily a hardware issue.

Ameet.

---

