---
title: "Dell E7440 Dockingstation Monitor goes black on login to Kubuntu 16.04"
date: 2016-05-21
forum: Desktop Environments
---

### Post by epeedk on 2016-05-21
Whenever I login to Kubuntu 16.04, my monitor connected through a docking station goes black. Sometimes (~50%) it goes black before I comes to the login page. This startet recently.

PC: Dell Latitude E7440
Graphic:
[FONT=monospace][COLOR=#000000]Latitude-E7440:~$ lspci | grep VGA                  [/COLOR]
00:02.0 [COLOR=#FF5454]**VGA**[/COLOR][COLOR=#000000] compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)[/COLOR]

Anyone got any idea of how to fix it. All the issues I could find was about the nvidia driver, which I don't use.

Regards

Michael[/FONT]

---

### Post by epeedk on 2016-05-23
Found a solution:
>   rm -Rf .local/share/kscreen/
>   shutdown -r now

After that the screen works again.

---

