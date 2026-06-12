---
title: "Steam/proton issue, game works, but launch fails after usage"
date: 2019-05-27
forum: Gaming &amp; Leisure
---

### Post by pqwoerituytrueiwoq on 2019-05-27
I was looking at getting a new game for the 1st time in over 5 years and i wanted to see how well steam would work
I happen to have a couple games on steam from when i got a Phenom II 965 
Anyway i never played it as it would not run on Linux and i do not want to deal with windows
but anyway i installed [Darksiders Warmasterd Edition](https://www.protondb.com/app/462780)
enabled proton 4 for unsupported tittles, and it open and runs just fine, just wish i had a FPS counter... (edit found a option for that in steam, idk if it works)
so i played the game and stopped a few times and then when i open it it will not start, the only thing i have found to make it work again is the delete all steam folders in my home directory [FONT=courier new]~/.steam[/FONT] & [FONT=courier new]~/.local/share/Steam[/FONT]
It will say the game is running when it is not
and downloading a 20GB game over and over sucks, let alone how big modern games are
i tried not deleting the game and only the games cache and that almost worked, but the game will not get past the loading screen if i do that
Any idea what files i can delete when this happens and re-download everything from scratch?
xubuntu 18.04 64bit; CPU - i5-4690k; GPU; GTX 1060 3GB;Nvidia driver 418.56
extra software sources:
[url=http://i.imgur.com/avb4ozx.png]
  [img]http://imgur.com/avb4ozxl.png[/img]
[/url]
*multiverse and restricted repos are active

---

### Post by CatKiller on 2019-05-27
Simply verifying the files from within Steam may well do it, and be less brutal.

Proton's per-game Wine prefixes are in ~/.steam/steam/steamapps/compatdata/, and the game files are in ~/.steam/steam/steamapps/common/

---

### Post by pqwoerituytrueiwoq on 2019-05-27
I tried verifying, it solves nothing
i played it a while after making this post, here is the log file
after exiting it still says it is running, here is the games log file:
[https://paste.ubuntu.com/p/87yM99YK2X/](https://paste.ubuntu.com/p/87yM99YK2X/)

---

### Post by CatKiller on 2019-05-27
Well, Proton is just Wine with DXVK. Sometimes it works, and sometimes it doesn't.

There are *lots* of reports in the ProtonDB you linked of issues with the videos - which is reflected in your log - and a whole bunch that say it didn't work at all for those users.

Games not exiting cleanly is relatively common with Windows games through Proton. Deus Ex: Human Revolution does the same for me. I just kill the process in that case. Sometimes a restart of the machine helps.

---

### Post by bigbangnet on 2019-06-05
I noticed something yesterday. When I played or messed around trying to run Fallout 4 correctly yesterday I noticed even though I exited out of the game, it would still be running. I got POP!_OS so I went in the system monitor and stopped the process attached to the game (fallout 4 in this case), then restarted the game through steam and it worked correctly.

---

