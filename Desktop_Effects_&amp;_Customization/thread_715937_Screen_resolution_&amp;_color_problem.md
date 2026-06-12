---
title: "Screen resolution &amp; color problem"
date: 2008-03-05
forum: Desktop Effects &amp; Customization
---

### Post by terrorsathan on 2008-03-05
Hi,

Actually my screen has an resolution of 1280x768 px.
How can I set this resolution as default?

I added "1280x768" to the xorg.conf, but it looks like this won't work.
```
Modes      "1280x768" "1024x768" "800x600" "720x400" "640x480"
```
Is there a ways to force-use the resolution of 1280x768px?

I hope for help, thanks :).

---

### Post by terrorsathan on 2008-03-05
Is there no one, who could help? :(
I've tried now several screen setting in xorg.conf, but none of them works ...
Might it be because my driver is configured wrong?

---

### Post by boeing777 on 2008-03-05
did you turn on the restricted driver for your video card? because it should automatically adjust the resolution for you if you turned it on.

---

### Post by boeing777 on 2008-03-05
Open System-->Administration-->Restricted Drivers Manager and then turn on your video card driver from there

---

### Post by terrorsathan on 2008-03-05
When I try to access System-->Administration-->Restricted Drivers Manager it returns the following message:
```
Your hardware does not need any restricted drivers.
```
Looks like it won't work.

---

### Post by boeing777 on 2008-03-05
I'm not sure about this, i read it somewhere that they are working on a driver for this card. it's not out yet.

---

### Post by terrorsathan on 2008-03-05
So this means that I can't set the desired resolution?
Hmm ... this is really weird.

Anyway, thanks for your help.

---

### Post by boeing777 on 2008-03-05
you know what:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

download Envy from this site

it should work

---

### Post by boeing777 on 2008-03-05
let me know when you try to install the card with Envy

---

### Post by terrorsathan on 2008-03-05
Do I have to choose 'Install the ATI driver'?
Sorry, I'm new to all...

---

### Post by boeing777 on 2008-03-05
yes,

---

### Post by terrorsathan on 2008-03-05
Ok, I installed it now.
At the login panel it looked like the correct resolution was used, but after login the resolution changed again.

Btw thanks for you help until now ...

---

### Post by boeing777 on 2008-03-05
try to go into Administration --> Screens & Graphics and see if you could change it there

---

### Post by terrorsathan on 2008-03-05
Wow, it worked now! The screen looks even more clearer than before.
I just figured out, that the 'Extra Appearance Effects' Work now!
Damn, thanks a LOT man, you did great job :) ... you made my day :)

---

### Post by boeing777 on 2008-03-05
you're welcome. now change this post's topic title  to "solved". thank you

---

### Post by terrorsathan on 2008-03-05
Ok, but why doesn't it show the new title if I change the title of my first post to '[solved] Screen resolution & color problem'?

---

