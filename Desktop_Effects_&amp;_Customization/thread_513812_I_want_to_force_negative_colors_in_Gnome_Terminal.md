---
title: "I want to force negative colors in Gnome Terminal"
date: 2007-07-30
forum: Desktop Effects &amp; Customization
---

### Post by rburks on 2007-07-30
Hi all.  I've installed Compiz-Fusion in Feisty and it's great, even coming from Beryl and Compiz before that.  But one thing I would like to do is have my Terminal windows use the Negative plug-in by default, so I don't have to do the Super+N action every time I open a Terminal.

I've seen screens of Terminal being negative and/or transparent.  In Beryl I was able to make Terminal windows semi-transparent but I forget how I did it.  I think it was by telling the plug-in to match a Type or a Title that always made Terminal use my transparency.

I just can't seem to get it working with Negative in compiz-fusion.  Maybe these screen shots are of people using a different Terminal than the default Gnome Terminal.

Thanks for your help and opinions . . . !

Rob

---

### Post by rburks on 2007-07-30
Ok I figured it out and yes I feel like a dumbass.  But I'll post what I did just in case it helps someone else.  I looked around a bit harder in some of the other plug-ins and found in Animations the name= match.  Doh!! Then I had to find out how to launch a terminal in the command line, and after a few tries and looking back at the animation plug-in (name=gnome-screensaver):

I went to the Negative plug-in and put this in the 'Neg Windows' value:

name=gnome-terminal

Simple when you know the format.  Oh well I can go to bed now.

:popcorn:

---

### Post by Sqwishy on 2007-07-30
You don't need to use compiz/beryl to make to change the colours.

Open the terminal >> right click >> edit current profile
Click onColors tab >> Uncheck the first box (User colors from system theme) >> And click on the 2nd part and choose white on black (or another one you want) from the list
Click on Effects tab >> Transparent Background >> Change the slider

Good luck

---

### Post by bubba2120 on 2007-07-31
yeah thats what i did to change the colors. i made mine black with white text to look like the command prompt in windows, :)

---

