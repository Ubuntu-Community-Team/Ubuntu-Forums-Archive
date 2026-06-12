---
title: "Why does copy paste suck so bad in Ubuntu and some other things?"
date: 2011-03-24
forum: Desktop Environments
---

### Post by inckiekage on 2011-03-24
I recently switch from Windows 7 to Ubuntu, because in Windows, I have bad graphical errors (looks like hardware errors, but it doesn't happen in Ubuntu).

BUT Why is copy/paste functions SO bugged, this is something you just expect to work? 

Sometime I cannot copy/paste between different windows and programs (including Firefox, gedit and so on) and I have to restart the machine in order to get copy/pasting working again.

at work, I'm using a docking station, and there for I have different screen resolutions, but EVERY time I dock my computer, in the morning, the first thing I have to do, is to rearrange, my applets because they are kinda placed randomly at my panels.

flash in fullscreen seems also to be very bugged, some times the screen just freezes, and when I use my sound control buttons on my laptop, the image freezes too, and i have to exit fullscreen and enable it again.

I think it's because of all these small things that simply just doesn't work or is bugged for some people, and that many programs just have a very awful look, that Linux is not that of a great success on the desktop.

and I really miss the behavior from PuTTY @ Windows where you can just mark text, and it is in your clipboard, is there any way, to enable same behavior in the terminal in Ubuntu?

But everything doesn't have to be errors, I like to tell that I LOVE that I don't have to wait 5-10 minutes before I can use my computer, when I cold boot it. GPMC / mpd is also lovely and I can tell you that HPLib makes it easier to install a printer in Linux and take less of a time than on Windows using their own Windows drivers :P

---

### Post by slackthumbz on 2011-03-24
> **inckiekage said:**
> I recently switch from Windows 7 to Ubuntu, because in Windows, I have bad graphical errors (looks like hardware errors, but it doesn't happen in Ubuntu).

BUT Why is copy/paste functions SO bugged, this is something you just expect to work? 

Sometime I cannot copy/paste between different windows and programs (including Firefox, gedit and so on) and I have to restart the machine in order to get copy/pasting working again.

at work, I'm using a docking station, and there for I have different screen resolutions, but EVERY time I dock my computer, in the morning, the first thing I have to do, is to rearrange, my applets because they are kinda placed randomly at my panels.

flash in fullscreen seems also to be very bugged, some times the screen just freezes, and when I use my sound control buttons on my laptop, the image freezes too, and i have to exit fullscreen and enable it again.

I think it's because of all these small things that simply just doesn't work or is bugged for some people, and that many programs just have a very awful look, that Linux is not that of a great success on the desktop.

and I really miss the behavior from PuTTY @ Windows where you can just mark text, and it is in your clipboard, is there any way, to enable same behavior in the terminal in Ubuntu?

But everything doesn't have to be errors, I like to tell that I LOVE that I don't have to wait 5-10 minutes before I can use my computer, when I cold boot it. GPMC / mpd is also lovely and I can tell you that HPLib makes it easier to install a printer in Linux and take less of a time than on Windows using their own Windows drivers :P

Umm, you do know that you can just select text with your mouse and then middle click to paste it right?

---

### Post by Elfy on 2011-03-24
> ...to rearrange, my applets because they are kinda placed randomly at my panels...Try locking the panel

Alt+F2
gconf-editor

Navigate to apps>panel>global

got to the locked_down key and enable it.

---

### Post by mcduck on 2011-03-24
> **inckiekage said:**
> 
and I really miss the behavior from PuTTY @ Windows where you can just mark text, and it is in your clipboard, is there any way, to enable same behavior in the terminal in Ubuntu?


This already works in every Linux application, the only difference is that it's a separate method from copy/paste, and doesn't use a clipboard (so it only copies stuff directly from one place to another, without storing it in clipboard in between).

Just highlight any text anywhere, and middle-click where you want to paste it.

What comes to your other copypaste, are you perhaps closing the program where you are copying from before you paste? That would explain your issues. If you want to be able to do that you should install some clipbaord manager...

---

### Post by inckiekage on 2011-03-24
> **forestpiskie said:**
> Try locking the panel

Alt+F2
gconf-editor

Navigate to apps>panel>global

got to the locked_down key and enable it.
been there, done that ;-), dont work.


[QUOTE=slackthumbz]Umm, you do know that you can just select text with your mouse and then middle click to paste it right? [/QUOTE]
Yep, I know that, but since there is no middle button on my laptop, iIhave to press left/right click at the same time, not a very good key combo IMO.

I just miss the mark text, to get it in clipboard, and ctrl+v to insert or right click in putty. i works really well, and im used to it.

---

### Post by tgalati4 on 2011-03-24
There are also several helper copy/paste apps that get around the limitations that you have mentioned.

GNU/Linux is not perfect.

But I use it.

---

### Post by Zzl1xndd on 2011-03-24
> **tgalati4 said:**
> There are also several helper copy/paste apps that get around the limitations that you have mentioned.

GNU/Linux is not perfect.

But I use it.

+1 Glipper is the app I use makes up for all the complaints I had about copy/paste.

---

### Post by inckiekage on 2011-03-24
> **tgalati4 said:**
> There are also several helper copy/paste apps that get around the limitations that you have mentioned.

GNU/Linux is not perfect.

But I use it.

I know, either is Windows, OSX or any other operating systems, take this as feedback

---

### Post by ajgreeny on 2011-03-24
I use parcellite for my clipboard manager, which I began to use a long time ago when glipper had lots of bugs, and would keep crashing.

Parcellite lets you choose if you want to use just the standard Ctrl+C for copy, or Ctrl+C and Primary (selected text).  I find using the two together far to difficult to manage, as it puts too much junk in the clipboard manager, particularly if you select text a lot, but I do make enormous use of the "select and middle click to paste" option, which never appeared in the versions of windows I used, or if it did, I never knew about it.

---

### Post by racie on 2011-03-24
> **inckiekage said:**
> flash in fullscreen seems also to be very bugged, some times the screen just freezes, and when I use my sound control buttons on my laptop, the image freezes too, and i have to exit fullscreen and enable it again.

Ahh!  I think I can help you!  I had a similar problem where flash would freeze in full screen.  At first I thought it was my video card, but I realized that other types of videos in full screen worked just fine.  Anyway, enough of my rambling... the solution was found by someone [here](http://www.noobrescue.com/blog/flash-fullscreen-doesnt-work-on-ubuntu-10-10).

```
sudo mkdir /etc/adobe 
sudo su 
sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg
```

---

### Post by inckiekage on 2011-03-25
> **racie said:**
> Ahh!  I think I can help you!  I had a similar problem where flash would freeze in full screen.  At first I thought it was my video card, but I realized that other types of videos in full screen worked just fine.  Anyway, enough of my rambling... the solution was found by someone [here](http://www.noobrescue.com/blog/flash-fullscreen-doesnt-work-on-ubuntu-10-10).

```
sudo mkdir /etc/adobe 
sudo su 
sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg
```

love you :)

[QUOTE=ajgreeny] I use parcellite for my clipboard manager, which I began to use a long time ago when glipper had lots of bugs, and would keep crashing.

Parcellite lets you choose if you want to use just the standard Ctrl+C for copy, or Ctrl+C and Primary (selected text). I find using the two together far to difficult to manage, as it puts too much junk in the clipboard manager, particularly if you select text a lot, but I do make enormous use of the "select and middle click to paste" option, which never appeared in the versions of windows I used, or if it did, I never knew about it.[/QUOTE]

thx for the tip, i will evaluate it, the see if this fixes my ctrl+c/ctrl+v issues

---

### Post by VanillaMozilla on 2011-03-25
Look at the Edit menus for the two applications.  That will show the shortcuts for Copy and Paste.  It's usually <ctrl>c and <ctrl>v, but not always.

Sometimes the shortcut must be different if the application uses the ^C and ^V for something else.  For example, ^C in terminal applications has a different use that predates windowing computer systems.

Hey, but thanks for the middle click trick.  I didn't know that.

---

### Post by inckiekage on 2011-03-26
isn't it posebil to remap the middle mouse to ctrl+v?

i think that will fix my issues.

then i only have to mark text and paste with ctrl+v

---

### Post by ajgreeny on 2011-03-26
But if you use parcellite, and choose to use both the primary selection and Ctrl+C for copy, both a midle click and Ctrl+V will work to paste the copied data.

That middle click to paste a selection is one of the most useful ways of copying that I know of in any OS.  I don't think it is even available in windows as an option.

---

### Post by inckiekage on 2011-03-27
> **ajgreeny said:**
> But if you use parcellite, and choose to use both the primary selection and Ctrl+C for copy, both a midle click and Ctrl+V will work to paste the copied data.

That middle click to paste a selection is one of the most useful ways of copying that I know of in any OS.  I don't think it is even available in windows as an option.

I disagree with when using a laptop with no middle button, so you have to use left/right click at the same time, on my laptop I has to put my hand/hands in an awkward position.

most of the time my hands are placed near ctrl and v

---

### Post by mcduck on 2011-03-27
> **inckiekage said:**
> I disagree with when using a laptop with no middle button, so you have to use left/right click at the same time, on my laptop I has to put my hand/hands in an awkward position.

most of the time my hands are placed near ctrl and v

If your laptop's touchpad has multi-touch capabilities then a three-finger tap works as a middle click.

---

### Post by ajgreeny on 2011-03-29
> **inckiekage said:**
> I disagree with when using a laptop with no middle button, so you have to use left/right click at the same time, on my laptop I has to put my hand/hands in an awkward position.

most of the time my hands are placed near ctrl and v
Yes, I agree about that, but I seldom use a laptop, and when I do, I am always baffled by the awkwardness of a touchpad vs a mouse with, in my case 5 buttons, which is so good it is almost unbelievable.

I realise that a touchpad is essential for a laptop, but I just can not get on with them, as so many mouse options that I use and *need* are missing.

---

