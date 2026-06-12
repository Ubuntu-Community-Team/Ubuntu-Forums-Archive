---
title: "Game Launch/Management system list"
date: 2010-09-22
forum: Gaming &amp; Leisure
---

### Post by komitaltrade on 2010-09-22
It will be nice if here will be posted all known game launching and/or management systems.

Till now, I found like best:

- MythTV
- XBMC

---

### Post by frostwork on 2010-09-23
**typhon:**
[http://www.frostworx.de/?p=1](http://www.frostworx.de/?p=1)
many more features in svn:
[http://code.google.com/p/typhon-launcher/](http://code.google.com/p/typhon-launcher/)

**wahcade:**
[http://www.anti-particle.com/wahcade.shtml](http://www.anti-particle.com/wahcade.shtml)

**gelide:**
[http://gelide.sourceforge.net/](http://gelide.sourceforge.net/)

---

### Post by komitaltrade on 2010-09-23
Nice post.

Typhon is limited with numbers of games and it is not too clear how to set and browse. 

Wahcade is also quite limited (like djl).

Gelide looks great and probably is best available application (not media center). So, far as I saw, only problem is help files (manual missing). It also need some solution for fetching on-line informations about the games (like GCstar).

---

### Post by frostwork on 2010-09-24
hi!

well typhon is limited only for normal programs (7 menus, all with 16 entries) and not for
emulators. imho browsing is quiet easy, but I agree that the settings could be easier to
handle. I'll try to improve this (still looking for help btw) :)

tbh I also can't see where wahcade is limited (maybe apart from being written in python).

yeah gelide is very nice, but not really made for a htpc setup.
As I use the launcher on my htpc I'd prefer typhon or wahcade therefore.
for desktop gelide simply rocks.

---

### Post by komitaltrade on 2010-09-24
Well, it is small irony, typhon is written for Linux and he is limited for linux games (7x16).

I agree how gelide don't support linux games at all (so, worst) and how it is not perfect for htpc (but it is possible to launch it in fullscreen mode). 

But, when you talk about HTPC, it cant be doubt how MythTV is the best option. Moreover:

- support ALL GAMES (Linux and emulated - included PC) - just typhon can enter in competition (so far)
- all setup can be hidden from final users (any other system have those capability), what is important to avoid how users (public, your children's, parents, etc.) dont delete games or make some other mess - any other system can compete this feature.
- a part of other MythTV features (media center), it is only real hermaphrodite solution. It mean how you can use it like standalone OS system (media center with capabilities to have also menu for application launchers), but also like desktop application (e.g. put it like startup application in desktop (e.g.) 4 and you have all the time available media for quick access)

So far, my votes are - gelide is best desktop oprion and MythTV is best HTPC option - my global vote is MythTV (above two features).

By the way, i still looking for better solution (thats why post exist), as MythTV have complicated settings (gelide is here best without competition).

---

### Post by frostwork on 2010-09-28
ok, just updated typhon svn to 7x20 entries
( [http://code.google.com/p/typhon-launcher/source/detail?r=41#](http://code.google.com/p/typhon-launcher/source/detail?r=41#) )
if you really need more standard program entries, patches are always welcome :)
a perfect rewrite would be to replace this "limit" with a proper function to count all set entries in the config - help required.

of course you could alternatively use xdg-open as "emulator" and some desktopfiles as "games" (in every frontend).

can't speak for mythtv, haven't touched it for years as I prefer vdr for dvbs.

if xbmc would get rid of the ancient "window keeps focus" bug (caused by sdl)
it would simply rock as launcher imho (might even now, haven't tried it for a long time).

---

### Post by komitaltrade on 2010-09-28
I (can) agree how 7z16 or 7x20 can be enough for some ordinary user, but as I look for solution for public usage, I should to be able to launch (first at all, to easy navigate and search) thousands of games (e.g. just sega or neo-geo are small footprint - less than 1 GB - for over 1000 roms per console, I also have 180 free windows via wina installable games and what about the thousands of linux games???).

---

### Post by frostwork on 2010-09-28
as already mentioned the emulators don't have that limit, just the normal programs.
I also mentioned that you can xdg-open as emulator - so you can also launcher your wine games as "game roms". 
I prefer "sh" as emulator and some scripts as roms for wine games though, but that's not the point.

to sum it up. there are not very many launchers out there. those exiting all have their pros and cons, but none of them is perfect.
but hey!
opensource -> teamwork -> patches -> new features
(in a perfect world at least :???: )

---

### Post by komitaltrade on 2010-09-28
Yeah.

 - 7 x 20 mean 7 emulators x (XXX) games and/or 7 linux genres (action, FPS, etc.) x 20 games

but, ...

1) 7 x XXX roms mean very long (e.g.) neo-geo list (what about filtering?)
2) 7 x XXX mean limitation on 7 emulators (or I'm wrong?)
3) I wrote on the end ("*what about the thousands of linux games???*"), so what we will do with linux games?

But not take it malicious and/or negative. Aim of topic was exactly try to review existed solutions and to see what about the games in linux (see pool). That by nature include review of advantages and disadvantages of the solutions.

I saw on your website (p.s., look&feel also clearly indicate it) how you decided to turn it in mediaccenter (logical way of development).

That by nature put typhon in comparison with MythTV, XBMC and Boxee (also support games, but ...).

By the way, Freevo also support games (Moovida not), but I found Freevo very unstable.

---

### Post by frostwork on 2010-09-29
hey!

1) good point. that's why I at least added a "quickbrowse function" which skips 10 entries at once. not perfect, but better than nothing atm. I really wished there were more contributors, as I'm working on typhon alone and I'm still learning :)

2) another good point. adding support for another 7 emulators is on my internal todolist.
atm it would be possible though to use one of the program enitres to launch a 2nd typhon with a different typhon-emurc (and close the 1st typhon)

3) hm I know very many linux games out there, as I'm always searching for new ones
and port those to linux (if possible) and create gentoo ebuilds (gentoo-gamerlay).
tbh I doubt that there are many people having literally thousands of native linux games installed :)
anyway - a function in $launcher which reads all desktopfiles automatically (and oc using the found genres and settings) would be the perfect solution (f.e. like netbook-launcher,  lxde, kupfer or simply every dropdownmenu in "bigger" DEs).
speaking for typhon I can't implement this alone I'm afraid.

but enough about typhon now.

it has been a while (several years) since I last used 
**freevo**
( [http://freevo.sourceforge.net](http://freevo.sourceforge.net) )
It was quiet complicated to configure, but when done it was nice to use.

There's another ancient emulatorlauncher, which is missing on this list
**advmenu**
( [http://advancemame.sourceforge.net/menu-readme.html](http://advancemame.sourceforge.net/menu-readme.html) )
I used it several years ago to create 2 ppc linux live game cds (launching native games)
It might look a bit outdated (configurable), but it did its job very good.

no idea if there are any other launchers not mentioned yet.

---

### Post by komitaltrade on 2010-09-29
Idea with multiple instance is in fact excellent idea, as it is fact how users from begin know what console they want to play.

Yes, it is thousands (just original ubuntu repository (Ubuntu Software Center) give you choice of 488 games, but it is not the point in numbers (also 488 is great number).

I already paid development of system based on Netbook Launcher, but I was after finished payment abandoned. So, I can upload code (if somebody want it). It is based on Netbook Launcher (Karmic version), but upgrade disable it, as developer used NL library (hacked).

At moment, in cyber cafe, I'm using NL (as for me is easy to disable all changes from users and they like desktop menu system) and Im using 3 GNOME sessions.

- Regular (Internet and other applications)
- Kids (Firefox, Prisms for online games for kids and linux games for kids, included educational) and
- Gamer (games sorted by genre, not by consoles).

Operator simply remotely switch sessions. 

Reason of approach is because nobody want crowded menu, but owner of cyber need multipurpose PCs to extending clients by number and percentage of PC usage.

Now I looking for better solution and thats all.

---

