---
title: "compiz ceased to load automatically... ??"
date: 2011-12-31
forum: Desktop Environments
---

### Post by lk32 on 2011-12-31
Hi.
I use Ubuntu 11.10 from a few months now, and everything worked fine, until today. I didn't shutdown badly the system, neither i installed something strange and neither downloaded new packages yesterday... but when i booted the system this morning, something was wrong, and i think the problem is in the loading of the desktop envinronment. Everything goes fine with the login, and it SEEMS fine with the desktop, too... i opened firefox throught gnome-do, and when i tried to maximize the window by double-clicking on the top bar, FF just crashed and closed him-self. This repeated every time i tried it, and then i noticed that in every window the top bar (the one with the close-maximize-minimize buttons) had disappeared. More: when i start nautilus, the interface load fine (without top bar) but if i try to just focus it the whole system nearly freeze: i'm not able in any way to use nautilus, and to get back to use other programs (such as a terminal, or even to open the shutdown prompt) i have to wait a long time.
Another thing i noticed was that the change-desktop icon on the right-bottom corner was strangely switched to one single desktop from the six that i used... well, actually is even strager than that: in the icon i see a single desktop, but with the dimension that it would have if there were 6 on two row of them... and when i try to switch between desktops, i find out that there are actually only 4 desktop avaiable :S.
I partially solved this mess starting manually in the terminal "compiz" in background, using "$compiz &". This restore top-bars and i can use nautilus and everything normally, BUT it still doesn't fix the desktops thing that i described above. One more thing is that the "switching animation" (i don't know how is it called) that appear when switching between desktops using Ctrl-Alt-{Arrows} is changed... now it is more "animated". In fact, is more similar to the one that appear when changing desktops in Unity (while i'm doing it throught gnome).
This fix is only temporary though, i must manually start compiz (or whetever i do with that command) everytime i reboot the system, wich is pretty annoying.
More info: the problem is "desktop-system indipendent", that is: it holds indifferently logging with gnome, gnome-classic, unity, unity-2d

What happened to my poor Ubuntu?? What can i unconsciously have done to him? And especially, how do i fix this??
Thanks for your time!

EDIT: i was wrong: this is definetly desktop-envinronment-dependent: i'm doing more testing and here is more info:
Logging with "gnome" everything goes *perfectly*, nothing is slow and nothing seems to show any problem.
Logging with "gnome-classic", "gnome-classic (with no effect)" brings all the problems described above. More info about that: different programs behave differently: with firefox, i can start with no problems except for the top-bar missing, and i can drag&drop the window without problems (but not double-clicking it, which close the program without messages or warnings). With Nautilus i can't even focus the window. With the terminal i can use the program (even if it is abnormally slow), but if i try to drag&drop the window the system freeze. During this "freezing" periods, i can't switch desktops or do anything; if i try Ctrl-Alt-Del it shows the log-out prompt but i can't click on the buttons; still if i wait the 60 seconds it logs out.
MORE: i think ubuntu is going crazy (or maybe that is me, or probably both xD)
Logging with "ubuntu" (which should be unity i think) brings all the problems above. Also: i can't see any of the "unity-things" until i start compiz with the terminal (and i have to do this immediatly, or i risk to freeze the whole system: even try to drag&drop the terminal freezes everything and i can hear the fun going like crazy, which means that the system is breathlessly doing something... i think trying to bite his tail like dogs xD). On the terminal where i start compiz i also receive tons of warning. If i try Ctrl-C compiz through the terminal in which i started it, i also get (well i get lot of things, but i especially noted this one) a segmentation fault error, and i'm left with nothing but the background and the terminal, in which i can only scroll up and down, not write or move the window or anything. Shortcuts to logout don't work anymore. I had to reboot using a tty terminal (yes, those shortcuts still work).

I think i collected enough info for you erudite guys to figure out what's going on... if not tell me what more you need to know! :)
PS: sorry for eventual grammar mistakes, i'm not english-native!

---

### Post by lk32 on 2011-12-31
up

---

### Post by lk32 on 2012-01-01
i still have this problem!! no clue??

---

### Post by lk32 on 2012-01-02
up!!!

---

