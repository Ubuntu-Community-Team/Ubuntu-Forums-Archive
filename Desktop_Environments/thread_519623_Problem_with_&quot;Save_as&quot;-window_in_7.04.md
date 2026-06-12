---
title: "Problem with &quot;Save as&quot;-window in 7.04"
date: 2007-08-07
forum: Desktop Environments
---

### Post by dk@ on 2007-08-07
Hello!

I have small problem with my 7.04 and I think that it is Gnome problem.

When I try to "save as" document in Open Office, I get following window: 
[IMG]http://lh5.google.com/kadantsev.d/RrhqFTZP39I/AAAAAAAAAoE/FP1ByHIQtVo/s144/Screenshot_oo22_dk.jpg[/IMG] [Link to big picture]("http://picasaweb.google.com/kadantsev.d/Temp/photo#5095939617707778002")

As you see, there is just two lines for "Places" an list of folders. The problem is that I can't resize this window to view more than 2 lines. Work with just 2 lines is uncomfortable.

But the same window in gedit is possible to resize and to see more than 2 lines! How to repair it?

In addition, my friend has a little bit different "save as"-window: 
[IMG]http://lh5.google.com/kadantsev.d/RrhqFTZP3-I/AAAAAAAAAoM/T17j1cQYhMo/s144/screen_oo22.jpg[/IMG] [Link to big picture]("http://picasaweb.google.com/kadantsev.d/Temp/photo#5095939617707778018")

Actually, I find it more useful then mine. My friend works also under Gnome. Why this window is different?

Thanks!

---

### Post by FuturePilot on 2007-08-07
Have you tried moving your mouse to the edge of the window until you see the resize arrow and then resize it that way?

---

### Post by dk@ on 2007-08-07
2FuturePilot
Yes, of course. I can resize "save as"-window in gedit exacly this way.

---

### Post by weblordpepe on 2007-08-07
I have this same problem. Its a pain in the *BEEP*
I am running 1680x1050 resolution. Hi-res, I know. Yes, widescreen too.

....mm..

what were we talking about? Oh yeah the dialogue box. Yeah its irritating.


EDIT:
[http://picasaweb.google.com/kadantsev.d/Fun/photo#5090490536864767890](http://picasaweb.google.com/kadantsev.d/Fun/photo#5090490536864767890) hehehe

---

### Post by FuturePilot on 2007-08-07
Hmmm. It worked for me when I just resized the entire window.:confused: Sorry, I don't know what else it could be.:(

---

### Post by RedSquirrel on 2007-08-07
1/
Using the default dialog:

Try left-clicking in the Locations area then press and hold Alt key while right-clicking... you can drag to make the Save As dialog the size you prefer. This definitely works in Fluxbox; not sure about other window managers.

EDIT: 

- I just reread the thread and I see that *you* are able to resize the dialog by clicking on its edge and dragging, so you don't need this Alt-right-click trick. ;)

- sometimes (not always) if you click "Browse for other folders" it will resize to something more reasonable. You might have to click it a couple of times.

- small note for Fluxbox users: I made an entry in my keys file to resize the the Save As dialog when I press Ctrl-Alt-s...

```
Control Mod1 s  :MacroCmd {MoveTo 100 100}  {ResizeTo 800 750}
```

2/
You can change the look of the Open/Save As dialog for Open Office:

Click: **Tools -> Options -> OpenOffice.org -> General **

There is a setting for Open/Save As dialogs there.

Screenshot...

---

### Post by dk@ on 2007-08-08
2RedSquirrel

> I just reread the thread and I see that you are able to resize the dialog by clicking on its edge and dragging, so you don't need this Alt-right-click trick.
Yes, but not in OO's "save as"-dialog.

> sometimes (not always) if you click "Browse for other folders" it will resize to something more reasonable. You might have to click it a couple of times.

Wow!!! It's alive! :D

> You can change the look of the Open/Save As dialog for Open Office...
Thanks, I'll try it this evening.

---

### Post by callan79 on 2007-08-08
> **dk@ said:**
> 2RedSquirrel
Yes, but not in OO's "save as"-dialog.
Wow!!! It's alive! :D
Thanks, I'll try it this evening.

You know, I've found the same thing, the SAVE as dialogs from different programs show up differently, and the one from open office is just like dk@ says, really small and annoying.

I don't know any fix, I haven't bothered looking, but thought I'd comment that mine seems pretty random too.

Cheers,
Callan

---

### Post by RedSquirrel on 2007-08-08
I have read that there have been some improvements to GTK that relate to this sort of thing. I think the version that is included in gutsy is supposed to fix some of these problems. I haven't switched to gutsy yet so I don't know from personal experience whether the issue has been addressed... it will be interesting to see how well it performs.

---

### Post by richtard on 2007-08-17
The save as dialog for most programs that I use in Ubuntu 7.04 seems to be this way-> very little room for file structure information  (despite being quite a large dialog box).. They are next to useless in their present form. Yes I can resize them, but I don't want to resize them EVERY time I try to save something. 

Does anyone know of a way to resize  the "save as" dialog universally and permanently?

Cheers for any help anyone can give me.

---

