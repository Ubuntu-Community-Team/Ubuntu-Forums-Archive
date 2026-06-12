---
title: "Gnome volume control dissapeared!"
date: 2010-08-17
forum: Desktop Environments
---

### Post by wkulecz on 2010-08-17
The master volume control on my wife's computer (Ubuntu 10.04) has disappeared from the main menu.  I can't figure out how to get it back.

What process supplies this?  I've no idea where to look.  Various "mixer" controls all seem to work but none put back the quick access master volume control back on the Gnome menubar.

---

### Post by SantaFe on 2010-08-17
Have you tried right clicking on a Panel, choosing Add To Panel, and when the Add To Panel box pops up, click on Indicator Applet, then click the Add button at the bottom?

---

### Post by randywilharm on 2010-08-17
This is a bug in 10.04 Lucid....

Enter in terminal:

pkill gnome-panel



this will reset gnome
and you should get the control back

---

### Post by wkulecz on 2010-08-19
Thanks for the replies, I'll try them on my wife's computer tonight or tomorrow and get back about it.

I tried the "Add To Panel" thing initially but was stopped dead in my tracks by not having a clue as to the name of the thing I needed to add, but I don't think the indicator application is the volume control as my wife's computer still is getting notifications of updates available.

---

### Post by Spice Weasel on 2010-08-19
Have you tried installing "gnome-alsamixer"? It's an alternative to the default with more options.

---

### Post by wkulecz on 2010-08-20
> Have you tried installing "gnome-alsamixer"? It's an alternative to the default with more options

No.  This is my wife's computer, somehow something she did killed the volume control application.  I want to put it back to what it was.  Adding more options or making it different is not really helpful.

I can launch any of the other mixer applications and they all seem to work, as does the volume control in System->Preferences->Sound, but none of this is as convienent for my wife as was the default master volume control on the Gnome panel.

I'll look into what has been suggested this weekend.

---

### Post by karmila on 2010-08-20
I got the same problem as yours.

I added "gnome-volume-control' command to startup application and it gave me volume control slider at the gnome-panel but not the same as before, it lost sound preference option.

I've tried to restart the panel with pkill gnome-panel but nothing change. I even restored the panel to the default but the volume control still missing. As I remember, i didn't do anything that possibly make the control missing, it just lost.

---

### Post by JohnElway on 2010-08-20
To reload the GNOME panel I usually use this command:

```
killall gnome-panel
```

It's always worked for me.

---

### Post by wkulecz on 2010-08-22
Add to Panel -> Indicator Applet brought it back.  Its also bring in the Email/Chat icon which I suspect she might have deleted, not realizing the Volume Control was tied to it.

Thanks!

---

### Post by MakOwner on 2010-08-23
> **JohnElway said:**
> To reload the GNOME panel I usually use this command:

```
killall gnome-panel
```

It's always worked for me.

I have the same issue, and restarting the panel doesn't work for me either.
I know I haven't deleted anything from the panel - this is my desktop.

---

### Post by karmila on 2010-08-31
> **MakOwner said:**
> I have the same issue, and restarting the panel doesn't work for me either.
I know I haven't deleted anything from the panel - this is my desktop.

My problem still unsolved either, yes I do nothing too that might delete the applet. It just disappeared!

---

### Post by karmila on 2010-09-01
Now, my problem is solved!

I don't know why but I needed to install indicator-sound first (don't know why it's missing..?)
```
sudo aptitude install indicator-sound
```
And then add indicator applet to the panel (before I installed indicator-sound, it's only added mail notification but no volume control)

---

