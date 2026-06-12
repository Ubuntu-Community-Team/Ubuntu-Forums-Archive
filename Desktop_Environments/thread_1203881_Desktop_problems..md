---
title: "Desktop problems."
date: 2009-07-03
forum: Desktop Environments
---

### Post by Anarcyn on 2009-07-03
My desktop has shrunk on me and now i cant set it out of 800 x 600. this wouldn't be a problem except that the rest of my desktop is set to a higher resolution and now i cant use many programs because the X's aren't seen on the screen at all.

Please help me out.

---

### Post by synapsys on 2009-07-03
What do you mean the desktop has shrunk on you? What x's? Do you have a screenshot?

---

### Post by Anarcyn on 2009-07-03
ok im REALLY new at this and dont know how to post screen shoots in Ubuntu but i can try to explain better. my screen resolution is at 800 x 600 BUT my ACTUAL resolution is set 1280 x 780 and the screen only shows the top left quarter of my whole desktop.

---

### Post by snakeman21 on 2009-07-03
So just to clarify:  You're saying it's as if your screen is "zoomed in" on the upper left section of the screen, and you can't see anything else?

---

### Post by Anarcyn on 2009-07-03
yes thats what i mean. a little bit more that i just remembered is that i was having some network trouble a while ago and one of the deamons starting acting up and that is what started this whole thing.

---

### Post by synapsys on 2009-07-03
Open a terminal: Applications >> Accessories >> Terminal
and type:

```
sudo dpkg-reconfigure xserver-xorg
```If you can't get to the terminal because of the resolution, press CTRL+ALT+F1 to drop to terminal. Enter above command here. Then hit ALT+F7 to bring back desktop or CTRL+ALT+DEL to restart.

P.S. To get a screenshot in Ubuntu simply press 'print screen' key

---

### Post by Anarcyn on 2009-07-04
Thank you for your help my desktop is finally back to the way is was.

Thanks again

---

### Post by synapsys on 2009-07-04
No problem....

Remember that one... it's gotten me out of a couple jams...

---

