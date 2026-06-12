---
title: "Screen resolution woes..."
date: 2006-10-05
forum: Desktop Environments
---

### Post by urbandryad on 2006-10-05
Kubuntu doesn't like me. :( I finally got the dang thing to install and it isn't detecting my screen properly. I even edited the xserver xorg configuration file, followed all the instructions on this website I could find in the forum, removed all the under 1024x768 from the file and everything is set up under display settings. I've restarted x server countless times and it still isn't detecting my settings, and it still only gives me an 800x600 monitor. What the heck am I doing wrong? ](*,) 

My video card is a neomagic in a Dell Latitude Cpi notebook. :( Please help me. :(

---

### Post by JGuru on 2006-10-05
First backup your '/etc/X11/xorg.conf' file

 $ **sudo cp /etc/X11/xorg.conf /etc/X11/xorg_back.conf**

 $ **sudo gedit /etc/X11/xorg.conf**

  Make the required changes in the file as per Screen Resolution your Monitor
 supports.
 Save the file. Now for the changes to take effect, type the following commmand:

 $ **sudo dpkg-reconfigure -phigh xserver-xorg**

 Logout & login again.

---

### Post by urbandryad on 2006-10-05
OKay, that didn't work. I still have the black stripe of unused monitor space around my desktop. >_> I suppose I can live with my resolution like this, it isn't too bad.

My friend suggested I update my BIOS. What do you think, and how do I do this? :P

---

### Post by urbandryad on 2006-10-05
Doesn't anybody care? Helloooo? Still need help. :(

---

### Post by jd65pl on 2006-10-05
Do you have the correct drivers installed for your card?

As previously mentioned the command below helps you configure the resolution   of the x server
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

You may wish to configure other functions of the xserver to try to resolve this, I do not have the same graphics card to recreate the issue or have heard of it before so could give an exact fix.

Try the command below for reconfiguring the xserver
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by dave2010 on 2006-10-05
Hold on, hold on!
Black stripe?
Have you tried adjust the field size with the controls on your monitor?
You never know.
D.

---

### Post by jd65pl on 2006-10-05
> Hold on, hold on!
Black stripe?
Have you tried adjust the field size with the controls on your monitor?
You never know.

That could also be a good option!

---

