---
title: "[SOLVED] SOS - Disaster Recovery Required"
date: 2008-06-12
forum: Desktop Environments
---

### Post by Felicity_X on 2008-06-12
Help!!!

I was running a Ubuntu 50.4 live cd from my cd rom on my Intel 86 desktop, which does not at present have an installed operating system.

I got connected to Firefox and was surfing the internet doing a great deal of toing and froing in a social website when everything froze.  I had placed the cursor into a text box on the website and attempted to type into it.  It started to do its "I'm working", ring a ring a roses dance and stuck.  No amount of typing produced any text in the box.  I could still move the cursor, and pressing the exit button at the top of the screen seemed to resolve the problem except that everything was jammed, except for the cursor.

I eventually managed to get back to the Ubuntu screen by clicking the cancel button on the screen, but no screen buttons on the Ubuntyu screen would work at all, including the system button, which meant I could not log out.  So I pressed the power on button on the box in desperation.  The Ubuntu screen disappeared and I got the DOS message:-

"Power button pressed
The system is going down for system halt now"

The box will not actually power off, which means that I cannot insert the cd and power on the system to reload the system from the CD.  Presumeably, as I have not, and cannot now log off the system, it is sculling around in the works somewhere, but I do not know how to access it.

I can remove and reinsert the disc into the cd drive, but it does not start to run when inserted.

I have not tried switching off at the mains.  If I do that, will it clear, or will I come back to the same screen I just left.

What to do??

In desperation!!!:confused:

---

### Post by Felicity_X on 2008-06-21
No need to reply, anyone.  I used the blunt instrument of pulling the power plug.  Not to be advised, I suppose.  It did work, however, with no aparent damage!

---

### Post by starscalling on 2008-06-21
felicity these things should be tried in this order in the future:


1. control+alt+backspace
that trys to kill the X-window and restart the gui

2. control+alt+f1
this gets you to a console - when there 
sudo /etc/init.d/gdm restart
if that doesnt work tell it to stop then start

3. control+alt+delete
this is also known as a 'graceful reboot'

if none of these things work, then:

4. hold power button for several seconds
typically they are able to send some sort of mssg to OS and its not a graceful reboot - but its not as bad as just yanking it, which is of course the last resort.


the reason we try not to do so is that linux filesystems sometimes lose data when this is done, or files get corrupted. but alas, sometimes it is the only thing we can do. :popcorn:

---

### Post by Felicity_X on 2008-06-21
You are so right.  I think various central parts of the system are not working as they should, and it has just instructed me to reinstall!

---

