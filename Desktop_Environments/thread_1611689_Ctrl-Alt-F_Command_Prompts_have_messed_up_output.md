---
title: "Ctrl-Alt-F Command Prompts have messed up output"
date: 2010-11-02
forum: Desktop Environments
---

### Post by Scarcer on 2010-11-02
Not sure exactly how to explain it. My command prompt screens are appearing messed up.

the resolution appears to have squeezed the command prompt vertically to just a few pixes at the top of the screen. The command prompt appears to also repeat several times horizontally. This is also the case with boot-up.

I'm still in the experimental phases of learning how linux works, messing with GDM, and installing/installing some boot screen tweaks here and there to see what would happen.

I can't quite remember exactly WHAT I did.

Any tips on how I can troubleshoot and supply more information is welcome.

---

### Post by Ryan Dwyer on 2010-11-02
Can you provide a screenshot?

---

### Post by Scarcer on 2010-11-02
Not sure how to take a screenshot of a command screen, w/e the term is.

I'll see if I can figure out how.

---

### Post by Scarcer on 2010-11-02
[http://i921.photobucket.com/albums/ad55/Quadjunky/IMAG0103.jpg](http://i921.photobucket.com/albums/ad55/Quadjunky/IMAG0103.jpg)

---

### Post by Ryan Dwyer on 2010-11-02
The Control + Alt + Function screens are called TTYs. That will make it easier for you to search for the answer.

I did a search and found the following which may help: [http://ubuntuforums.org/showthread.php?t=122936](http://ubuntuforums.org/showthread.php?t=122936)

Were you playing around with your kernel boot line or any config files when this happened?

---

### Post by Scarcer on 2010-11-02
I installed readaheadfedora to check it out and see if it would make the sytem boot faster. I removed it because the text it was displaying wasn't really compatible with Ubuntus boot screen, so it didn't look very good.

I also modified grub's settings and enlarged the resolution to make it look better. But I'm assuming that would only be isolated to grub, and not Ubuntu.

Might be other possibilities I'm not remembering

---

### Post by Scarcer on 2010-11-02
Tried from the link you suggested, doesn't appear to be the issue.

---

