---
title: "I have a problem plz HELP!!!!"
date: 2009-03-06
forum: General Help
---

### Post by NathanDS101 on 2009-03-06
Hi im having a problem ubuntu loads properly then i put my username and password correclty then it only shows a brown background and a small mouse i can move the mouse. I wait for 10 minutes and it wont go further can someone help me please i downloaded it from the ubuntu site and from a cd, SOLUTION PLZ !!! using a windows xp

---

### Post by UbuntuNerd on 2009-03-06
see if you can hit (Ctrl+Alt+f1) it should take to the command prompt, hit Alt+f7 to get back to the desktop

---

### Post by NathanDS101 on 2009-03-06
> **UbuntuNerd said:**
> see if you can hit (Ctrl+Alt+f1) it should take to the command prompt, hit Alt+f7 to get back to the desktop
ok then what?

---

### Post by UbuntuNerd on 2009-03-06
first copy this code to a piece of paper.now go back to the command prompt. next enter the first line follow by enter then the second line follow by enter then the third and enter. hit (alt f7) to get back to your desktop.
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```
hope that helps

---

### Post by NathanDS101 on 2009-03-06
This is all i need to do then it will work?!?!!?:D:D

---

### Post by entr3p on 2009-03-06
> **NathanDS101 said:**
> This is all i need to do then it will work?!?!!?:D:D

Maybe. You will have to try it out and report back.

---

### Post by NathanDS101 on 2009-03-06
Alright gunna try it right know!

---

### Post by UbuntuNerd on 2009-03-06
it should work you can also try reinstalling your desktop at the prompt type this:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by NathanDS101 on 2009-03-07
i dont get it i got the code but now it goes to something ubuntu/disk/root does not exsist or something and something to shell?? never happend before i boot it it shows the ubuntu loading thing and in like 2 seconds it goes to the thing i told you above

---

### Post by UbuntuNerd on 2009-03-07
if you can still go back to the command prompt try reinstalling your desktop with the code I gave you above, you may have to enter your login information first.

---

