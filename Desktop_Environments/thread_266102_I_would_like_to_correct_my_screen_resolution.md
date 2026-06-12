---
title: "I would like to correct my screen resolution"
date: 2006-09-26
forum: Desktop Environments
---

### Post by CaveRat on 2006-09-26
but I'm not sure what to do in xorg. My monitor is a Sceptre 20.1 wide screen and the correct setting should be 1680 x 1050. Here is my xorg settings:

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40? [Unknown nVidia Card]"
    Monitor        "Sceptre"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Any help here would sure be appreciated. These are the defaults Ubuntu installed.

---

### Post by whizbaby on 2006-09-26
Have you tried putting your desired resolution in front of 1280x1024, looks like this
Modes "1680x1050" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
Do this for every modeline, then restart the x-server (press *ctrl-alt-F1*, login and type **sudo /etc/init.d/gdm restart**, logout (*ctrl-d*) and press *ctrl-alt-F7* to get back to graphical login).

---

### Post by CaveRat on 2006-09-26
Thanks for the post. I copied this line from someone elses mode line. Can I do this? I hope this does not confuse matters.

"1020x1200" "1680x1050" "1440x900" "1280x800" "960x600"

---

### Post by whizbaby on 2006-09-26
Just put
"1680x1050"
right behind the *Modes*-word and in front of the other resolutions in your xorg.conf.

---

### Post by CaveRat on 2006-09-26
> **whizbaby said:**
> Just put
"1680x1050"
right behind the *Modes*-word and in front of the other resolutions in your xorg.conf.

Ok I'll do that and let you know what happens.

---

### Post by CaveRat on 2006-09-26
I'm dead. I'm typing from my (ugh) Windoz box. I followed your post to the letter and X is dead. I tryed to sudo gedit /etc/X11/xorg.conf to revert and could not get in.

---

### Post by whizbaby on 2006-09-26
Undoing the changes and restarting the x-server will get you back to your old state. (If x crashes you can still get to the terminal with ctrl-alt-F1 to edit files). Posting your xorg.conf would be a good next step.

---

### Post by capnrick on 2006-09-26
I am assuming that you changed the line that looks like this:
```
Depth 24
Modes "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
```

to this:
```
Depth 24
Modes "1680x1050" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
```

I should think that it would work that way.  If not... I don't know.  Hopefully you don't need to write a modeline...

I can't say for sure about ATI drivers, but I know that if you have an nvidia card and are using their drivers ("nvidia" and not "nv") you actually don't need to set the modes at all - the drivers ask your monitor and it tells them.  In this case, you can just comment out the lines using the "#" key, like this:

```
Depth 24
 # Modes "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
```

Hope you get it working

---

### Post by CaveRat on 2006-09-26
I could not get in to xorg.conf. I am using a Nvidia card, but I installed it a few weeks after I installed Ubuntu. I'm also using the restricted Nvidia driver.

---

### Post by whizbaby on 2006-09-26
Yes, you can.
less /etc/X11/xorg.conf (at least boot from liveCD and post it from there (the xorg.conf on the HD, not of the live system))

---

### Post by CaveRat on 2006-09-26
OK all is well now. I did a reboot and I'm back. Whew! It did boot to the new resolution, but it looked bad. There were like shadows in the text. Out of focus or something. I guess I'll stick to the default resolution unless someone has any ideas or suggestions.

---

### Post by CaveRat on 2006-09-26
> **whizbaby said:**
> Yes, you can.
less /etc/X11/xorg.conf (at least boot from liveCD and post it from there (the xorg.conf on the HD, not of the live system))

less? What is that? Sorry if I seem dumb, but I am a wannabe ex Windoz Ubuntu noob. I guess that qualifies me for the dumb part. LOL

---

### Post by whizbaby on 2006-09-26
*less* is a comfortable terminal command and shows the content of a file  in several ways (directed by options).
So typing
**less /etc/X11/xorg.conf**
shows you the content of xorg.conf and lets you browse and search in it, quit with 'q'.
Type **man *command*** for the manual of *command*. 
You could also post your xorg.conf as an attachement (look at the bottom of *reply to thread* screen).

---

### Post by CaveRat on 2006-09-28
> **whizbaby said:**
> *less* is a comfortable terminal command and shows the content of a file  in several ways (directed by options).
So typing
**less /etc/X11/xorg.conf**
shows you the content of xorg.conf and lets you browse and search in it, quit with 'q'.
Type **man *command*** for the manual of *command*. 
You could also post your xorg.conf as an attachement (look at the bottom of *reply to thread* screen).

Sorry it took me awhile to get back to you here. I appreciate all the help you gave here. I will check out the man command. I also added 1490x900 resolution the next morning. This is the one I'm using now, and the fonts look normal. 1680x 1050 was too small for my aging eyes.

---

