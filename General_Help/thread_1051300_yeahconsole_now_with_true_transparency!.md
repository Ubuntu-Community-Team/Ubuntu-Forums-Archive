---
title: "yeahconsole: now with true transparency!"
date: 2009-01-26
forum: General Help
---

### Post by hopla on 2009-01-26
I got yeahconsole working, with true transparency!

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=101136&stc=1&d=1233002749[/IMG]
Screenshot of upper left corner of my screen, running yeahconsole, with standard xterm, zsh shell and top. Showing two gnome terminals underneath.

Since tilda (in repos) doens't work anymore for me in Intrepid, I needed to find a different FPS style terminal. So I found yeahconsole, which is just as slim as tilda (no fuzz) and doesn't seem to have the annoying key-focus bug tilda had. Hooray!

One thing that it doesn't have however is true transparency. If you use a terminal that supports transparency (not the standard xterm, but e.g. rxvt) you can get some fake kinda looking transparency like in the old days where you see the background, but not any windows between the app and the background.

After a long and windy road in search for True Transparency, I finally found a solution. I'm just gonna give it to you straight. If you would also like to know why and how this works and why I didn't do it with XYZ, please ask below.

The only thing you need to have installed from repos is yeahconsole (apt-get install yeahconsole).

Create an executable script (I named it yeahconsole_transparent) somewhere in your home directory containing:
```
#!/bin/sh

# start yeahconsole
yeahconsole &

# wait a little until all the windows are created
sleep 1

# get yeahconsole window id
id=$(xwininfo -root -tree | grep yeahconsole -B 2 | head -1 | perl -p -e 's/^ *(0x.*?) .*$/$1/g')

# make transparent!
# value is between 0 (invisible) and 2^32 (fully opaque)
xprop -id "$id" -f _NET_WM_WINDOW_OPACITY 32c -set _NET_WM_WINDOW_OPACITY 3221225472

```

You can know run yeahconsole_transparent and you will get a transparent yeahconsole! Yeah!

Now, how to get this at login. Go to System > Preferences > Sessions. Click add and fill in a name (YeahConsole Transparent) and a description if you want. As the command enter:

```
sh -c 'sleep 15 && /path/to/yeahconsole_transparent'
```

The sleep thingy is necessary, else the script might fail if Gnome is not yet fully started.

Click Save and Close. Logout and log back in and check out your new transparent yeahconsole!

Remarks:
* Notice that everthing in the console is transparent. Even the characters, so it's no gnome-terminal transparency, but if you keep the console relatively opaque (high OPACITY value in the script), it shouldn't bother you to much.
* I'm running Gnome with Compiz, I did not yet try this with Compiz disabled or on KDE, but I think it should work with any compositing window manager (and thus also with any desktop manager)...
* Tell me if it works for you too, not just if it doesn't, thanks :)
* These are my yeahconsole settings in .Xresources:
(twosuperior is the key under ESC on some/most azerty keyboards, handleWidth 0 gets rid of the ugly grey resize handle (you can still resize with Ctrl++ or Ctrl+-))
```
yeahconsole*restart: 1
yeahconsole*toggleKey: None+twosuperior
yeahconsole*consoleHeight: 20
yeahconsole*aniDelay: 10
yeahconsole*faceName: Monospace
yeahconsole*faceSize: 8
yeahconsole*handleWidth: 0

```

---

### Post by thephoenixvampire on 2009-01-27
this might sound stupid....but by chance, where is the .Xresources file?

---

### Post by C0pac3t1c on 2009-01-27
hmmm

---

### Post by hopla on 2009-01-27
You must create the .Xresources file in your home directory.

@C0pac3t1c: is that a bad hmmm or a good hmmm?

---

### Post by 0bsidian on 2009-01-31
Can this be done with Tilda? I was able to install and run it successfully on Hardy, but like you were I'm looking for true transparency to free up some visual space on my desktop while running terminal. The only reason I'm asking is that Tilda is in Synaptic and YeahConsole seems to be run by an independent programmer who doesn't seem intent on supporting or updating it (only a bit worried about bugs 'n such b/c of the YeahConsole webpage). Thanks

Oh also, I just tried this and I'm not using Compiz with Hardy 8.04 on a Dell XPSM1210 and nVidia chipset. It isn't working for me, which might be the lack of compiz. I also don't have a lot of experience yet modifying system elements with scripts etc so I don't quite follow what the script is doing well enough to modify it. Any suggestions would be appreciated.

---

### Post by hopla on 2009-02-01
> **0bsidian said:**
> Can this be done with Tilda?
If I remember correctly, Tilda has a setting for this (right click on the Tilda window, you will find a 'Settings' item or some such in the context menu).

Tilda has more features (but is a bit buggy) than YeahConsole and I would still be using it if it didn't start crashing since I updated to Intrepid.

> I was able to install and run it successfully on Hardy, but like you were I'm looking for true transparency to free up some visual space on my desktop while running terminal.

If it runs, then it's only a matter of configuring it and your done I think :)

> 
 The only reason I'm asking is that Tilda is in Synaptic and YeahConsole seems to be run by an independent programmer who doesn't seem intent on supporting or updating it (only a bit worried about bugs 'n such b/c of the YeahConsole webpage). Thanks
YeahConsole is in Synaptic too, at least on Intrepid.

> 
Oh also, I just tried this and I'm not using Compiz with Hardy 8.04 on a Dell XPSM1210 and nVidia chipset. It isn't working for me, which might be the lack of compiz. I also don't have a lot of experience yet modifying system elements with scripts etc so I don't quite follow what the script is doing well enough to modify it. Any suggestions would be appreciated.

Try the Tilda transparency settings first, I don't think you need Compiz for that.

---

### Post by 0bsidian on 2009-02-01
I was able to get the true transparency working (even with just gnome) as there is a setting in the appearances manager that allows you to choose one of three levels of visual affects. If the moderate or high level effects are selected then transparency works. However, I'm still unable to find anything that says how to control more specific settings. I'm assuming that there must be some conf files somewhere that determine all of these things (xprop for example, although I can't find the transparency parameter in mine). I want to keep everything in low graphics mode for optimal performance EXCEPT for hte transparent terminal. Any ideas?

---

### Post by afrodeity on 2011-08-01
I love yeahconsole. The only thing which bothers me is not being able to scroll, so for example if I run weechat-curses and print a help menu /help, i can't see all the options. Any idea how to rectify?

UPDATE: Okay silly me, this was just a weechat issue. Pgup and Pgdown keys do the trick. Weird.

---

