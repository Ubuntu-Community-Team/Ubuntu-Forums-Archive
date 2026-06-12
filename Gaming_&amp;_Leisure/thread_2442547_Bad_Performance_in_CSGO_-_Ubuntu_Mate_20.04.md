---
title: "Bad Performance in CS:GO - Ubuntu Mate 20.04"
date: 2020-05-04
forum: Gaming &amp; Leisure
---

### Post by joaocrespo on 2020-05-04
Hello everybody.

It has been a while since the last time i posted here, but Linux generally just works, so I see this as a good thing :)

Anyway recently i started playing CS:GO, but unfortunately it seems to have some FPS drop in Ubuntu (but not in Windows) during firefights, which takes out a bit of the fun :(

My pc specs are:

[B]CPU - AMD Ryzen 5 1600 Hexa-Core 3.2GHz
[/B][h=4][B]RAM - 16GB (1x16GB) DDR4-2400MHz
Motherboard  - MSI B350M MORTAR ARCTIC
GPU - GeForce GTX 1070 Quick Silver 8G OC 
Screen - SAMSUNG C24F390
[/B][/h][B]OS - Ubuntu mate 20.04 (fresh install)
Nvidia Driver - 440

[/B]I already tried:
Disable Steam overlay
Change the Game to fullscreen (it was fullscreen windowed)
Disable composition (at control center » mate tweak)
All the (have you tried having no apps on the background)

Since this is not a question of the hardware not being able to fully suport the game, and since the game is native to linux, my guess is something related to the Kernel or Xorg.

Any guesses? I already googled a bit and i cant seem to find a satisfactory answer.

Thanks in advanced.

---

### Post by Perfect Storm on 2020-05-04
You could try with gamemode from Feral and see if it boost your performance: [https://www.omgubuntu.co.uk/2019/08/feral-gamemode-ubuntu](https://www.omgubuntu.co.uk/2019/08/feral-gamemode-ubuntu)

---

### Post by mastablasta on 2020-05-05
> **joaocrespo said:**
> 
[B]OS - Ubuntu mate 20.04 (fresh install)
Nvidia Driver - 440

[/B]I already tried:
Disable Steam overlay
Change the Game to fullscreen (it was fullscreen windowed)
Disable composition (at control center » mate tweak)
All the (have you tried having no apps on the background)



there is an issue that appear a month or two ago and i don't think it was ever repaired. it appear sin windows as well but might not be noticeable. it is often not even noticeable on higher end and new  machines. but it is quite bad and very noticeable on the old ones.

anyway what happens is that the short movie shown on the start doesn't actually end but is looping in the background. on better hardware it causes FPS drop that might not be noticeable by user unless checked specifically. on my old PC it dropped them form over 30 FPS to 10 or less. so of course i noticed. anyway the solution is to turn this video off with a command you add to shortcut and also turn off menu animations. once i did that FPS was back up again. another plus side is that the game loads faster when you launch it. i was also able to increase most settings to medium. the negative side is that the menus are now very dark (something like a "browser dark theme") with no background photo (just the guy standing there with his weapon animating the moves). but the point is it the game works great on a 16 year old single core PC. we tried the same on new machine and it also resulted in no sudden FPS drops and increased average FPS. the fix is described on steam forums. i would give you a link, but i don't have access to any gaming sites from work.

edit - found it on Twitter:
> For people who've had massive FPS issues since the operation:

Go to Steam Folder>Steamapps>common>Counter Strike Global offensive>csgo>Panorama


Rename the folder called "videos" to "videos1"


Have -novid in CS launch options


Should fix the drops, increased my FPS with ~100

---

### Post by joaocrespo on 2020-05-05
Thanks for the answers.

**Artificial intelligence** Feral game mode seems to have worked.


**Mastablasta **- I was already using novid, but renaming the video folder seems to have removed clutter :)

---

### Post by Perfect Storm on 2020-05-05
Glad it worked for you. Please mark the thread solved.

regards,

---

