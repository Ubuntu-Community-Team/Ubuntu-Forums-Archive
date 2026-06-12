---
title: "Adept - can't install new software"
date: 2006-10-07
forum: Desktop Environments
---

### Post by hodad on 2006-10-07
Just left using Suse Linux because I couldn't get YaST to install new software packages on the PC.  I tried for about a year(!).  Always "unresolved conflicts", and I haven't a clue how to deal with them...

On a friend's suggestion, I just installed Ubuntu, and, well, you guessed it, I can't install software.   The Adept screen looked friendly enough, but just about the time I thought I might be getting close, I get the following message:

"The APT database could not be opened, this may be caused by incorrect configuration...  Try  running apt-setup or apt -get update...", and I'm kicked out of Adept](*,) .  

Needless to say, I tried both commands from the shell, and all I get is "no such command". Now Adept cannot be accessed.  I suppose I could just wipe the hard drive again and reinstall Ubuntu, but I'm tired of doing that (3 times already today).

Is it possible to load new software in Linux, or must you just be satisfied with what is installed automatically when you buy an off the shelf new set of CD's?  

I don't have a lot of time to deal with futzing with computers;I'd go with an Apple if I had the money, but, unfortunately, I don't.  Also, being over 50 is another problem I suppose...

Anyway, sorry to vent, but if anyone can help me out I would be very thankful!

---

### Post by GreenHawkIA on 2006-10-07
It is very possible.  First do you have a working internet connection on Ubuntu?  If so, good...Then, open that shell back up and type in "sudo apt-get update" and "sudo apt-get upgrade" (no quotes), then type in your password when it asks for it.  If those return an error message, please reproduce it here.  Also copy & paste what's in your /etc/apt/sources.list file.  You can get this by typing "sudo gedit /etc/apt/sources.list" and then copying and pasting the contents that pop up here.  This all will help diagnose the problem.

---

### Post by lemonsCC on 2006-10-07
Double Post...

[http://ubuntuforums.org/showthread.php?t=272793]("http://ubuntuforums.org/showthread.php?t=272793")

---

