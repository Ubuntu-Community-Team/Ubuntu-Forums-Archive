---
title: "Running a chess/crazyhouse engine (tjchess) on xboard"
date: 2012-09-25
forum: Gaming &amp; Leisure
---

### Post by linux_dream on 2012-09-25
Hello guys,
I would like to run TJchess 1.1 on xboard. I've already downloaded the linux version in the website ([http://tonyjh.com/chess/](http://tonyjh.com/chess/)).
I think it is a winboard engine, not an UCI one. 
So I've searched how to play against a winboard engine on xboard on this forum and found [quote=shad0w9]U need  to use direct link to crafty, like for exemple:
xboard -fcp "/usr/games/bin/crafty" -fd /usr/share/games/crafty/[/quote] 
So I've tried a similar thing for TJchess but that did not work. I don't understand what are the fcp and fd linking to. Aren'y they supposed to both link to crafty.exe in that case? If so, why is it a different path? Which one is supposed to link to the engine.exe? And to what is supposed to link the other?

I tried ```
xboard -fcp /home/isaac/Games/TJchessFICS/tjchess -fd /home/isaac/Games/TJchessFICS/

``` but it says that the program "/home/isaac/Games/TJchessFICS/tjchess" terminated unexpectedly. 
When I try ```
xboard -fcp /tjchess -fd /home/isaac/Games/TJchessFICS/
``` it says that the program "/tjchess" terminated unexpectedly.
I tried with and without the "'s, it returns the same message. I cannot get it to run on xboard.
Any idea what I'm doing wrong?
Thanks in advance.

---

### Post by TonyJH on 2012-09-29
Hi,

What xboard version?  This command line is working for me.  Could you try it?

xboard -cp -fd "/home/tony/TJchess" -fcp "./TJchess_1.1_linux_32bit"


Or, if the TJchess binary is in your current directory, you don't need the -fd parameter and can try this:

xboard -cp -fcp "./TJchess_1.1_linux_32bit"

---

### Post by linux_dream on 2012-09-29
> **TonyJH said:**
> Hi,

What xboard version?  This command line is working for me.  Could you try it?

xboard -cp -fd "/home/tony/TJchess" -fcp "./TJchess_1.1_linux_32bit"


Or, if the TJchess binary is in your current directory, you don't need the -fd parameter and can try this:

xboard -cp -fcp "./TJchess_1.1_linux_32bit"
Hi Tony! (I am critterbot on FICS, trying to use linux instead of windows). Thanks for helping me.
I tried ```
xboard -cp -fd "/home/isaac/Games/TJchessFICS" -fcp "./tjchess"

``` and I get "error: The first program (/TJchess) terminated unexpectedly". I attach a screenshot, the message appears in xboard, no the terminal itself.
I use xboard 4.6.2.
I tried with and without the "'s, it produces exactly the same error message.
I changed the name of TJchess_1.1_linux_32bit to tjchess and it is in /home/isaac/Games/TJchessFICS for me.

---

### Post by linux_dream on 2012-09-29
Ok guys! The problem was that apparently I had no permission to execute tjchess. So a simple "chmod u+x tjchess" worked.
Thanks a lot Tony!

---

