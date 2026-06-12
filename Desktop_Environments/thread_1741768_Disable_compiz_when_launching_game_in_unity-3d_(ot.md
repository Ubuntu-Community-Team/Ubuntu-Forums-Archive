---
title: "Disable compiz when launching game in unity-3d (otherwise GL  games are unplayable)"
date: 2011-04-28
forum: Desktop Environments
---

### Post by interzoneuk on 2011-04-28
Hi.

How do I temporally disable compiz when in unity-3d so that I can play a game at the correct speed (with compiz enabled I get about 20% of the speed I get with compiz disabled)

I have tried a script with

metacity --replace &
./game
compiz --replace &

But this makes an unusable desktop..

I know I can use unity-2d but that seems to be worse in terms of usability..

I also know I can use gnome2 but whats the point when that will be missing in the next release ...

Is there anyway of doing this in unity-3d?

Are there any plans (possibly from compiz) to ever do this automatically ?

One thing that worries me is that a new user will try a opengl game and think that Linux is far slower than Windows at games (which if you have a nvidia card with the binary driver is not true)

Cheers

---

### Post by AndersAA on 2011-04-28
tried metacity --replace && game && unity --replace?

---

### Post by Krytarik on 2011-04-28
Since Unity (3D) is based on Compiz, you obviously can't disable it without messing up your desktop.

Greetings.

---

### Post by AndersAA on 2011-04-29
> **Krytarik said:**
> Since Unity (3D) is based on Compiz, you obviously can't disable it without messing up your desktop.

Greetings.

You can replace it with metacity while the game is running.

---

### Post by Krytarik on 2011-04-29
> **AndersAA said:**
> tried metacity --replace && game && unity --replace?
It *may* even work, but not with "unity --replace", instead with "compiz --replace", like the OP stated.

You could also place launchers for all of them at your desktop, just in case anything goes wrong.

But all of that is of course a bit risky, because without Compiz running you obviously can do barely anything in Unity, like experienced.

---

### Post by AndersAA on 2011-04-29
> **Krytarik said:**
> It *may* even work, but not with "unity --replace", instead with "compiz --replace", like the OP stated.

You could also place launchers for all of them at your desktop, just in case anything goes wrong.

But all of that is of course a bit risky, because without Compiz running you obviously can do barely anything in Unity, like experienced.

I just tried, it works fine... And definitly unity --replace. Unity is tied to compiz, doing a metacity --replace takes down your gui but keeps your window manager going. (aka if you want it usable you'd need to start up gnome panel and nautilus too). A compiz --replace afterwards will bring up a window manager, but not everything else.

---

### Post by Krytarik on 2011-04-29
> **AndersAA said:**
> I just tried, it works fine... And definitly unity --replace. Unity is tied to compiz, doing a metacity --replace takes down your gui but keeps your window manager going. (aka if you want it usable you'd need to start up gnome panel and nautilus too). A compiz --replace afterwards will bring up a window manager, but not everything else.
Metacity and Compiz are both window managers. And Unity is just a plugin of Compiz, like any other of it. Can you confirm that if you run "compiz --replace", after replacing it before by Metacity, it brings up Unity as well? Anything other than that would be really weird.

---

### Post by mc4man on 2011-04-29
> Can you confirm that if you run "compiz --replace", after replacing it before by Metacity, it brings up Unity as well?

a metacity --replace & 
followed by a 
compiz --replace & 
will return you to your unity desktop
(personally just login to classic (no effects) for a few things that are better there

---

### Post by interzoneuk on 2011-05-01
Hi - thanks to everybody who posted.

Using 

compiz --replace & 

After the game seems to result in buggered desktop

unity --replace & 

for some reason seems better

I only want this on full screen games where i'm not using the desktop whilst playing (so metacity --replace is fine as long as the command afterwards results in a functioning desktop)

I am still worried a Linux newbie will try a game (i.e quake wars, etc) in Linux and just think Linux is a lot slower than windows...)

For example on my machine (geforce 8500) on openarena I get about 160fps without compiz - with compiz I get about 55 fps.

Quake wars is just not playable with compiz full stop... without I get about 50 fps

I really hope that gnome/unity/compiz (any one!!) is working on a solution where compiz can be turned off automatically when a full screen game loads (what is the point in wasting my video card on features I can't see at the time? - it completely rapes the fps also)

I believe modern versions of KDE4 turn off compositing automatically when launching full screen games - is gnome / unity ever going to have this feature?

---

### Post by Krytarik on 2011-05-01
The point is that any higher FPS than the refresh rate of your monitor doesn't really make sense. And Compiz is set up by default to respect that fact. Of course it needs to detect the refresh rate correctly, or you set it manually. And it may well be that even then the games don't run as fluent as without Compiz.

Try setting the refresh rate manually in "CompizConfig Settings Manager -> General Option -> Display" by disabling "Detect Refresh Rate" and modifying "Refresh Rate".

You may also try disabling "Sync To VBlank" there.

---

### Post by interzoneuk on 2011-05-02
Hi

The 1/3 loss of speed is absolutely nothing to do with the refresh rate.

Compiz kills 30-60 % fps on any game

ETQW with compiz (for example) I get 8-12 fps rather than 50 fps without (i.e not playable with compiz enabled)

My point was that as long as you have disabled compiz you get the same fps in Linux as Windows (some games are higher in linux..)

The games i'm referring to are built for Linux and Windows btw....

---

### Post by not4us on 2011-05-12
So is there any "easier" way to do this (disable compositing)and then enable it back?
I'm really getting to like Unity but I need my games working properly :D

---

### Post by Krytarik on 2011-05-12
> **not4us said:**
> So is there any "easier" way to do this (disable compositing)and then enable it back?
I'm really getting to like Unity but I need my games working properly :D
You could just place some launchers for that on your desktop, like I mentioned earlier.

Specifically, these are for:
- "metacity --replace"
- "compiz --replace"
- your games

Of course, this is because you can't access the Unity launcher/panel while Compiz isn't running.

As a fallback variant, you could also run Gnome Panel while in that state, add launchers for:
- "gnome-panel"
- "killall gnome-panel"

You see, you can do pretty much everything to a Unity session, if you keep in mind that Unity is just a plugin of Compiz, running on top of a usual Gnome session, but with the Unity launcher/panel instead of Gnome Panel, of course.

Greetings.

---

### Post by not4us on 2011-05-12
> **Krytarik said:**
> You could just place some launchers for that on your desktop, like I mentioned earlier.

Specifically, these are for:
- "metacity --replace"
- "compiz --replace"
- your games

Of course, this is because you can't access the Unity launcher/panel while Compiz isn't running.

As a fallback variant, you could also run Gnome Panel while in that state, add launchers for:
- "gnome-panel"
- "killall gnome-panel"

You see, you can do pretty much everything to a Unity session, if you keep in mind that Unity is just a plugin of Compiz, running on top of a usual Gnome session, but with the Unity launcher/panel instead of Gnome Panel, of course.

Greetings.

I'll have to give that a try and see. Will keep you posted on results.

---

### Post by clemmy on 2011-07-12
I don't play games, but I need to turn off compiz for better googleearth experience. I've succesfully followed the advices of this thread, it worked great, so I'd like to thanks all the contributors :)

I've also improved it al little bit, so that it automatically load unity-2d when disabling compiz. This way it provide a more consistent user experience!

If somebody want's to try this solution, can follow the following steps.

**1. Get Unity 2D**
```
sudo apt-get install unity-2d
```
Tip: Unfortunately unity2d will be selected as the default session! Just remeber to select Ubuntu when you login next time. This setting will be remembered and 3D will be your default session again. ;-)


**2. Prepare 2D starter**
Create an empty document in your home, name it 2d-desktop, give it execution rights (right click -> permissions -> Execution), and put the following text in it:
```

#!/bin/bash

metacity --replace &
killall -9 unity

sleep 1

killall -9 unity-window-decorator &
killall -9 unity-panel-service &

sleep 1

unity-2d-launcher &
unity-2d-panel  &

exit 0

```


**3. Prepare 3D starter**
Create an empty document in your home, name it 3d-desktop, give it execution rights (right click -> permissions -> Execution), and put the following text in it:
```

#!/bin/bash

killall -9 unity-2d-panel &
killall -9 unity-2d-places &
killall -9 unity-2d-spread &

# sleep 2

unity --replace &

killall -9 unity-2d-launcher &

exit 0

```

**4. Enjoy**
Now you can simply switch from 2d to 3d desktop with just a double click on the appropriate file!

---

### Post by Chronos6 on 2011-07-31
Works great, thanks for the solution. I have an ati hd4200 and when i get back to 3d mode my screen is messed up. Do you have any idea how could i reset the driver?

---

### Post by aneeszaki on 2011-10-30
[U]
[/U]the solution of clemmy works great thx :)
I am thinking about putting 2d-desktop then game-exec then 3d-desktop in one script.

Anyway thx :)

---

### Post by Zwenx on 2012-05-16
On 12.04 LTS, here are the fixed scripts to switch between unity 2D and unity 3D on the fly:

Unity 2D:

```
#!/bin/bash

metacity --replace &
killall -9 unity

sleep 1

killall -9 unity-window-decorator &
killall -9 unity-panel-service &

sleep 1

unity-2d-shell &
unity-2d-panel  &

exit 0
```


Unity 3D:

```
#!/bin/bash

killall -9 unity-2d-panel &
killall -9 unity-2d-places &
killall -9 unity-2d-spread &

# sleep 2

unity --replace &

killall -9 unity-2d-launcher &
killall -9 unity-2d-shell &

exit 0
```

Enjoy :) There Should be a default option in System Settings -> Appearance, in my opinion, especially with the coming of steam to linux, Ubuntu should be game ready.

