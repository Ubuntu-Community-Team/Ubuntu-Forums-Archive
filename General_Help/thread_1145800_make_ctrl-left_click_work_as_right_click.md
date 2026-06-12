---
title: "make ctrl-left click work as right click?"
date: 2009-05-02
forum: General Help
---

### Post by slugicide on 2009-05-02
My friend's laptop has a broken right button on the trackpad, making it near impossible to access the right-click menu. Is there a way for her to make a shortcut so that something like CTRL-Left-Click will act as a Right-Click? Thanks!

---

### Post by slugicide on 2009-05-02
bump

---

### Post by Brandon Williams on 2009-05-02
This seems like something that xmodmap ought to be able to do, but I can't see any way to accomplish it in the xmodmap man page. If it's possible to do, maybe this suggestion will jog someone else's memory.

Sorry I can't be more help.

---

### Post by BslBryan on 2009-05-02
> **Brandon Williams said:**
> If it's possible to do, maybe this suggestion will jog someone else's memory.

Actually, it did!  :-)

Add this to /etc/rc.local (Places --> Computer --> Filesystem --> etc --> Ctrl + H --> then, open up your text editor (since right click isn't working yet) and drag rc.local to the text editor.  Sorry for the explanation if you know what you're doing, but I didn't want to take any chances. :P)

Then add, 
```
#makes right cmd right click
xmodmap -e 'keycode 116 = whatever you want'
```

Also, tapping 3 times on a touchpad is the same thing as right clicking.

---

### Post by Brandon Williams on 2009-05-02
Yes, that will set the right-hand control key to act like right mouse button. Is there a way with xmodmap to remap Ctrl+<left mouse button> so it acts like the right mouse button? I couldn't figure out a way to specify a mouse button for the keycode command.

Also, your mention of the triple-tap reminded me of something ... triple-tap doesn't work for me, but I know that synamptics touchpad can be configured to treat a two-fingered tap as a right-click. Look [here](https://help.ubuntu.com/community/SynapticsTouchpad) for more information about advanced touchpad configuration.

The final though I have is that under mouse accessibility settings, you can select to have a long left click be treated as a right click.

---

### Post by BslBryan on 2009-05-02
Well, you would use "Pointer_Button1" for a click... 

I'm not sure that Button1 is left click, though.

Also, keycode 129 is CTRL, if that helps any.

---

### Post by Brandon Williams on 2009-05-02
It occurred to me that users of MacBooks must have a solution for this. One thing I see mention of for them is a program called mouseemu. I've never tried it, but it seems worth a look.

---

### Post by aextance on 2009-05-04
Are you sure your friend's right click has stopped working because of a physical problem with the machine? I've had something very similar with left click following the upgrade to Jaunty. It still works in Intrepid, so I'm running both on different partitions at the moment, which I find very irritating. 

Could someone tell me *specifically* what I need to do to make something like the right shift key on my machine work as left click? It doesn't look too hard, but I've been messing around so much on this that it's really affected my work, so I'd like to get someone who knows to tell me how to do it rather than stumbly around blindly any more.

---

### Post by Brandon Williams on 2009-05-04
[This forum post](http://ubuntuforums.org/showpost.php?p=5801976) has a specific suggestion for how to map a keyboard key to right-click.

---

### Post by aextance on 2009-05-04
Thanks for that! Oddly enough I couldn't get the script procedure to work. Do you think the location and filename are important? I was assuming not, as long as I made it executable with the chmod a+x command. I started off putting the file somewhere else with a different name, and then put it in the same location as in the thread you linked to but it didn't work either time. The script looks like it's executing in the terminal, but doesn't complete. 

Elsewhere in the thread there was a single command that did the trick in terminal before I tried using the script with exactly the same name and location. Interestingly enough my regular left click also started working again at the same time. However, I've now repeated it and neither my original left mouse and the new key - right shift - I assigned won't do anything. The shift won't even shift!

Back to Intrepid again!

---

### Post by Brandon Williams on 2009-05-04
At some point in the procedure your left mouse button started working again? Maybe all you need is 'xkbset m'. It shouldn't be required, but that is the most likely of the two changes to have led to the mouse button working again.

As for the script ... it should run from anywhere. That said, I wouldn't put it in /usr/local/bin/ myself unless it's a multi-user system and everyone needs it. If it's just you, then I would put it in your $HOME/bin/ (making that directory, if necessary). Then, I would add a new entry to the list of 'Startup Applications' (I think that's what it's called; I'm not on an Ubuntu box at the moment) to run my script at login.

---

### Post by BslBryan on 2009-05-04
> **Brandon Williams said:**
> At some point in the procedure your left mouse button started working again? Maybe all you need is 'xkbset m'. It shouldn't be required, but that is the most likely of the two changes to have led to the mouse button working again.

As for the script ... it should run from anywhere. That said, I wouldn't put it in /usr/local/bin/ myself unless it's a multi-user system and everyone needs it. If it's just you, then I would put it in your $HOME/bin/ (making that directory, if necessary). Then, I would add a new entry to the list of 'Startup Applications' (I think that's what it's called; I'm not on an Ubuntu box at the moment) to run my script at login.

+1, sounds good.  aextance, keep us posted?

---

### Post by Brandon Williams on 2009-05-04
I just got home to me Jaunty machine and tested the commands from the post that I suggested.

```
$ xmodmap -e 'keycode 62 = Pointer_Button3'
$ xkbset m
```

After running those two commands, my right shift key reliably works as if it were the right mouse button. If those two commands to not have the same effect for you, then I agree that there must be something more confusing going on here, probably with the mouse driver, I would guess.

---

### Post by aextance on 2009-05-05
Yeah, that's what I did, except with pointer button 1. As with a lot of the fixes I've tried, it worked once and then not again. Thanks for your help though.

Actually, I read that we're supposed to be using hal now for our mouse stuff rather than xorg.conf. Could that be playing a part here?

---

### Post by aextance on 2009-05-19
It turns out it was my touchpad dying, I think. I am using Jaunty successfully for everything now having turned it off. 

I got a clue when, having gone back to Intrepid, after about 10 days of correct mouse usage I started getting random left clicks all over the place. I guessed it was probably the touchpad, and sure enough when I turned it off my trackpoint and buttons worked just fine. 

Switching across to Jaunty and turning off the touchpad solved my problem there, and I'm even confident enough to be using it as the sole OS. 

It's still odd that there was a difference between the two versions of Ubuntu, however. I also think I had an inkling that this was going on before, as when I turned on the computer in either OS it often initially brought up drag-boxes. That and the fact that I could make other left click options work temporarily did make me wonder if the trackpad was acting as if it was holding down left click all the time. I thought I'd investigated it, but if I did it clearly wasn't very thoroughly. 

Thanks for all your help.

---

