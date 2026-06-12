---
title: "3 monitors + opengl working?"
date: 2008-02-28
forum: Desktop Effects &amp; Customization
---

### Post by Bionabolgeek on 2008-02-28
I have two 17" TFTs and a 32" LCD TV. 17"s are connected to nvidia 8600GT, and TV is connected to 6200LE (both cards different PCIE slot). Everything working perfectly in MS Windows.

I decided to give linux a try few days ago, so I installed Ubuntu 7.10.
After learning about xorg.conf, nvidia proprietary drivers, twinview, xinerama, xgl, compiz, and such things, several things came to conclusion:

1. Xinerama = no openGL. No way to start xgl/compiz, no way to run any openGL app (they crash on start). If i try to run xinerama and forced xgl, gnome crashes when trying to load.

2. Twinview works just the way I want, but it uses only 2 monitors (on the same card)

3. i have no problem setting any desired configuration manually in xorg.conf or even better in nvidia drivers (took me some time to figure out that i cant run nvidia driver settings while xgl is active - failsafe gnome configuration is only way to load it).

4. Now the things gets interesting: if I, for example, set all 3 monitors active in xorg, and i disable xinerama or twinview, gnome will apear on first monitor, while other 2 will be turned on and only black pixels are displayed. I can move my mouse cursor over those 2 monitors, but i cant drag windows there. While on them, mouse cursor turns to "X". Same happens for example if i use twinview, 2 monitors are used and 3rd monitor (LCD TV) is black and with "X" cursor.
SO i came to conclusion that i have to manually run multiple gnome or X instances on that "black screens" so i can get usable workspace. But, i dont have a single clue HOW to do it. I googled and googled, but not a single tutorial or any useful info on how to do that. At the end i managed to learn something about startx, so i tried "gksudo startx -- :2
" wich opened another x instance, but again on first monitor, and i was unable to see main X instance until i killed new one with crtl+alt+backspace.
Can anyone teach me how to run multiple gnome / X on unused monitors?

Just to make some things clear:
- no, i dont want to use xinerama, i want opengl (for example, compiz / xgl).
- one mode (monitor configuration) is particulary interesing to me: first two monitors should work in twinview mode, while LCD TV should have his own gnome instance. I do all the work on main monitors, while TV will be used for watching fullscreen videos (VLC) and running power point presentations (open office).

Thanks :)

---

