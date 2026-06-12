---
title: "ZSNES in software center - no &quot;install&quot; button - ?"
date: 2014-11-28
forum: Emulators
---

### Post by michael-piziak on 2014-11-28
ZSNES appears in the software center - but no "install" button - ?  
Get More Info button also takes me to a dead link.

Is there a terminal code line(s) I can use to install this - please.

p.s. Perhaps ZSNES is being worked on - is that a possible explanation why the install button doesn't work currently ?

---

### Post by ibjsb4 on 2014-11-29
I do not use this package, but you should be able to install it.  Try this in terminal:
```
sudo apt-get update && sudo apt-get install zsnes:i386
```
[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---

### Post by Bucky Ball on 2014-11-29
I am using 14.04 mini install with xfce4 and Synaptic Package Manager. When I click the box next to zsnes:i386 I have the 'Mark for installation' option, no issue.

Perhaps try installing it from a terminal, as suggested by ibjsb4, and see if that throws any errors.

---

### Post by michael-piziak on 2014-11-29
I used his terminal line and it is running.  I'm testing it to see how long it runs, as some have reported it locks up after X minutes of play.
One thing about this version, is that if you don't input the diagnol directions for the gamepad, it works.  If you do insert them, it messes up the controller during game play.

Marking this thread as solved.

p.s. Please tell me the terminal code line to uninstall this, just in case it doesn't work out - as software center doesn't give me an uninstall option even at this point.

---

### Post by ibjsb4 on 2014-11-29
> p.s. Please tell me the terminal code line to uninstall this, just in  case it doesn't work out - as software center doesn't give me an  uninstall option even at this point. 						
[https://help.ubuntu.com/community/AptGet/Howto#Removal_commands](https://help.ubuntu.com/community/AptGet/Howto#Removal_commands)

---

### Post by Bucky Ball on 2014-11-29
```
sudo apt-get remove zsnes:i386
```

... should do it. ;)

---

### Post by michael-piziak on 2014-12-09
Update:  ZSNES still appears if one searches for it in the software center; however, there is no "install" button to the right as there should be.

I'm running Ubuntu 12.04 lts 64 bit.

---

### Post by Bucky Ball on 2014-12-12
Odd.

---

