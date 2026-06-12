---
title: "Poker Stars with Wine"
date: 2006-04-27
forum: Gaming &amp; Leisure
---

### Post by manutd on 2006-04-27
I have a PokerStars question...

I've just finally installed Wine. *I think* :-k 

So to find out for sure I downloaded PokerStars, and installed it! Seemed to work OK! 
I opened it up usuing -
wine "C:/Program Files/PokerStars/Pokerstarsupdate.exe" (something like that)

It starts fine, but when I go into a table or into a tournament, after about 1-2minutes the "main menu screen" looks like it shrinkes! 
When I leave the table and try to make the original window big it won't let me! I have to shut it down and load it up again just to change tables.

Also if my screensaver comes up when PokerStars is open, the computer completely freezes up! Then I have to pull the bloody plug which makes me cringe everytime I do it! 
"I think it's cause windows always gave me hell about doing it like that". 

So does anyone know if it's Wine that is doing this or the program PokerStars? 
I felt I had some problems installing wine, so it could be bugs?? I don't know! 

Also, how does your OS get effected everytime u push the button to turn it off?? 
It it like windows and has to go and fix itself??? 
Or is it not really that bad (u just loose unsaved data)????? :-?

---

### Post by hollywoodb on 2006-04-27
1st of all, instead of 'pulling the plug', ctrl+alt+backspace should kill X and bring you back to login. chances are that X is freezing up, not the entire system

some apps are finicky about how they are run with wine.  to avoid problems I've gotten into the habit of starting applications with wine from the directory the executable is in. try this:
```

cd ~/.wine/drive_c/Program\ Files/PokerStars
wine Pokerstarsupdate.exe

```

also, not all applications work 100% with wine... winehq.com is a good resource, as is #winehq on irc.freenode.net

---

### Post by manutd on 2006-04-27
Cool tks Hollywood,
I'll give that a shot and see how it goes! 

I also think I need to get an updated version of Wine just in case I'm running an older version! Might get rid of some of the bugs! 

Thanks again! :-D

---

### Post by KrazyPenguin on 2006-04-30
Pokerstars works perfect with Crossover 4.2 (but not 5.0).

With WINE the trick is to right-click on PokerStars Lobby when it shrinks (the tab or the actually shrinkage) and choose "Minimize".
Then from the table screen click on "View Lobby" and the lobby will open.

Always open the lobby as soon as you go to a table.  If you leave the table the lobby will remain open as long as you opened it before leaving.

Otherwise you are screwed!!!

Good Luck!!!

---

### Post by KRiSX on 2006-05-01
yes... the only issue i have with poker stars is that the main lobby screen can become next to impossible to access... hitting the show lobby or whatever it says button usually always fixes this problem...

only issue i've noticed with standard wine is that the fonts are damn ugly... tried installing under cedega but the installation fails (although the fonts look a lot nicer on the install program)...

haven't tried crossover... but yeah... to improve the fonts you can of course install the microsoft fonts packages into wine... but its still not perfect

at least you can get ur poker fix in linux :)

---

### Post by bazz-dee on 2006-09-20
I uses to play PokerStars with Wine. But since Kernel-Update yesterday i have some problems. When i go to a table, my mouse will move to the middle of the table and i can't move the mouse out of the window, or even to the leave table button.
Anyone experienced the same problem or has an solution to this ?

---

### Post by DirtDawg on 2006-09-20
I know this doesn't address your particular issue, but I use [pokerroom.com]("http://www.pokerroom.com/") when I want to play. It uses a Java client and even sports a little penguin under its "instant play" option. A Linux friendly suggestion 4 U.

---

### Post by bazz-dee on 2006-09-20
yeah, i know also some other java clients.
but i like pokerstars more than the other sites

---

### Post by scotty2hott2k on 2006-09-20
im getting the same issure, i think its mroe of a wine issue (since i only got it after updating to latest) rather than a kernel issue

---

### Post by blacha on 2006-10-02
clicking view lobby -> main lobby brings it back to normal.

---

