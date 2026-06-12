---
title: "Is there a way to Fluxbox Menus Without Fluxbox?"
date: 2007-05-23
forum: Desktop Effects &amp; Customization
---

### Post by blazercist on 2007-05-23
Ok heres the story I think the right-click system menu from fluxbox is PUUURTY, but I also think that the window animations and such in beryl are also PUUURTY, I realize that they are both window managers and therefore never the two shall meet.  I was wondering if there was a way to get that PUURTY right-click style system menu working under beryl?

---

### Post by blazercist on 2007-05-24
any body?

---

### Post by urukrama on 2007-05-25
Not that I know. You could use beryl with XFCE, which also has a right click desktop menu but looks otherwise a bit like Gnome.

---

### Post by blazercist on 2007-05-30
Why thank you I'll try xfce out today after work.

---

### Post by Pugwash on 2007-05-30
Anyone know a guide on how to get beryl working with xfce? I've got it up and running in gnome with xgl but couldn't manage to get it to work with xfce.

---

### Post by blazercist on 2007-05-30
I was actually wondering the same thing, I think it should work theoretically, seeing as how xfce is a desktop environment and beryl is a window manager... wouldn't the XGL script be the same there is a portion of the script that starts gnome i believe. just start xfce instead??  have you tried installing xfce ontop of a working gnome/xgl/beryl install and seeing if it just works?

---

### Post by FuturePilot on 2007-05-30
If you have a Nvidia card you don't need XGL.

---

### Post by chalewa on 2007-05-30
> **Pugwash said:**
> Anyone know a guide on how to get beryl working with xfce? I've got it up and running in gnome with xgl but couldn't manage to get it to work with xfce.

there are guides for this around..

however, wherever you see an instance of gnome in the startup script, merely replace that with the xfce startup command...which of course i cannot remember for some reason right now...

xfce4-desktop maybe?

---

### Post by blazercist on 2007-05-31
> **FuturePilot said:**
> If you have a Nvidia card you don't need XGL.

look at my signature pal, i have ATI

---

### Post by Pugwash on 2007-05-31
> **blazercist said:**
> I was actually wondering the same thing, I think it should work theoretically, seeing as how xfce is a desktop environment and beryl is a window manager... wouldn't the XGL script be the same there is a portion of the script that starts gnome i believe. just start xfce instead??  have you tried installing xfce ontop of a working gnome/xgl/beryl install and seeing if it just works?

I tried it, but you get problems when you try to move icons around and stuff on the desktop. I thought it might have been some sort of incompatibilty with xfce .  I'm going to try it again, I've found this guide - [http://www.linuxquestions.org/questions/showthread.php?t=555247](http://www.linuxquestions.org/questions/showthread.php?t=555247) .  The guy seems to have got it to work. Hope that helps you too.

Edit - Yes, I've just managed to get it working with the guide above.  But instead of creating  the "xgl.desktop" file in  /etc/X11/sessions/ , put it in  /usr/share/xsessions/ . Here's a screenshot, I'm so happy I got it working :) :

---

### Post by blazercist on 2007-05-31
Thanks, so the entire process was:

sudo apt-get install xubuntu-desktop
sudo mv /etc/X11/sessions/xgl.desktop /usr/share/xsessions/
gksudo gedit /usr/local/bin/startxgl.sh 
and then change gnome-session to xfce4-desktop

correct?

---

### Post by Pugwash on 2007-05-31
> **blazercist said:**
> Thanks, so the entire process was:

sudo apt-get install xubuntu-desktop
sudo mv /etc/X11/sessions/xgl.desktop /usr/share/xsessions/

Yep, you have to create the "xgl.desktop" first as detailed in the guide and then you can move it.  


> gksudo gedit /usr/local/bin/startxgl.sh 
and then change gnome-session to xfce4-desktop

correct?

You could try that, but I followed the guide exactly in case of any problems, and stuck in as mentioned there :

```
#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4  
export DISPLAY=:1 
exec xfce4-session 
```

And before finishing remember to make the script executable  by :

> sudo chmod a+x /usr/local/bin/startxgl.sh

That should get it done, if you have any problems let us know.

Cheers

---

### Post by blazercist on 2007-05-31
well i already have xgl.desktop because i have a working beryl install on my gnome/xgl session so instead of moving the file do u think copying and then editing it would work?  I don't want to create any issues where it will run multiple times or something like that but i also want it to be working if and when i go into gnome.

I realize that im being a nuisance and most of my questions can be answered by trial and error but i dont have my box infront of me cuz im at work.

---

### Post by Pugwash on 2007-05-31
> **blazercist said:**
> well i already have xgl.desktop because i have a working beryl install on my gnome/xgl session so instead of moving the file do u think copying and then editing it would work?  I don't want to create any issues where it will run multiple times or something like that but i also want it to be working if and when i go into gnome.

Ah,ok,  you're in the same position as me then. I named the file **xgl2.desktop**:

```
gksudo gedit /usr/share/xsessions/xgl2.desktop
```


Then put in:

```
[Desktop Entry]
Encoding=UTF-8
Name=Xfce with xgl
Exec=/usr/local/bin/startxgl2.sh
Icon=
Type=Application 
```

And I named the script, startxgl2.sh :

```
gksudo gedit /usr/local/bin/startxgl2.sh 
```

And entered:

```
 #!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4  
export DISPLAY=:1 
exec xfce4-session 
```

Finally, make the script executable:

```
 sudo chmod a+x /usr/local/bin/startxgl2.sh 
```


Log out and choose the "Xfce with xgl" session, and log in again. This won't affect your gnome/xgl session.

Hope that helps.

---

