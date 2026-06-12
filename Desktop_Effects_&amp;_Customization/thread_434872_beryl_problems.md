---
title: "beryl problems"
date: 2007-05-06
forum: Desktop Effects &amp; Customization
---

### Post by L0c on 2007-05-06
feisty
radeon 9000
open drivers

1. when i run beryl video files dont play the way they play when beryl is off...
example: i start a video in any player except xine and video isnt shown until i move the window. if i fullscreen video i see black backround + statusbar from player. if i open a menu and close it again part where video is supposed to be shown turns black and menu is shown afetr its closed(not refreshed... sort of)
2. in beryl i have random computer freezes(cant do anything, not even raising skinny elephants). i solved this in edgy by putting AccelMethod EXA, but since upgrade when i try EXA and try running beryl, X restarts
3. in beryl gnome keyboard shortcuts dont work(not sure if this is or isnt normal since beryl has its own shortcuts too, so not so much of a problem)

in gnome video play normally, no freezes, and ofc shortcuts work
ati has direct rendering and glxgears(as a testing) worked just fine in beryl and gnome
if you think there's no soltuion to this problem maybe you can give me a suggestion how to get some beryl options in gnome. such as moving mouse to upper-right corner to offer windows, moving a window with mouse from one desk to another by dragging and switching between desks with mouse wheel when on background

---

### Post by rygar on 2007-05-06
sorry to answer your question of least concern, but i don't have an answer for the first two

gnome shortcuts from (system -> preferences -> keyboard shortcuts) use metacity.  beryl overrides metacity, so you'll have to create new shortcuts in beryl.  sound like you already know how to to do this, but if you don't i'll explain...

---

### Post by L0c on 2007-05-06
> **rygar said:**
> sorry to answer your question of least concern, but i don't have an answer for the first two

gnome shortcuts from (system -> preferences -> keyboard shortcuts) use metacity.  beryl overrides metacity, so you'll have to create new shortcuts in beryl.  sound like you already know how to to do this, but if you don't i'll explain...

thnx for anwsering
yes, i know that part(setting up shortcuts).

---

### Post by dodgePT on 2007-05-06
I thought i'd share this with everyone, i have the same kind of problem you have L0c,
This problem happens with almost all ATI models, mine included (9600XT) and is due to the bad ATI proprietary driver.

Solution:
Open MPlayer, goto preferences, select X11/Xv driver (in video preferences), hit OK and close MPlayer. You'll see that now you can watch movies, but only in window mode, 'cause if you toggle fulscreen, image will look blocky, and framerate will be low.

Now, try to start MPlayer through the console with this command: "gmplayer -zoom" (without quotes).

Open a movie and check it out, image don't look blocky anymore :)

---

### Post by L0c on 2007-05-06
thnx dodgePT
i actually dont have blocky image in fullscreen when opened normally
now i tried to do same thing for totem by adjusting gstreamer-properties
changed to No Xv
now i get the blocky image but only in totem, or if i change drivers to anything else in gstreamer-properties i still get the initial problem with totem

---

### Post by travm on 2007-10-28
I have this problem too I think.  Video playback works fine if i select xfce4 as my window manager, but when beryl is running the show the videos dont show up unless I move the window, and even then they dissapear again.  I am using totem and I cant find that setting.  I suppose I probably could just turn beryl off when I want to watch a video.

---

