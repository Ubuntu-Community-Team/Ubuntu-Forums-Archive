---
title: "Fullscreen Bug"
date: 2021-06-17
forum: Gaming &amp; Leisure
---

### Post by strapse on 2021-06-17
Whenever im in a fullscreen application, and i press the "decrease volume" or "increase volume" or "start menu button" on my keyboard, here is what happens in order:
1. It minimizes the fullscreen application
2. I try to re-open the application by clicking it or using the keyboard shortcut, both dont work
3. I try to close the application by right-clicking it in the task bar, that wont register either
4. I try to reboot the system using the dropdown menu in the top right corner, that doesnt even open
5. I realize my mouse isnt inputting anything to the computer, so a force shutdown by holding down the power button is needed
6. After reboot everything works fine until i accidentally press one of those buttons again while playing minecraft in fullscreen and the cycle happens again

Does anyone here have a solution to this?
I tried looking everywhere and it doesnt seem like anyone is having this issue

How to recreate the bug:
1. Open minecraft (or one of its modded clients)
2. Enable fullscreen
3. Press one of these buttons on your keyboard/laptop:
"Increase volume"
"Decrease volume"
"Windows (start) button"
"Increase brightness"
"Decrease brightness"
4. The operating system becomes unusable except after reboot or killing the process somehow without using the mouse

As a person who frequently changes between volumes this is making playing anything in fulllscreen practically unplayable
(I am a newbie in linux if that helps)

Thanks in advance.

---

### Post by mastablasta on 2021-06-18
what OS? which GPU? wayland or the old Xorg (you can choose at login).

it is not an OS issue. it works fine for me and my kids PC also work fine. we are on Kubuntu. they even go as far as running / switching youtube music in background.

---

### Post by k-i-w on 2021-09-02
> **strapse said:**
> [U][COLOR=#000000]Whenever im in a fullscreen application, and i press the "decrease volume" or "increase volume" or "start menu button" on my keyboard, here is what happens in order:
1. It minimizes the fullscreen application
2. I try to re-open the application by clicking it or using the keyboard shortcut, both dont work
3. I try to close the application by right-clicking it in the task bar, that wont register either
4. I try to reboot the system using the dropdown menu in the top right corner, that doesnt even open
5. I realize my mouse isnt inputting anything to the computer, so a force shutdown by holding down the power button is needed
6. After reboot everything works fine until i [/COLOR][[COLOR=#000000]applinked[/COLOR]]("https://applinked.me")[COLOR=#000000] accidentally press one of those buttons again while playing minecraft in fullscreen and the cycle happens again

Does anyone here have a solution to this?
I tried looking everywhere and it doesnt seem like anyone is having this issue

How to recreate the bug:
1. Open minecraft (or one of its modded clients)
2. Enable fullscreen
3. Press one of these buttons on your keyboard/laptop:
"Increase volume"
"Decrease volume"
"Windows (start) button"
"Increase brightness"
"Decrease brightness"
4. The operating system becomes unusable except after reboot or killing the process somehow without using the mouse

As a person who frequently changes between volumes this is making playing anything in fulllscreen practically unplayable
(I am a newbie in linux if that helps)

Thanks in advance[/COLOR][/U].
I am also facing same issue. I am unable fix it till now.

---

### Post by ajgreeny on 2021-09-02
I do not see this happen in my Xubuntu 20.04 either so it is not a normal problem.

Show us the output of terminal command ***inxi -Fzx*** which will tell us a lot about your software and hardware.

---

