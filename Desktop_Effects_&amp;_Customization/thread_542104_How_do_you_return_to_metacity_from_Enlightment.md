---
title: "How do you return to metacity from Enlightment"
date: 2007-09-03
forum: Desktop Effects &amp; Customization
---

### Post by DGentry on 2007-09-03
I set up Enlightenment windows manager on my box, Now I'd like to return to metacity. Only problem is, I don't know how to switch back without just re-installing the system which sounds rather drastic.

Any ideas?

---

### Post by Phurious on 2007-09-03
I switch back and forth between Compiz and Metacity.  To return to Metacity I use ALT + F2 and enter:
```
metacity --replace
```

I am only guessing, but hope it works for you.

---

### Post by DGentry on 2007-09-03
I was able to launch a term window but when I did the command of metacity --replace. I recieved the following

Doug@doug-Linux:~$Metacity --replace
Window manager warning: "" found in configuration database is not a valid value for keybinding "Toggle_shaded"
bash: Window: command not found


HMmm, not looking good.. BAWwwwwwwwwwwwwwww!

---

### Post by Phurious on 2007-09-03
Did you use a lower case "m"?  Your output shows an uppercase "M".

---

### Post by DGentry on 2007-09-03
My bad, I did do it with a lower case m... I just have to type this instead of copy and past. I can't seem to figure out how to copy something in Enlightenment.

---

### Post by DGentry on 2007-09-03
I still get the same thing 

Doug@doug-Linux:~$metacity --replace
Window manager warning: "" found in configuration database is not a valid value for keybinding "Toggle_shaded"
bash: Window: command not found

---

