---
title: "Gnome doesn't keep the resolution settings..."
date: 2005-03-27
forum: Desktop Environments
---

### Post by lordmyth on 2005-03-27
Well... I made X have the right resolution settings for my monitor, and I can choose it with the resolution settings app in Gnome, but the next time I start Gnome, it gets again in the 1024x768 resolution... Any ideas why he would do this?

---

### Post by martijntje on 2005-03-27
I don't know why it would do that. However, i do know how to correct it.

Open your xorg.conf file.
```
sudo nano -w /etc/X11/xorg.conf
```

Look for a section called "Screen"
In this section, you will see a number of screenmodes. Locate the one you like, and note the "Depth" value there. Now, go back to the beginning of the Screen section, and change the DefaultDepth option to this value. Save the file.

X will now use that one as your default screen.

Press <Ctrl>+<Alt>+<Backspace> to restart your X server, and test if it works.

---

### Post by lordmyth on 2005-03-27
Ehh, I was asking for the resolution, not the screen depth!!! Please, read the post properly, I'm really no noob, the xorg.conf file is set up fine.

---

### Post by martijntje on 2005-03-27
In that case, why don't you comment out all the resolutions you don't use? That surely solves the problem.

---

### Post by lordmyth on 2005-03-27
That does not work, and even if it would, it wouldn't be a very good solution... In my opinion, the problem lies in Gnome somewhere, not with the X configuration...

---

### Post by DougZ on 2005-03-31
I'm having the same problem and I *am* a linux noob, so don't want to play any more than I have to.  (I say this having re-installed about a dozen times now thanks to user-induced screwups - guess that's why they call it a learning process  8-[  )

I really want my logon screen and my user screen resolution set to 1024x768. On my crappy monitor thats about the max and still be readable.

I changed it and selected "remember settings".  Rebooted, and everything is cranked  back up to 1600x1200.  I can see the logon screen being like that, but not my personal desktop ???

This really a pain, so any help would be greatly appreciated.

---

### Post by DougZ on 2005-03-31
nvm, after the last upgrade of my packages, performed just minutes ago, gnome now keeps my screen resolution.  Now if I could just figure out how to change the resolution of the logon screen...

---

### Post by xinel on 2005-07-28
Im having the same problems and Ive been working on it for hours.

---

### Post by wiraone on 2005-07-28
It seems that some setup or some weird thing happened to me too .. this doesn't happend when I'm using Fedora .. whenever I turn on my PC without turning on the monitor, Ubuntu decided that it will go for the lowest resolution that I've which is 800x600 .. switch on the monitor and do the ctl-alt-backspace and it back to normal .. there should be something .. somewhere that differentiate  X setup in Fedora and Ubuntu ..

---

### Post by BanskuZ on 2005-07-29
i'm having the same problem.  ](*,)

---

### Post by Owdy on 2005-09-16
[QUOTE=martijntje]
Look for a section called "Screen"
In this section, you will see a number of screenmodes. Locate the one you like, and note the "Depth" value there. Now, go back to the beginning of the Screen section, and change the DefaultDepth option to this value. Save the file.[/QUOTE]


I have 5 of them, and they all are same:
> 
 SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection

Can i edit one those, to like this:

>  SubSection "Display"
                Depth           16
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection 
?

---