---

### Post by BigSilly on 2012-08-09
> **Zwenx said:**
> On 12.04 LTS, here are the fixed scripts to switch between unity 2D and unity 3D on the fly:

Unity 2D:

```
#!/bin/bash

metacity --replace &
killall -9 unity

sleep 1

killall -9 unity-window-decorator &
killall -9 unity-panel-service &

sleep 1

unity-2d-shell &
unity-2d-panel  &

exit 0
```


Unity 3D:

```
#!/bin/bash

killall -9 unity-2d-panel &
killall -9 unity-2d-places &
killall -9 unity-2d-spread &

# sleep 2

unity --replace &

killall -9 unity-2d-launcher &
killall -9 unity-2d-shell &

exit 0
```

Enjoy :) There Should be a default option in System Settings -> Appearance, in my opinion, especially with the coming of steam to linux, Ubuntu should be game ready.

I absolutely agree, and sincerely hope it is in the works. It's a major omission, especially as you say with Steam on the way. On my KDE install, all I have to do is pop into system settings, and in the effects settings tick "suspend effects for fullscreen windows". Mainline Ubuntu needs this option desperately.

---

### Post by madtom1999 on 2012-09-19
I'm having serious problems with a couple of opengl apps - blender and googleearth which are both unusable on my 4core amd. Other graphics heavy things run like a dream. 
Something seriously wrong with unity...

---

