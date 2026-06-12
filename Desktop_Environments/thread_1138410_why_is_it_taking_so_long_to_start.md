---
title: "why is it taking so long to start?"
date: 2009-04-26
forum: Desktop Environments
---

### Post by abrax on 2009-04-26
Hello

I have a little problem and i don't know how to solve it, even tough i have read a lot of information in this forum.

I upgraded from 8.10 to 9.04 and the boot time is sometimes taking a lot of time and sometimes is very fast. I don't know if this is a bug or something like that. Also, when the GDM login window starts, I put my username and password and it can take up to ~2 min. in making the desktop entirely usable. Sometimes when I login, it switches to the terminal and 2 or 3 seconds later gdm login window starts again as if i had not logged in, so i have to do it again and then happens what I've said before.

Maybe this other thing is related to that time problem i have:
Since upgrade to Jaunty, EVERY TIME I run a command with sudo or open an application that requires root privileges, it takes a long time to do the command, or open the window, as if it is checking if my password is correct (my pwd is 3 letters long, so i don't think there is a lot of checking to do :lolflag: adding that i dont have many passwords stored)

i think this is a mixed issue between gnome and the console or something like that...

anyone wants to help :P

---

### Post by abrax on 2009-04-28
why no one ever answers any of my questions?

---

### Post by ngsupb on 2009-04-28
It appears there is no solution for this yet:( 

I couldn't determine the problem.
It boots very fast, but take takes some time to login for me too.

I don't have the problem with sudo though.

---

### Post by abrax on 2009-04-28
thanks, well, let's just wait for a solution then :)

---

### Post by andrea000 on 2009-04-28
not a solution but a suggestion maybe stop some programs from 
auto loading on start up (not that there is a lot of them) but
that may speed up your start up some but it's just a thought.

---

### Post by abrax on 2009-04-28
> **andrea000 said:**
> not a solution but a suggestion maybe stop some programs from 
auto loading on start up (not that there is a lot of them) but
that may speed up your start up some but it's just a thought.

thanks andrea000 i also tried that  but nothing happened, now i think its the password thing i mentioned because, as i said before, everytime i sudo something or put my pwd for any administrative task it takes a lot of time to authorize it.

---

### Post by tkoco on 2009-04-29
Several conditions can cause the startup which you are describing. Most of them involve resource starvation - not enough RAM memory, slow harddrive, just to name a couple of them.

Here is a systematic approach to help fix slow response desktops:

1) goto System -> Administration -> Services and disable unnecessary Services. Suggested ones to disable: atd and bluetooth.

2) goto System -> Preferences -> Sessions and disable unnecessary programs. Suggested programs to disable: Bluetooth Manager and Remote Desktop.

(If you do either step 1 or 2, reboot the machine and try your desktop)

3) Open a terminal window and type in 'free'. If you see a number other than zero listed in the "Swap" row under the "used" column, your system is using a portion of the hard drive as 'memory'. While doing this method allows more flexibility, the cost is the time lost while accessing the hard drive. The best cure for this condition is to add more RAM memory to the motherboard provided the motherboard can support the extra RAM.

4) The size of the screen display, in terms of pixels, affects the response of the desktop. Two possible solutions: 1) downsize the screen from a larger matrix to a smaller one (i.e. go from 1280x1024 to 1024x768 ) or 2) upgrade the video card to a faster, more recent model. In the case of video which is built into a motherboard, install a video card and disable the 'on-board' video in the BIOS.

Good luck!
 
> **abrax said:**
> Hello

I have a little problem and i don't know how to solve it, even tough i have read a lot of information in this forum.

I upgraded from 8.10 to 9.04 and the boot time is sometimes taking a lot of time and sometimes is very fast. I don't know if this is a bug or something like that. Also, when the GDM login window starts, I put my username and password and it can take up to ~2 min. in making the desktop entirely usable. Sometimes when I login, it switches to the terminal and 2 or 3 seconds later gdm login window starts again as if i had not logged in, so i have to do it again and then happens what I've said before.

Maybe this other thing is related to that time problem i have:
Since upgrade to Jaunty, EVERY TIME I run a command with sudo or open an application that requires root privileges, it takes a long time to do the command, or open the window, as if it is checking if my password is correct (my pwd is 3 letters long, so i don't think there is a lot of checking to do :lolflag: adding that i dont have many passwords stored)

i think this is a mixed issue between gnome and the console or something like that...

anyone wants to help :P

---

### Post by nyarlathotep77 on 2009-05-17
No worries abrax, you're not the only one to have problems with sudo.
There is also another thread about this at [[COLOR="Blue"]http://ubuntuforums.org/showthread.php?p=7297391[/COLOR]]("http://ubuntuforums.org/showthread.php?p=7297391")

---

### Post by abrax on 2009-05-18
thanks, tkoco, i'll try that.
thank you, too, nyarlathotep77, let me read that.

---

