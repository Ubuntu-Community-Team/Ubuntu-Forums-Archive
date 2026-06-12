---
title: "messed up unity desktop with compiz"
date: 2011-06-28
forum: Desktop Environments
---

### Post by xXzero_contentXx on 2011-06-28
I messed up my desktop by playing with settings in compiz while i was in unity desktop.  The problem happened when i was checking and unchecking features for the cube function. After messing with those i have no menu and no sidebar cant access anything with keyboard shortcuts cant bring up a terminal. The only thing that exists are a few shortcuts to files on desktop. Running 11.04. BTW classic and all others work fine.

---

### Post by nilarimogard on 2011-06-28
You'll probably want to reset Compiz and Unity. For this, use the commands below:
```
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
```

In my test, resetting just Compiz makes Unity crash so make sure you run both of those commands. More info: [How To Reset Unity, Launcher Icons Or Compiz In Ubuntu]("http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html")

---

### Post by cybrsaylr on 2011-06-28
I did the same thing about a week ago. Put in Compiz and tried enabling the cube features and lost the whole Unity desktop. Spent a few hours tying to recover Unity following a few suggestions and got nowhere. Ended up doing a reinstall and all is fine again.

It was then I discovered Compiz has problems with Unity and is best avoided for now unless you have the know how to do some reconfiguring of Unity.

---

### Post by FormatSeize on 2011-06-28
In my experience, certain combinations of effects cause the desktop to go haywire. As such, I don't like to toy around too much with various settings in Compiz if I don't feel like I have an hour to waste trying to guess at what combination will decide not to break my desktop today.

---

### Post by zuerston on 2011-06-28
> **xXzero_contentXx said:**
> I messed up my desktop by playing with settings in compiz while i was in unity desktop.  The problem happened when i was checking and unchecking features for the cube function. After messing with those i have no menu and no sidebar cant access anything with keyboard shortcuts cant bring up a terminal. The only thing that exists are a few shortcuts to files on desktop. Running 11.04. BTW classic and all others work fine.

I sure hope they fix this crap! **I HATE UNITY** and **LOVE COMPIZ**.  Compiz will not even run right when using the "classic" desktop,** FULL OF BUGS ,TOTAL CRAP! **

**Can Unity be TOTALLY REMOVED from Natty?????????** I don't even want it on my computer! 
Damn,** I miss my CUBE and EXPO !!!!**

FIX PLEASE!
:mad:

---

### Post by h4x0l2 on 2011-06-28
> **cybrsaylr said:**
> I did the same thing about a week ago. Put in Compiz and tried enabling the cube features and lost the whole Unity desktop. Spent a few hours tying to recover Unity following a few suggestions and got nowhere. Ended up doing a reinstall and all is fine again.

It was then I discovered Compiz has problems with Unity and is best avoided for now unless you have the know how to do some reconfiguring of Unity.



2nd this... the wobbly windows works, but thats about it.

---

### Post by h4x0l2 on 2011-06-28
> **zuerston said:**
> I sure hope they fix this crap! **I HATE UNITY** and **LOVE COMPIZ**.  Compiz will not even run right when using the "classic" desktop,** FULL OF BUGS ,TOTAL CRAP! **

**Can Unity be TOTALLY REMOVED from Natty?????????** I don't even want it on my computer! 
Damn,** I miss my CUBE and EXPO !!!!**

FIX PLEASE!
:mad:

enable the login lock screen. Enable lock screen on screen saver.
when you boot, choose GNOME classic(very bottom of page), problem solved. Compiz will work fine.

if not, reinstall compiz FROM THE CLASSIC DESKTOP and repeat the above steps.

---

### Post by zuerston on 2011-06-28
[SIZE=4][COLOR=black]**OK !! **[/COLOR][/SIZE]

