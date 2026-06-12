---
title: "Compiz Edge Fliping. Conrner only?"
date: 2010-08-13
forum: Desktop Environments
---

### Post by TyLLy_4 on 2010-08-13
Hi all ... 
This is driving me crazy. Compiz works like a charm when i set the whole right or left edge to flip y desktop wall. However  thats quite annoying because it flips when i try to close a window or use the scrollbar. 

I used to have this configured where it would only flip on the bottom corner. however i had to reinstall die to sound issues and now i cant make it happen. 

The second i switch right, to bottom right it stops working. 

I have tried with both CCSM and simple config settings manager (see SS)

Can you guys help me get this working?

Thanks in advance .... 
(the Ubuntu community rocks)

---

### Post by TyLLy_4 on 2010-08-13
please?

---

### Post by TyLLy_4 on 2010-08-14
really ubuntuforums? 

No one is going to reply? 

:( :( :( :(

---

### Post by varunendra on 2010-08-15
> **TyLLy_4 said:**
> really ubuntuforums? 

No one is going to reply? 

:( :( :( :(

Maybe it is because you've answered the question partially by yourself (reinstalling die causing a conflict!!??) and compiz settings may get very tricky sometimes in case of conflicts.

Sorry for no-useful comment rather than a help, but since you've already tried ccsm & simple-ccsm, I can only suggest either setting (in compiz) everything to default then resetting as you like, or even better- just uninstall the whole compiz package+CCSM, disable ultra visual effects & reinstall them. (You won't have to download them again if their .deb packages are still in /var/cache/apt/archives folder.)

---

### Post by TyLLy_4 on 2010-08-15
Reinstalling didn't cause the problem. the problem is that i had to do a clean install of Ubuntu and after doing so i couldn't do configure corner flip again. 

I will uninstall everything and reinstall it.... 

thanks for posting.



Edit: Didn't work also i noticed that it does not work for rotate cube neither.

---

### Post by varunendra on 2010-08-16
> **TyLLy_4 said:**
> however i had to reinstall [COLOR=Red]**die**[/COLOR] to sound issues and now i cant make it happen.

Gotcha....! So it was a typo that got me confused (die or due?;)).

Have you tried Ubuntu Studio + Compiz? I think (for no explainable reason ;)) that is more suitable for compiz effects.

Can you post a list of all the effects that you have enabled with compiz? Also, while trying to enable rotate cube, do you get any error message?

As you can see in my profile, I'm using Ubuntu Studio 9.10, but I've disabled all the effects months ago to gain performance. However, based on your description, I may try the same on a live flash installation. (Compiz or any visual effects don't work on VMware :()

Are other effects working fine? (wobble, water, burn, fade, etc.).

---

### Post by TyLLy_4 on 2010-08-16
I had no Idea that Ubuntu studio existed. Looks perfect for me! however i don't want to perform an install and loose all my apps and what now (burned ISO ... will do on next install) 

The edge flip effect works fine with both desktop wall and desktop cube (witch i don't use for performance issues like you mentioned) however it's quite annoying as it only enables you to use the whole side of your desktop as a trigger to switch to the next desktop. 

In my old install (yes i did mean DUE to a reinstall) this worked with the bottom corner of the screen only. This its what im trying to enable :( 


Enabled Plug ins are: 
Desktop Wall
Bicubic Filter
Blur Windows
Fading Windows
Window Decorations
Wobbly Windows
Window Previews
Image Loading (all Extensions)
dbus
Inotify
Glib
Mouse Position Polling
Regex Matching
Resize Info
Scale Addons
Session Management
Workarounds
Extra WM Actions
Move Windows
Place Windows
Resize Windows
Ring Switcher
Scale
Snapping Windows

---

### Post by TyLLy_4 on 2010-08-16
I was trying to post my compiz settings .... but i cant find the file ... 
when i go to ~/.config/compiz/compizconfig/ all i see is a small config file wich only has this: 
```
[gnome_session]
profile = Default
plugin_list_autosort = true
```

---

### Post by varunendra on 2010-08-17
Okay, I've just installed Lucid on a flash drive & CCSM, simple CCSM on it. Enabled whatever you listed with two issues:

[LIST=1]
[*]Couldn't find 'Bicubic Filter'
[*]Snapping Windows has a conflict (Edge Resistance) with Wobbly windows, so didn't enable (Wobbly windows is enabled).
[/LIST]
Now, for the flip windows effect in desktop wall, I've set it so that when I click at the bottom right corner of the screen, it switches to the next desktop.

Step 1:
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/Screenshot-1.jpg[/IMG]

Step 2:
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/Screenshot-2.jpg[/IMG]

Step 3:
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/Screenshot-3.jpg[/IMG]

Step 4:
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/Screenshot-4.jpg[/IMG]


Is that what you want? If not, then please post in detail the action and its effect that you want.

---

### Post by TyLLy_4 on 2010-08-17
Your my new favorite person in the world! 

Thank you so very much! 

Also i discovered something weird (do you think its a bug that should be reported) 

The setting I was trying to enable was actually edge fliping (where the screen flips without you having to click anything) but when i enabled the "move within wall" settings like you suggested (where im actually supposed to click on the corner to make it flip) it works the way I wanted it to.

So i guess in order to have edge flip I needed to enable move within wall. Should i report this? 

Thanks A lot again this is precisely why i love ubuntu

---

### Post by varunendra on 2010-08-17
> **TyLLy_4 said:**
> Your my new favorite person in the world! 

Thank you so very much!
Hmm.... Nevermind! Here's a challenge for you:

**_Challenge_: **Find me a new & better complement, because (I think) I've found what you were originally looking for:> **TyLLy_4 said:**
> The setting I was trying to enable was actually edge fliping (where the screen flips without you having to click anything)
To do so, just follow the new screenshots:
Step 1:
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/Screenshot-1-1.jpg[/IMG]

Step 2: 
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/Screenshot-2-1.jpg[/IMG]

Step 3: 
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/Screenshot-3-1.jpg[/IMG]

Step 4: Click OK and close the boxes. You may (or may not) wish to change the default settings related with other flip options. Just repeat the same steps (selecting different corners/edges).

I'm eagerly waiting for my Nobel Prize!!:cool:

> **TyLLy_4 said:**
> Thanks A lot again...... that won't do,..... I want my Nobel prize......[-(


[:lol: Nevermind really, I do these things out of interest, & it was quite a fun solving the puzzle :lol: For a while I was like in my initial computer learning days..:popcorn:]

---

### Post by TyLLy_4 on 2011-02-21
LOOOL I just stumbled unpon this old post while googling for how to do this again.

I handt seen your last post. 

You sir are a gentleman and a scholar 

[IMG]http://www.quintessentialpublications.com/tracyrtwyman/wp-content/uploads/2010/03/You-Win-an-Internet.jpg[/IMG]


Gimme ur addres via PM and ill send u somthing nice XD

---

### Post by varunendra on 2011-03-15
Thanks buddy!
I think you've already overloaded me with your complements.. Won't be able to handle anything more. :)

Enjoy!

---

### Post by TyLLy_4 on 2011-03-15
In the end I realized that the cube plug in doesn't seem to have this issue. and its much easier to setup. (plus you get 4 screens instead of 4 .... i need a lot of room to hide all my open porn windows at work :lolflag::lolflag::lolflag:)

anyways .... the bug seems to be caused by having both simple config compiz and config compiz installed at the same time and on use. 

DUHHHHHHHHHHH

corrected the issue by uninstalling, reseting, uninstalling reseting installing again and redoing config from scratch .....

---

### Post by varunendra on 2011-03-15
Um.... well, I had both installed when I tried what I suggested. So at least on that version, there wasn't any issue at all! The only thing I needed was to know where the settings were..

---

