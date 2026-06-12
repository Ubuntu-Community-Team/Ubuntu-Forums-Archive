---
title: "Wine 0.9.38 (trouble with steam)"
date: 2007-06-03
forum: Gaming &amp; Leisure
---

### Post by DerangedDingo on 2007-06-03
Well....
All was going perfectly with Steam. Everything. Half Life 2 was a friggen dream.
But I wanted to skip ahead a mission or two, and regain my savegames and whatnot, so I copied the folder in C:\Program Files\Steam\steamapps\half-life 2 on my windows drive and replaced the one in my .wine folder.

Either it was this or a wine update from 0.9.37 to .38, but Steam refuses to connect. I tried repairing the installation, reinstalling, uninstalling, but, no matter what, Steam refuses to connect my account. The error message says it could be an internet connection problem, but I have cable and I was browsing the internet at the same time it was having connection problems... the Steam.log shows nothing but errors that related to it not being able to connect, the only fishy thing I saw was "server refused connection" or something like that, which is wierd, I don't hack and my account is perfectly clean. my copy of half life 2 was bought legally, so..

It's just confusing. Reinstalling won't do anything. fixme:'s in the terminal say something about "not being able to remove shortcuts.dat" in my Steam folder, but, if I check, that file doesn't exist...

---

### Post by Ferrat on 2007-06-03
try removing wine 0.9.38 and install 0.9.37 again and see if it helps, I know the wine guys would like to know if something has regressed

---

### Post by slowdeath on 2007-06-03
i was having the same problems with Steam, so i uninstalled 0.9.38 and went back to 0.9.37 and everything works fine now.

---

### Post by Ferrat on 2007-06-03
Report it to the wine guys then, so they can find the regression =)

---

### Post by Enverex on 2007-06-03
As you're testing beta software I'm sure you'd have no problem in taking the next step as Ferrat mentioned above:

Regression testing is when you use the GIT program to sort through patches between versions of Wine to find the exact patch that cause the bug or breakage that didn't used to exist on an older version of Wine but has now appeared. See [http://wiki.winehq.org/GitWine?highlight=%28git%29#head-fc6d68a85d32bb6a8f4ea0485f50dbb6409ab6f4](http://wiki.winehq.org/GitWine?highlight=%28git%29#head-fc6d68a85d32bb6a8f4ea0485f50dbb6409ab6f4)

---

### Post by sonicborg on 2007-06-03
i had trouble using .37 to even isntall and start steam, when i saw .38 come out, i installed it and steam started installing fine,
after the first update to the steam client, it is no longer able to connect.

As suggested above, i have taken a step back and used .37 again, and now it runs nicely.

---

### Post by jfox83 on 2007-06-03
how do you revert back to 3.7?
I am unable to connect to steam also.

---

### Post by sonicborg on 2007-06-03
go to winehq and download page, they hold a archive of old downloads there.
I have got it all installed now, but i get that stupid error that reg is in use, you have to go into the game properties and run file integrity check before launching the game. this is annoying, slow, and a pain in the *** if you have a clan match :)

also suffering from blank screen now when i actually get into the game. so much hassle, hardly making it worth it.

---

