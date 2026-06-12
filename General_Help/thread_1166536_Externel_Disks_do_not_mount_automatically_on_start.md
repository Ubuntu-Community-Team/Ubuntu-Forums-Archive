---
title: "Externel Disks do not mount automatically on start-up with desktop disabled"
date: 2009-05-21
forum: General Help
---

### Post by d_inevitable on 2009-05-21
Hi,

in order to have different wallpapers on each compiz viewport, I have disabled the nautilus desktop using gconf-editor. I am not quite sure which value it was, but I think it has been the following:
[INDENT]>  /apps/nautilus/preferences/show_desktop[/INDENT]Ever since I did that, my external drives are no longer mounted on system start-up, but do get mounted the moment I point nautilus to 'computer:///'.

This is quite a big problem for me as I do have some start-up applications that expect some drives to be present.

Is there a way I could mount all available external drives on start-up without using the nautilus desktop?

I suppose I could launch nautilus and point to 'computer:///' at start-up, but then the nautilus window would be quite annoying every time I login, so therefore I am looking for a  better solution. Any Ideas?

---

### Post by taurus on 2009-05-21
Are those external drives always connected to your machine?  You could add entries in /etc/fstab for those drives so they would be mounted automatically each time you boot Ubuntu.

---

### Post by d_inevitable on 2009-05-21
That's the thing, they can occasionally be unplugged I also will be adding other drives, etc. 

Therefore I am looking for a more dynamic solution.

---

### Post by d_inevitable on 2009-05-24
bump

---

### Post by raymondh on 2009-05-24
> **d_inevitable said:**
> That's the thing, they can occasionally be unplugged I also will be adding other drives, etc. 

Therefore I am looking for a more dynamic solution.

Hello d_invitable,

something "dynamic" like this?

[http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/)

Hope it helps.

---

### Post by d_inevitable on 2009-05-25
> **raymondhenson said:**
> Hello d_invitable,

something "dynamic" like this?

[http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/)

Hope it helps.

Well, that's not exactly what I meant by dynamic. Sorry, I should have perhaps clarified this. 

But what I really was looking for is some way to bypass gnome-desktop, (which in my opinion should have nothing to do with mounting external hard drives) to detect any available external disks rebooting and mount them accordingly.

It seems that I would need to explicitly tell pysdm which disks to mount on start up.

It seems like a nice tool though. I haven't had a chance to reboot yet to see whether it will mount all the drives that I have configured with it.

Can this gnome-desktop behaviour be considered as a bug btw? Obviously it was intentional, but it really seems like some kind of poor workaround to me.

---

