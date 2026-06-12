---
title: "Ubuntu with Kubuntu shutdown screen?"
date: 2006-07-07
forum: Desktop Environments
---

### Post by newlinux on 2006-07-07
I recently installed KDE just to test it out using
```
sudo aptitude install kubuntu-desktop
```

Now, even when I log in using Gnome, I get the Kubuntu shutdown screen when I shutdown. Is there a way I can get back to the Ubuntu shutdown look without removing Kubuntu-desktop? Or did I install the KDE wrong in the first place?

Thanks,
Marlon

---

### Post by Dr. Nick on 2006-07-07
I beleive that is due to kdm. You are not able to hit the shutdown from within gnome, you have to log off and then shutdown correct? If so then I know what you mean and can offer a possible solution [here]("http://ubuntuforums.org/showthread.php?t=22271&highlight=replace+kdm+gdm")

If not then I dont follow your problem
[]("http://ubuntuforums.org/showthread.php?t=22271&highlight=replace+kdm+gdm")

---

### Post by newlinux on 2006-07-08
I'm sorry if I'm not clear. When I click the logoff/shutdown/switch user/restart button and then choose shutdown, the splash screen that is displayed (showing services shutting down, unmounts, etc.) is the Kubuntu splash screen...

Thanks

---

### Post by Dr. Nick on 2006-07-08
ohhhhh Ok. so when you shutdown you get the blue text and when you boot its brown, or blue?

I have this same problem and never bothered to look into a fix. Those boot up / shutdown screens are called usplash

look at this thread, specifically the last post for a possible fix
[http://ubuntuforums.org/showthread.php?t=209978&highlight=restore+ubuntu+usplash](http://ubuntuforums.org/showthread.php?t=209978&highlight=restore+ubuntu+usplash)

---

### Post by newlinux on 2006-07-08
Exactly what I needed. Thanks!

---

### Post by newlinux on 2006-07-08
I also had to do:
```
sudo dpkg-reconfigure linux-image-`uname -r'
```

see:

[http://doc.gwos.org/index.php/Different_usplash](http://doc.gwos.org/index.php/Different_usplash)

---

