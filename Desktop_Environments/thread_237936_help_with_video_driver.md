---
title: "help with video driver"
date: 2006-08-16
forum: Desktop Environments
---

### Post by codegamer on 2006-08-16
i have some minor experience with linux, however it was with FC4. (just so you know where my experience lies)

i tried installing Tremulous and kept getting an openGL error. after searching google, i went to  [https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

i followed the direction on which driver is needed. (i have a NVidia GeForce 5600 FX) on the next page it said to search for nvidia-glx in the restricted area.  i followed all instructions and discovered that nvidia-glx was not on my computer (fresh install 45 mins ago).  i googled and got the nvidia-glx, but get an error:   Dependency is not Satisfiable: x11-common

So i got the x11-common and got this error:     Conflict with the installed package 'xserver-xorg'

at this point i am lost and only want to try Tremulous.

Please help me.

---

### Post by Greycloak on 2006-08-16
I'm not 100% sure on this one, but I just looked at the nvidia howto link from the page above and your card is listed as one of the 'legacy' cards.

If that is the case you need the nvidia-glx-legacy package.

---

### Post by codegamer on 2006-08-16
i though that at first (the way that the page looked at first) but at the bottom of the list of video cards is where the legacy list really is.  Mine is not in there.

---

### Post by Greycloak on 2006-08-17
D'oh!  Sorry about that! Unfortunately I don't have any other suggestions as I am an ATI user.

---

### Post by codegamer on 2006-08-17
that's ok, like i said, it got me too.  if anyone else could help me in any way, Please do.

---

### Post by Greycloak on 2006-08-17
Did you look it up in Synaptic Package Manager?

---

### Post by codegamer on 2006-08-17
that seemed to work.  when the guide said to search, i thought that it meant Places -> Search for files.

now i have another problem, when i set my resolution to 1024x768, my refresh rate is set to 85 Hz.  the problem is that it makes my screen look like crap.  the box that usually lets you change it won't let me.  how do i forcibly change it to 60 Hz?  and keep my 1024x768 resolution. (the only refresh rate that looks good on my monitor).

---

### Post by codegamer on 2006-08-18
nvm, got it working.
this thread is done, Mods please close.

---

