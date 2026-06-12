---
title: "nVidia 8600GT Ubuntu working driver wanted!"
date: 2007-08-08
forum: Desktop Effects &amp; Customization
---

### Post by YaroMan on 2007-08-08
HI every one Looking for working driver that will work with my  nVidia 8600GT... if some one can compile a deb file would be great i try to follow this tutorial [http://www.ubuntuparatodos.org/?q=node/169](http://www.ubuntuparatodos.org/?q=node/169) 
and I got it working but when I reboot a system it does not work any more... and I have to do all over again... and it is keeps happing until each reboot.

---

### Post by six on 2007-08-08
[http://ubuntuforums.org/showthread.php?t=514161](http://ubuntuforums.org/showthread.php?t=514161)

---

### Post by Obor on 2007-08-08
This is how i got it to work
[http://www.robdian.co.uk/content/view/56/](http://www.robdian.co.uk/content/view/56/)

The reason why it doesn't work after reboot is most probably either because you don't apply changes to fstab while you are in nvidia-xconfig or you don't run it as root (you need to start it with "sudo nvidia-xconfig")

---

### Post by z0mbie on 2007-08-08
> **Obor said:**
> This is how i got it to work
[http://www.robdian.co.uk/content/view/56/](http://www.robdian.co.uk/content/view/56/)

The reason why it doesn't work after reboot is most probably either because you don't apply changes to fstab while you are in nvidia-xconfig or you don't run it as root (you need to start it with "sudo nvidia-xconfig")

This is a fantastic tutorial. Worked for me right off the bat.

---

### Post by Obor on 2007-08-08
> **z0mbie said:**
> This is a fantastic tutorial. Worked for me right off the bat.

Thanks, good to hear.

I was worried when I was buying this card as I could see a lot of people having problems with it. I put info together from few threads and guides and this is what worked for me without problems. 

I hope it will be useful to others as this card comes with a lot of new PCs.

---

### Post by z0mbie on 2007-08-08
Oh so you're the author of that tutorial? Thats awesome, I think you should write more tutorials like that. It is simple and very efficient. Thanks for writing it!

---

### Post by YaroMan on 2007-08-09
Envy solved an Issue ;)

---

