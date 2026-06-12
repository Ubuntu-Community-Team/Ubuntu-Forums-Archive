---
title: "screen resolution"
date: 2006-08-03
forum: Desktop Environments
---

### Post by Kodiak3000 on 2006-08-03
I finally got my Ubuntu installed in a sparkling new box I built myself!

But I'm using a widescreen monitor, and it doesn't look like my resolution is supported. The monitors drivers are .exe files.  Any ideas?  I could convert them if there was a way to do that.  Suggestions welcome.

Thanks.

---

### Post by orb9220 on 2006-08-03
No you cannnot use windows video drivers. You must search for drivers for your graphics card type and monitor type.

Do a forum search for the graphics card and see which drivers you need.

---

### Post by endfx on 2006-08-03
Look in your monitor manual and see what resolution your monitor is.

Next do this:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.working

Now open up xorg.conf (as root) and change the following lines:

 SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection

All you have to do is add the new resolution you want to be the FIRST resolution in the Modes line. Ex:

Modes           "NEWxRESOLUTION" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"

Save, and restart X (or restart your computer)
If it doesn't work, and looks the same, then you need to upgrade your video card drivers -- a whole other topic :)

---

### Post by Kodiak3000 on 2006-08-03
Thanks endfx - can you tell me how to get to that sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.working?

Should I be looking for a folder called sudo? Or entering a command prompt.

Sorry, not very good at this part of it all.

Thanks

---

### Post by endfx on 2006-08-03
You enter that sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.working

at a command prompt (applicatioins -> Accessories -> Terminal)

What you're doing there is making a backup of the xorg file so incase something goes wrong you can go back to the working version.

---

### Post by Kodiak3000 on 2006-08-04
Sigh.

Okay, I can get into the terminal application, and type all that "stuff" in, but I just get another line like user@user~

Where is xorg.conf?

Sorry to be so dense - I was never any good with DOS, either :oops:

---

### Post by herrpoon on 2006-08-04
> **Kodiak3000 said:**
> Sigh.

Okay, I can get into the terminal application, and type all that "stuff" in, but I just get another line like user@user~

Where is xorg.conf?

Sorry to be so dense - I was never any good with DOS, either :oops:

That probably means its worked :p 

Once you've made a back up of it you can navigate to your xorg.cong (which is your graphics configuration file) via the Computer icon like you would in windows clicking on etc, then X11, and right clicking on xorg.conf, choosing your text editor, to make the necessary changes.

---

### Post by nightfire117 on 2006-08-04
> **Kodiak3000 said:**
> Sigh.

Okay, I can get into the terminal application, and type all that "stuff" in, but I just get another line like user@user~

Where is xorg.conf?

Sorry to be so dense - I was never any good with DOS, either :oops:

First, go to the command prompt:

Applications> Accessories> Terminal

(you do this through the GNOME menu, whatever it's called).

Then, in the terminal, you enter:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.working
```

which makes a copy of your xorg.conf file and names the copy as xorg.conf.working. The files are located in /etc/X11/....

Then, in the Terminal again, type:

```
sudo gedit /etc/X11/xorg.conf
```

and GEDIT should open up xorg.conf.

Where you see:

```
SubSection "Display"
Depth 24
Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
```

in the file, add the resolution you want to use to be first in the list, i.e. my screen is at 1600x1200, so:

```
SubSection "Display"
Depth 24
Modes "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
```

and since you said you have a widescreen (???) you'd just have to place your widescreen's resolution first in that list, like where I put 1600x1200. You should do this for where it says "Depth 24" and any other lower "Depth" value. This is your color depth, I believe(???) but I am still a n00b to Linux myself (I just screwed up my X window yesterday and had to reformat my Ubuntu, and now I'm gonna try installing the nvidia drivers another way....), so I am not responsible for any damages that may occur or anything that goes wrong. I only hope I could help. Thanks! :D ^_^

~Nightfire

---

### Post by Kodiak3000 on 2006-08-04
Thanks nightfire ...

I don't know what I did, but it looks right now.  I'm going to hang on to your post though!

Cheers

---

