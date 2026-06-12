---
title: "setting virtual resolution"
date: 2008-03-31
forum: Desktop Effects &amp; Customization
---

### Post by idnael on 2008-03-31
i want to run a application to take screenshots but the size i need is larger than my display.

So i suppose i can do that by configuring a virtual resolution that is larger that the physical resolution... Don't know if that Would work.

But i tried changing the Virtual setting in SubSection "Display" and nothing happened. The virtual resolution i specified is not used and the display doesn't scroll.

My system is Ubuntu 7.10 and the graphics card is Nvidia GForce 8.

How can i configure a virtual resolution??

thanks
daniel

---

### Post by pablol on 2008-05-01
I'm having the same problem. Does anyone know how to do this?
tia

---

### Post by vikasvishnu on 2008-05-02
> **pablol said:**
> I'm having the same problem. Does anyone know how to do this?
tia

Hmm.. I am not sure about this, but the "scrot" package can take screenshots with the size you specify. I haven't tried this yet, but:

1) Install scrot
2) man scrot

Check on it and see if it can meet your requirement. I will surely check on this and will let you know when I get to my computer.

-Vikas-

---

### Post by pablol on 2008-05-02
Vikas thanks for your reply, but I've made a mistake (I got confuse after reading so many forums about it). What I'm trying to do is to set Virtual Resolution to be bigger than my real resolution in Ubuntu Gutsy. The Virtual statement in the xorg.conf is being ignored. I've read that this may not work in this version of ubuntu. Any ideas?

---

### Post by vikasvishnu on 2008-05-02
> **pablol said:**
> Vikas thanks for your reply, but I've made a mistake (I got confuse after reading so many forums about it). What I'm trying to do is to set Virtual Resolution to be bigger than my real resolution in Ubuntu Gutsy. The Virtual statement in the xorg.conf is being ignored. I've read that this may not work in this version of ubuntu. Any ideas?

I am not sure if this works in your version, friend. But its worth a try. I am not sure about this, but I see many posts which says editing xorg.conf by hand is not resulting in the desired changes. Can you try this?

> sudo dpkg-reconfigure -phigh xserver-xorg

You should be able to add new resolutions from there. Once done, save your settings and try switching your resolution under System > Preferences > Screen Resolution. You might have to restart your X Display to get the changes to take effect. 

[COLOR="Sienna"]**PS: Please make sure to backup your current Xorg.conf file so you dont mess up things**[/COLOR]

Vikas

---

