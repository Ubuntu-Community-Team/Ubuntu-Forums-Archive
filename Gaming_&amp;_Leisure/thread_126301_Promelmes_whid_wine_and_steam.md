---
title: "Promelmes whid wine and steam"
date: 2006-02-06
forum: Gaming &amp; Leisure
---

### Post by svar on 2006-02-06
Hello :)

I try to get cs:s (steam) to run under wine but have a problem.
I get no texst at the login window (see link [here]("http://svar.home.online.no/bilde.jpg") )
I have installed the mozilla ddl file like said [here]("http://www.linux-gamers.net/modules/wfsection/article.php?articleid=17")

I have the latest wine

---

### Post by ubuntuforums on 2006-02-06
I would also like to know more about this.  I am in the process of setting up Ubuntu on my XP machine and I want to be able to run Steam and play CSS with  Ubuntu as well as other games.  All information will be very much appreciated.  Thanks... :)

Also, where can I get Linux drivers for my Sapphire Radeon 9600xt 256drr2 and my soundblaster live! 24-bit 7.1...  Thanks again... :)

---

### Post by svar on 2006-02-08
Now I got it working, but it lags like :evil: 
I wonder if I have done something wrong

---

### Post by svar on 2006-02-12
What can be wrong then I start winecfg, choose sound and then all quit?
then I try to start a game in wine, it says driect_sound missing or something.

---

### Post by gremlin hunter on 2006-02-12
From: [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games)

Start steam by just typing wine Steam after you changed to the directory you installed Steam. Once you are sure that there're no troubles with Steam and it runs fine, start it like that: WINEDEBUG="-all" wine Steam This suppresses all the errors and FIXME's Wine is trying to print while in normal mode. Steam and Steam games run then way faster (especially Half-Life 2 and its mods).

---

