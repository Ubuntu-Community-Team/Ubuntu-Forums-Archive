---
title: "Login screen resolution messed up"
date: 2007-02-10
forum: Desktop Environments
---

### Post by timmay on 2007-02-10
After an automatic update to linux kernel 2.6.16-11 my nvidia driver broke so I reinstalled it. However the screen resolution for the login screen is 1280x1024 as it should be BUT it's displaying it in a scrolling screen with a 1024x768 screen resolution. i.e. it's zoomed in and scrolls when moving the mouse to the edge of the screen.

Can someone let me know how to get it corrected?

---

### Post by ingo on 2007-02-11
try 
> sudo dpkg --reconfigure -a
to get gdm back on track...

hth

---

### Post by ingo on 2007-02-11
oops, something weird happened here...

---

### Post by alanhaggai on 2007-02-11
In your /etc/X11/xorg.conf file, sort the resolutions in order of preference. Like 1280x1024 comes before 1024x768 and so on. This might help you.

---

### Post by timmay on 2007-02-11
Thanks alanhaggai I'd got the resolutions in the wrong order without realising it ... silly me!

For some reason I had to manually add the 1280x1024 resolution to the xorg.conf the get 1280x1024 working in the desktop but I'd just added it on the the end of the list of resolutions.

Thanks

PS Ingo

I tried "sudo dpkg --reconfigure -a" but that doesn't seem to be a command.

I also tried "sudo dpkg-reconfigure gdm" which I thought might be what you meant but that didn't work ... I guess that's because it was a missconfig of xorg and not gdm.

Now I need to get the drivers for my TV card reinstalled on the new kernel and everything will be back to normal.

---

### Post by shareMenaPeace on 2007-02-11
see also this topic
[http://ubuntuforums.org/showthread.php?t=358572&highlight=envy](http://ubuntuforums.org/showthread.php?t=358572&highlight=envy)

Specialy look for envy as an alternative fix.

---

### Post by ingo on 2007-02-12
yeah, sorry, my mistake. Command should have read
sudo dpkg-reconfigure -a
but don't use that cos dpkg will ask you a lot of silly questions... This one is better 'cos aimed at gdm specifically
> sudo dpkg-reconfigure gdm

---

