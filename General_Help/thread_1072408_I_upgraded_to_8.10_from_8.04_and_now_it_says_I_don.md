---
title: "I upgraded to 8.10 from 8.04 and now it says I don't have monitors!"
date: 2009-02-17
forum: General Help
---

### Post by vizitorq on 2009-02-17
As the title indicates I upgraded to 8.10. Now when it rebooted it stopped in the terminal and asked me to login. So I did, and it just stayed in the terminal. I typed the command 'startx' and it says "fatal error: no screens found". This, as you might imagine, poses a huge problem! I have an nvidia graphics card with dual monitors. What can I do to fix the monitor issue AND everytime i boot to automatically start the x server

---

### Post by Embiggens on 2009-02-17
It's only stopping in the terminal because there's an issue with the graphics driver.  So I wouldn't worry about that.

Did you try reinstalling the nvidia driver?  I'm still not clear on this, but I think you need to do this everytime you change kernels because it gets compiled into the kernel.

---

### Post by vizitorq on 2009-02-17
I was under the impression ubuntu would restore all the settings that were important to keep the machine working as normal. So how do I install the graphics divers then?

---

### Post by vizitorq on 2009-02-17
The terminal says kinit: no resume image, doing normal boot.

---

### Post by Embiggens on 2009-02-17
Ok it appears you used the "supported" installation the first time, which it seems is a good way to do it.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Unfortunately though this is getting out of my limited expertise.  If I were you I would take a look at the last couple of bullet points in that link and see if there's anything informative there.  Also, if you want to post the content of you /etc/X11/xorg.conf file here that might be helpful, probably for someone other than me.

---

### Post by vizitorq on 2009-02-17
at this point all I want to do is downgrade back to 8.04. How do I do that without losing all my data?

---

### Post by Embiggens on 2009-02-18
Any progress?

I don't know how to downgrade, I think there is a way though.  Just for kicks, can you post /etc/X11/xorg.conf?  In that same /etc/X11 directory, is there another file called xorg.conf.backup or something like that?

---

