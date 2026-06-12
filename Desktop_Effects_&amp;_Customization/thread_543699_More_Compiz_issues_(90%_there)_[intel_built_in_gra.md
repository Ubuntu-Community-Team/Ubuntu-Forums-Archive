---
title: "More Compiz issues (90% there) [intel built in graphics]"
date: 2007-09-05
forum: Desktop Effects &amp; Customization
---

### Post by vic318ic on 2007-09-05
Hi there, Ive been scouring the threads looking for someone who's had similar issues as i've been experiencing.  It took me a few tries to get compiz quasi working, but i'm not 100% there yet.  

Couple issues off the bat that i'd like to get fixed:

1.) when i first log in and bring up my terminal to start compiz via:  compiz --replace.  The command window stays open, but doesnt return to a prompt.  This is the output i'm getting: 

```
rizla@rizladk:~$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: not present. 
Checking for Xgl: not present. 

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

```


What is this unhandled action type warning that keeps popping up?  Also, why is  this 
stray error showing up:

[b](gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
[/b] 


issue #2:

Cube doesnt rotate.  Do y ou need to have dual monitors to see 4 sides?  I currently only have 1 physical monitor with two desktops.  When i have it set to edge flip, it just flips to my second desktop.  I want that cool 3d cube zoom out rotation effect.  its not a REAL big issue, but i'm curious to know why its not working.

My rain and wiper dont work when i press shift+F8.

issue #3:
when I start emerald via; emerald --replace.  It screws up my windows and i lose my title bars and they get locked.  I have to restart gtk-window-manager in order to get it to show up.

Those are my main sticking points, other than that the expose works like a charm, alt tabbing works like it should.  All the basics are good.  

Can someone please help me trouble shoot those pesky errors please?  I know its redundant..  BTW, i have an integrated Intel graphics card on a Dell Optiplex G620if that helps

---

### Post by vic318ic on 2007-09-05
One quick follow up.  Is there a plugin for compiz that breaks out all your open apps onto the screen so you can see them all in a tiled view and mouse over the one you want?  I just wnat to play around to compare whether i like the expose flip tab or an exploded view of your open aps.  thanks.

---

### Post by dondad on 2007-09-05
> **vic318ic said:**
> Hi there, Ive been scouring the threads looking for someone who's had similar issues as i've been experiencing.  It took me a few tries to get compiz quasi working, but i'm not 100% there yet.  

Couple issues off the bat that i'd like to get fixed:

1.) when i first log in and bring up my terminal to start compiz via:  compiz --replace.  The command window stays open, but doesnt return to a prompt.  This is the output i'm getting: 

```
rizla@rizladk:~$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: not present. 
Checking for Xgl: not present. 

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)

```


What is this unhandled action type warning that keeps popping up?  Also, why is  this 
stray error showing up:

[b](gtk-window-decorator:8012): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
[/b] 


issue #2:

Cube doesnt rotate.  Do y ou need to have dual monitors to see 4 sides?  I currently only have 1 physical monitor with two desktops.  When i have it set to edge flip, it just flips to my second desktop.  I want that cool 3d cube zoom out rotation effect.  its not a REAL big issue, but i'm curious to know why its not working.

My rain and wiper dont work when i press shift+F8.

issue #3:
when I start emerald via; emerald --replace.  It screws up my windows and i lose my title bars and they get locked.  I have to restart gtk-window-manager in order to get it to show up.

Those are my main sticking points, other than that the expose works like a charm, alt tabbing works like it should.  All the basics are good.  

Can someone please help me trouble shoot those pesky errors please?  I know its redundant..  BTW, i have an integrated Intel graphics card on a Dell Optiplex G620if that helps


In order to get the cube, you need to have 4 virtual desktops. With two, it just flips back and forth between them. (you can get a neat effect with 3 also )

Also, do you have the skydome enabled? you need that to get the cube. Make sure that both cube and cube rotate are enabled in the compiz settings.

---

### Post by vic318ic on 2007-09-05
So how do I get 4 virutal desktops?  Where do i set that up?  How do i get skydome enabled, i dont remember seeing it in the compiz manager settings.

---

### Post by Inxsible on 2007-09-05
1) Do not use the terminal to bring up compiz. Press Alt + F2 to bring up the run dialog and then type in 
```
compiz --replace
``` or ```
emerald --replace
```Alternatively, you can install the fusion icon and start it using```
fusion-icon
```

---

### Post by Inxsible on 2007-09-05
System --Preferences --> Compiz Config Settings Manager -- > General Options. One of the tabs there has these settings

Make sure you have the following settings```
Horizontal Size = 4
Vertical Size = 1
Number of Desktops = 1
```

That will give you 4 sides for your cube and you can rotate it by pressing Ctrl + Alt + Button 1 of your mouse

Make sure you have the Rotate Cube plugin enabled though !!

---

### Post by Inxsible on 2007-09-05
> **vic318ic said:**
> One quick follow up.  Is there a plugin for compiz that breaks out all your open apps onto the screen so you can see them all in a tiled view and mouse over the one you want?  I just wnat to play around to compare whether i like the expose flip tab or an exploded view of your open aps.  thanks.Its called the Scale plugin where you can do what you want.

Search for it in CCSM. I am on a Windows machine at work and dont remember where exactly it is.

There's another plugin called Tile, which works pretty much the same way..This tiles all your windows and all the app windows are usable..whereas Scale, simply lets you choose one of the app windows you want to go to.

---

### Post by vic318ic on 2007-09-05
thanks alot for your help.  that was easy and i've got cube flippin goodness going on. what does the fusion -icon do?  I just tried it but it said it cant find the file.

---

### Post by Inxsible on 2007-09-05
> **vic318ic said:**
> thanks alot for your help.  that was easy and i've got cube flippin goodness going on. what does the fusion -icon do?  I just tried it but it said it cant find the file.
have you installed fusion-icon ?

Fusion icon helps in switching the composite manager between compiz and metacity so that you don't have to use the terminal. It also allows easier access to CCSM and Emerald Themer if you have installed emerald.

There is a deb file somewhere on the forum to install fusion-icon. Let me see if I can find it for you.

---

