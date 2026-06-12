---
title: "xubuntu won't work"
date: 2005-12-31
forum: General Help
---

### Post by Jammy_Stuff on 2005-12-31
After going through hell last night using a virtual machince to make an install CD for xubuntu, I managed to install it on one of my spare PCs. Then following the install guide, I installed gdm using:

```
sudo apt-get install gdm
```

This all went well and there were no errors. However when I try to boot into gdm using:

```
sudo /etc/init/d.gdm start
```

I get nothing on screen but a bar that alternates between green, purple and orange stripes. When I type in my username, hit enter, then type my password and hit enter, The bar across the top changes to white. How can I get it to display properly?

---

### Post by spite on 2005-12-31
Have you tried typing 'startx' ? This should make your GDM pop into screen and let you start a graphical session.

---

### Post by Jammy_Stuff on 2005-12-31
I tried that. It is popping into a graphical session, I think. It only seems to show a bar acroos the top though. The rest is just a black screen. Interestingly, it works on a VM I have set up in Windows (different PC). Are there any things installed in Ubuntu that aren't in XUbuntu to do with hardware compatability?

---

### Post by Jammy_Stuff on 2005-12-31
I've had a think and I can't help but think that it may be down to the xserver cofig. I'm using an old Dell M770 monitor and the Pc (a Dell Dimension L933r) has onboard graphics. Does anyone know what options I want to choose in the xserver configuration?

[Edit: If I set it to VGA as the driver, I can at least get it to display. Although it only shows about a quater of the screen and at 8 bit colour. Anyone know one it would work better with?]

---

### Post by Iandefor on 2005-12-31
What is the onboard graphics card?

---

### Post by Jammy_Stuff on 2005-12-31
I'm not sure. I'll install Windows 2000 tonight and post what it says in the device manager.

---

### Post by majikstreet on 2005-12-31
probably a xserver config issue.. i have a dell dimension 2350 and i got similar output until i reconfigured the xorg

---

### Post by Jammy_Stuff on 2005-12-31
Any chance you could tell me what you had to change the config to? I really want to get this working.

[Edit: Got Windows installed on it. It's an Intel 810 graphics controller hub]

---

