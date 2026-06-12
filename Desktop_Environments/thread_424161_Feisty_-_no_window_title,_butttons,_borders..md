---
title: "Feisty - no window title, butttons, borders."
date: 2007-04-26
forum: Desktop Environments
---

### Post by pt78 on 2007-04-26
Hi, I was trying to install msfonts, but I ended with almost unusable Ubuntu - no window menus, title, buttons, 
borders. Any Idea what went wrong? 

I do not use windows effects. 
Xorg.0.log says nothing much interesting:
 Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!

---

### Post by Pox on 2007-04-27
Try pressing Alt-F2, typing "gnome-terminal", then run "metacity --replace" in that terminal and post any error output.

---

### Post by smokey on 2007-04-27
> **Pox said:**
> Try pressing Alt-F2, typing "gnome-terminal", then run "metacity --replace" in that terminal and post any error output.

I tried that method and it killed beryl and forced me to run meta city only

---

### Post by swingincelt on 2007-04-27
I've seen this when enabling TwinView in nvidia-settings.  Don't know why it happens though.

---

### Post by Pox on 2007-04-27
> **smokey said:**
> I tried that method and it killed beryl and forced me to run meta city only

I thought you said you weren't running desktop effects? Thought you were referring to beryl/compiz there.

In that case, it's an emerald issue.  run "emerald --replace" from a terminal and post any errors.

---

### Post by smokey on 2007-04-27
Well I have a blank terminal window. it's as if the letters are the sam e color as the back ground... no way to change since I don't have a window border :confused: 

I kno wif I uninstall beryl I get my borders back and Terminal is normal again

---

### Post by fwojciec on 2007-04-27
Your card seems doesn't seem to be properly configured for use with Beryl.  Can you post your xorg.conf?

sudo gedit /etc/X11/xorg.conf

cut and paste the contents of the file here...

---

### Post by pt78 on 2007-05-01
I ended up with reinstalling Ubuntu. From start it was fine, but after some restarts problem appard again. I did not do any setting which may influence this (IMHO). Maybe it has something to do with graphics driver (I have Nvdia 6200)...
Anyway. I learned that I can bring window stuff (borders, title, close button....) by enabling and disabling Desktop effects. Quick fix, but after restart problem is back again...

I'm fairly desperate, even thinking of going back to 6.06.

---

### Post by Sunflower1970 on 2007-05-01
Had a similar problem with Feisty Ubuntu/Xubuntu. In Ubuntu I had to add Metacity to the startup menu and now they show up fine and dandy. Not too sure why they stopped showing up one day....This was after I had disabled Compiz at start up. 

It also happened in Xubuntu. I had decided I wanted to try the Xfce desktop for something different. The borders were there one day, then disappeared. So I uninstalled it. I just redid it last night. Haven't had a chance to see what happens, but I'm going to guess I'll have to either keep Metacity installed to keep the borders around, or maybe add xfwm4 to the startup menu to make sure my borders always show up.

---

### Post by pt78 on 2007-05-02
Sunflower1970 - And does session save and restore works OK if you add Metacity to the startup menu?

---

### Post by spayced on 2007-05-03
I have this same problem too. As the poster above suggested, solution is enabling and disabling Desktop effects. But it's annoying having to do this every time.

ATI Radeon X300 using fglrx driver.

---

### Post by craized on 2007-05-03
Hello, I just installed Ubuntu and set up my dual monitors and I'm having the same trouble. I'm fairly inexperienced with unix and I don't know where to start. Any pointers would be GREATLY appreciated.

Thank you

(if you need more info please ask for it with the command I need)

---

### Post by craized on 2007-05-03
[http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia](http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia)
I found a solution that worked for me. Thanks anyway.

---

### Post by pt78 on 2007-05-15
> **craized said:**
> [http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia](http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia)

Well, I tired those hints, I tried reinstalling Nvidia drivers using latest Envy. Nothing helped. I usually start without window decorations, only sometimes there are some at startup. Considering going back to 6.06...
:(

---

### Post by pt78 on 2007-05-20
It seems OK after last update of metacity. :)

---

### Post by de_pol on 2007-05-20
i had the same problem with beryl.
i was able to fix it, look in your advanced beryl options for rendering, and change it from automatic to XGL rendering.

that did it for me.

---

### Post by sab0403 on 2007-07-02
> **smokey said:**
> Well I have a blank terminal window. it's as if the letters are the sam e color as the back ground... no way to change since I don't have a window border :confused: 

I kno wif I uninstall beryl I get my borders back and Terminal is normal again

I had the exact same problem. It got solved by doing this:

[INDENT]1. Backup your /etc/X11/xorg.conf (sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup)
2. Edit your xorg.conf (sudo nano /etc/X11/xorg.conf)
[INDENT]A. In the Screen0 section add the following:
```
Option "AddARGBGLXVisuals" "True"
```
B. Save new xorg.conf (<Ctrl>+<O> to save, <Ctrl>+<X> to exit)[/INDENT]
3. Restart X (<Ctrl>+<Alt>+Backspace)[/INDENT]

which I found [here]("http://ubuntuforums.org/showpost.php?p=2514042&postcount=2"). My graphics card is a nVidia GeForce4 MX, btw. Props to Spr0k3t - it isn't my solution.

Hope this helps.

---

### Post by Nakkis on 2007-07-02
Run 

```
sudo nvidia-xconfig --add-argb-glx-visuals 
```

and restart X by pressing Ctrl+Alt+Backspace.

---

