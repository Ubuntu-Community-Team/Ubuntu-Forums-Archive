---
title: "Openbox problem."
date: 2007-06-30
forum: Desktop Environments
---

### Post by Freddy on 2007-06-30
Hi all.

I just recently installed Openbox, I tried to make a autostart.sh for Openbox using this guide [http://icculus.org/openbox/index.php/Help:Autostart](http://icculus.org/openbox/index.php/Help:Autostart). When choosing to open up a Openbox autostart session through GDM this happen.
```
Xsession unable to launch "home/freddan/.config/openbox/
autsotart.sh "X session---"/home/freddan/.config/openbox/
autostart.sh" not found; falling back to default session.
```
Can anyone help me with this one?

/Freddan

Ohh btw, I'm using 3.4.2, upgraded ubuntus older version with debs from Openbox site.

---

### Post by urukrama on 2007-06-30
copy the default menu.xml, rc.xml and autostart.sh files which should be in /etc/xdg/openbox/

The menu.xml file contains your menu settings; the rc.xml file basically everything else (keyboard shortcuts, desktops, fonts, mouse, individual applications, etc.)

---

### Post by moore.bryan on 2007-07-01
[I]are you sure your autostart.sh file is executable?
```
sudo chmod 777 ~/.config/openbox/autostart.sh
```
[/I]

---

### Post by Freddy on 2007-07-01
Hi Brian.

I'm using this guide [http://doc.gwos.org/index.php/Openbox_GnomeStraight#Use_obmenu](http://doc.gwos.org/index.php/Openbox_GnomeStraight#Use_obmenu) and I followed it to the letter but when reaching the point where I have to make a desktop entry something goes terrible wrong.

I fire up the file with nano,
```
sudo nano /usr/share/xsessions/openbox-autostart.desktop
```
but when tying to save it, I get a error.
> No such file
I looked the place up with Thunar and it exist and the freaking file is there, but I cant change it or chmod it.

Thanks for any help  / Freddan

---

### Post by moore.bryan on 2007-07-01
*okay... this might be an easy one to fix.  first, make sure you're in your home dir (cd ~), THEN create the file (sudo nano openbox-autostart.desktop).  put all the junk inside, save, and move the newly created file to the right place (sudo mv openbox-autostart.desktop /usr/share/xsessions/).  at this point, make sure it's executable (sudo chmod +x /usr/share/xsessions/openbox-autostart.desktop).  that should fix the problem.*

---

### Post by Freddy on 2007-07-01
Thanks for your help Bryan. 
I managed to fix my problem. I just created the autostart.sh file inside ~/.configure/openbox and left it at that. Didn't have to do any make any desktop files inside /xessions.

Now it's just some tinkering left and maybe finding myself a decent wallpaper :).

/Freddan

---

### Post by moore.bryan on 2007-07-01
*that was going to be my suggestion if the other didn't work... glad to hear you got it up and running.  for the bg, may i suggest this one:*

---

### Post by Freddy on 2007-07-02
Yes you may :), nice wallpaper a little to dark for my taste and the theme I'm using though ;).

/Freddan

---

### Post by moore.bryan on 2007-07-02
*no problem... make sure to check out [box-look.org]("http://www.box-look.org/") in your search.*

---

### Post by Freddy on 2007-07-02
Yeah, that has becoming my second home in the last few days, that and DeviantART that is :). The only problem with DeviantART that I know of, is you plan to browse through a few pages to find yourself a new wall and you mistakenly stay for hours ;).

/Freddan

---