I fixed it!  while running the "Classic" desktop, open synaptic, find **UNITY**,mark for **COMPLETE REMOVAL**, now find **GNOME** and mark for** INSTALL, **now **click apply** . when it gets done you will have **everything working in Compiz!!!**  just leave the login set to classic.
The **cube works** even the "gears" as before same with Expo it too works and all the rest of Compiz  **GREAT**
[B]Poooey on Unity!
[/B]
Its all fixed, and yes I did try the "regular" login,it has stuff missing so continue **with the Classic and all is well.** all other settings and icons are fine and unchanged.
:popcorn::):P:guitar:Goodbye Unity,its been bad to know ya!!! (song)

**Note to programmers:  We don't want MS windows look-alike crap! Why do you think we use Ubuntu and Linux? **

---

### Post by Krytarik on 2011-06-28
To those of you who still want to do some with Unity and possibly enable the Cube:

[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

Greetings.

---

### Post by zuerston on 2011-06-28
> **Krytarik said:**
> To those of you who still want to do some with Unity and possibly enable the Cube:

[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

Greetings.


Hello Greetings 2 U 2
Thats all fine for people wanting to diddle around all day, but I also like to use my computer and keep the diddle'ing to a minimum :D I use the heck out of that Cube, I use my PHP editor on one side and Komposer on another and my website on another! the side left,I have Firefox running and using stuff from the Internet in my programming chores and text notes, all sides are in full use!, so easy to flip sides with the mouse wheel. 
So the cube is not a toy for me and it must be working,its so easy to flip sides quickly to do tasks! and the Expo I like when contemplating my duties and just zip to any of those sides instantly, and its great as a "screen saver", well I use it for standby operations! ;)

Unity should only be a check box choice in Compiz for those that like it.
Ubuntu should come with Compiz FULLY loaded and all features enabled and tuned up! and users could just un-check the stuff they dont like. But by all means,,keep everything fully Compiz compatible,even Emerald.
:D

---

### Post by cybrsaylr on 2011-06-28
Been using Unity for about a month now and have 'adjusted' to it.

IMHO Gnome was more unified and efficient than Unity. With Gnome everything flowed from the top panel's 3 Tabs and each one quicky took you to whatever you wanted fast. Unity reminds me of KDE and Windows by offering you several ways to do the same thing, which of course requires extra mouse clicks.

I also miss the Gnome top panel and the way it could easily modified.

I miss the Gnome bottom pannel also. I multi-task a lot and used up to 6 desktops. Unity only offers 4, inless you add CCSM and add more which looks IMHO weird compared to the way Gnome did this. 

The 4 desktop Unity setup looks nice but when using all four desktops, if a window 'shifts and moves' inside that desktop, you cannot switch between desktops, until you manually find and correct the overlapping window at fault which isn't always easy. 

None of this existed with Gnome. Plus Compiz worked very well for me with Gnome. Unity does not play well with Compiz.

---

### Post by cariboo on 2011-06-29
> **cybrsaylr said:**
> Been using Unity for about a month now and have 'adjusted' to it.

IMHO Gnome was more unified and efficient than Unity. With Gnome everything flowed from the top panel's 3 Tabs and each one quicky took you to whatever you wanted fast. Unity reminds me of KDE and Windows by offering you several ways to do the same thing, which of course requires extra mouse clicks.

I also miss the Gnome top panel and the way it could easily modified.

I miss the Gnome bottom pannel also. I multi-task a lot and used up to 6 desktops. Unity only offers 4, inless you add CCSM and add more which looks IMHO weird compared to the way Gnome did this. 

The 4 desktop Unity setup looks nice but when using all four desktops, if a window 'shifts and moves' inside that desktop, you cannot switch between desktops, until you manually find and correct the overlapping window at fault which isn't always easy. 

None of this existed with Gnome. Plus Compiz worked very well for me with Gnome. Unity does not play well with Compiz.

Remember when Gnome 2 was released in 2002 (yes 9 years ago) it was so unusable I switched to KDE. Remember when WIndows XP was released in 2001, I was fortunate enough to be using Linux, so I didn't have to put up with usability issues.

What I'm trying to say, is that Gnome 2 and XP have matured quite a bit over the years. GIve Unity and Gnome-shell time to mature too.

---

