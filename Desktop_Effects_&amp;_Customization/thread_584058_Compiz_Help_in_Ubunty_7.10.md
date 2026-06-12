---
title: "Compiz Help in Ubunty 7.10?"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by andy- on 2007-10-20
In Live CD and after install the Desktop Effects worked fine. After installing restricted video drivers they disabled themselves. 

Now I get this: [[IMG]http://img264.imageshack.us/img264/663/screenshotzz5.th.png[/IMG]](http://img264.imageshack.us/my.php?image=screenshotzz5.png)

fglrxinfo: 

drew@home:~$ fglrx
fglrxinfo     fglrx_xgamma  
drew@home:~$ fglrx
fglrxinfo     fglrx_xgamma  
drew@home:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON X850 XT
OpenGL version string: 2.0.6473 (8.37.6)

Which is correct, that is the video card I have. Did some digging around, no luck, wonder if anyone has a quick fix for this? Thanks in Advance! Please describe in noob talk if possible, I know computers, but I'm very new to Linux still.

---

### Post by jimerickso on 2007-10-21
i think you need to install xgl. like this:

sudo apt-get install xserver-xgl

hope that helps!

---

### Post by andy- on 2007-10-24
That did it, thanks mate.

---

