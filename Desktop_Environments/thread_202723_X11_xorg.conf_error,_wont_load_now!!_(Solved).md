---
title: "X11 xorg.conf error, wont load now!! (Solved)"
date: 2006-06-23
forum: Desktop Environments
---

### Post by blacknyx on 2006-06-23
argh!!

I was so stupid!  Ubuntu was working wonderfully for me minus the fact that I couldn't use my forward and back buttons in firefox.
I had nvidia installed perfectly and everything..

oh why must I mess with something that was 99% perfect
*smacks myself*

Okay sorry  lol  

Anyhow I had my xorg.conf really good and then I used 
[http://ubuntuforums.org/showthread.php?t=28374&highlight=PS2+mouse]("http://ubuntuforums.org/showthread.php?t=28374&highlight=PS2+mouse")
That tutorial.  changing my xorg.conf
Oh and I was using a PS2 mouse so I just named it "mouse"  not "mouse.usb".  

Eerrr well then when I rebooted my computer.  X wouldnn't start up.  Now I'm on my laptop ready to pull my hair out.


**What's the command to have the system automatically try to reconfigure X for you?   xorg --configure  didn't work.  I can't remember it!! **

Sorry I sound crazy.. I'm frustrated with myself.

---

### Post by aysiu on 2006-06-23
You backed up your xorg.conf file before changing it, though, right?

If not, I believe the command you're looking for is ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by johnc4510 on 2006-06-23
sudo dpkg -reconfigure xserver-xorg

---

### Post by blacknyx on 2006-06-23
Thank you thank you!  That's what I needed.  Still getting used to switching from Gentoo to Ubuntu.   I still wish I could get my 5 buttons to work but I think now that I've got it working in general again I'll leave it alone.
Thanks both of you for helping me out.

---

### Post by Franscartoons on 2006-11-04
Had the same problem, thanks for the code!
:mrgreen:

---

