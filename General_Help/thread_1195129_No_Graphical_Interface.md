---
title: "No Graphical Interface"
date: 2009-06-23
forum: General Help
---

### Post by naharper on 2009-06-23
I'm running Hardy Heron with VirtualBox on my Macbook. VirtualBox crashed recently, and ever since I can't get the graphical interface to show up. I boot up and it gives me the error:

kinit: No resume image, doing normal boot...

I am NOT good enough with a terminal to work solely through it. How can I fix this?

---

### Post by Closed_Port on 2009-06-23
I know this isn't of much help, but the line you posted isn't an error message, though it might look like one.

Does it boot at all, that is, can you log in in the terminal, or doesn't it even get that far?

---

### Post by naharper on 2009-06-23
Yeah, I can log in just fine, it's just all in the Unix terminal.

---

### Post by Closed_Port on 2009-06-23
Can you start the graphical environment from there?
sudo /etc/init.d/gdm start

---

### Post by Polaris96 on 2009-06-23
try starting just x11 by itself.  your x settings might be whacked.

try this:

sudo X --configure

and then follow the output directions to test xserver with the "plain vanilla" config file you just generated.

---

### Post by naharper on 2009-06-23
sudo /etc/init.d/gdm start gives me a red "fail" message when I try it.  

When I tried the second suggestion, sudo X --configure, it told me that --configure is an "Unrecognized Option."

---

### Post by Polaris96 on 2009-06-23
yeah that's weird.  Mine's doing it too, now.  I'll get back to you about the X autoconfigure.  sorry about that.

---

### Post by blueridgedog on 2009-06-23
From the terminal, try:

```
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

---

### Post by Polaris96 on 2009-06-24
OK it was a syntax error.  You can get X to configure itself without going down to the packaging level by typing:

sudo X -configure

(i had originally typed X --configure. sorry.)

Xserver will output directions on how to test the new configuration in a "safe" way b4 you reinstall.  you should get a grey screen with a Mouse karet that can be mouse controlled.  After you get that press ctrl-alt-backspace to shut the X session and copy the new configuration to /etc/x11/x.config (CHECK that you have it in the same place before copying the file)

---

