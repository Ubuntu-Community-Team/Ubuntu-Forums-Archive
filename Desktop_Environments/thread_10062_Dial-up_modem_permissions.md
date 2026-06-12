---
title: "Dial-up modem permissions"
date: 2005-01-04
forum: Desktop Environments
---

### Post by brk3 on 2005-01-04
Hi, I just installed ubuntu and am very impressed etc. Thanks to all who made it possible. I am on a dial-up connection, and am using gnome-ppp to dial up. This is working fine, but the only problem is I have to run it as root. I dont have permissinns to the /dev/TTYSH0 or whatever the device is called. Ive tried changing some of the permissions but 1. I dont think I should have to go messing with permissions, and 2. That still doesnt work, there's still other files I need permissions to so it cant get a connection.
Why do I need root permissions to dial up, (i didnt on mandrake, which was my last distro). Really hope someone can help or tell me what I have to do to enable full uuse of gnome-ppp/wvdial because this is the only thing thats bogging me down in ubuntu so far.

Thanks,
paul.

---

### Post by zenwhen on 2005-01-05
[http://www.ubuntulinux.org/wiki/DialupModemHowto](http://www.ubuntulinux.org/wiki/DialupModemHowto)

This HowTo will get you there.

---

### Post by brk3 on 2005-01-05
Thanks for the link, its great, but to be honest not very cool for your modern user. People coming from other easy to use OS's dont want to be messing with scripts etc. and modem lights sucks.
Luckily for me I got my modem sorted, but I think Ubuntu should take this into to account for their next release, there still are dial-up users out there! (we'e mad, and we're not gonna take it anymore! well, at least until they bring broadband to my area  :mrgreen:  )

Here's what I did to get mine working and people may find it usefull:

1. Install gnome-ppp from either the package manager or from here get it off the net.
2. Put in your details and options in gnome-ppp and this will configure wvdial for you.
3. You now should be able to dial up *as root*, but if like me your having trouble accessing your modem as a normal user, make sure you have permissions to your modem device/sym-link, and any other ppp related files. The final thing that did it for me was that you need to give /usr/sbin/pppd 'set-uid id'. I did this by exectuing:

sudo nautilus /usr/sbin/

and then right clicking pppd and selecting the 'set user id' box.

I can now dial up as normal user. Ubuntu developers take note: this is too much trouble to get dial up working appropiatly! So just for the next realease if you could  take these details into account and pleasse include gnome-ppp in the installed packages. This program is essential for us dial-up users.
Thanks.

p.s. wow, my first mini-howto :) if you want this done out in more detail just let me know. maybe its worthless but just if I hadnt figured this out by now id probably be half way though a windows install by now. well ok, mandrake  :D

---

