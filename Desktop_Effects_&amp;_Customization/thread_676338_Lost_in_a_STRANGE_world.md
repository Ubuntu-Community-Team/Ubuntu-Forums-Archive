---
title: "Lost in a STRANGE world"
date: 2008-01-23
forum: Desktop Effects &amp; Customization
---

### Post by FishinMagician on 2008-01-23
Greetings...i am new to Ubuntu and to Linux itself..but i am intrigued by what i have been hearing and seeing about this OS. So downloaded and installed Ubuntu 7.1... and to tell you the truth..its pretty awesome..but i am having problems getting my nvidia 7800gt to work in gdm. i have read everything and tried all kinds of things based on the forums here..but i cannot seem to get it to work properly.Can someone please take me step by step through the whole process...i am getting frustrated to the point i am going to give up..and i really do not like that idea thanks in advance

---

### Post by FishinMagician on 2008-01-23
i got it fixed...thank you now i am smokin....

---

### Post by perixx on 2008-01-23
Hello there...

Look at this binary driver howto for Nvidia cards:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")
This should take you where you want to step-by-step.

I enabling the Nvidia proprietary drivers works with standard methods - via Applications > System > Restricted Driver Manager, I suggest you use this method instead. 

If it still doesn't work, you might need to reboot and maybe also to use 'sudo dpkg-reconfigure -phigh xserver-xorg' at the terminal. Then you need to reboot again (there's actually another method via CLI, but I forgot about it).

I don't know what your exact problem is, so I can't be more specific, sorry. And I also can't help you with any compiz eye-candy - I'm using plain Xfce.

perixx

---

