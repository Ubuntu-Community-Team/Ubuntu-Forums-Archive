---
title: "How-to force apps to launch on primary screen"
date: 2006-04-21
forum: Desktop Environments
---

### Post by Phesto on 2006-04-21
First, i must apologize because i know i've seen the solution on this forum before but searching today i've been unable to locate it again. I have a standard xinerama setup with my secondary screen Leftof my primary screen. And it seems that most applications want to launch on my secondary screen. I don't know if this is due to the fact that it's treated as one big desktop and a window's position is initialized at something like 100 X 100 which would then put it on the left (secondary monitor). If this is actually the case it would be interesting to see if just switching my monitors and setting the xorg.conf to be "secondary" Rightof "primary" would fix it. But I would also like to know if it's possible and how-to actually go about forcing all applications (or an app-by-app scenerio) to launch on the primary screen. 
Thanks in advance.

---

### Post by henriquemaia on 2006-04-21
[QUOTE=Phesto]First, i must apologize because i know i've seen the solution on this forum before but searching today i've been unable to locate it again. I have a standard xinerama setup with my secondary screen Leftof my primary screen. And it seems that most applications want to launch on my secondary screen. I don't know if this is due to the fact that it's treated as one big desktop and a window's position is initialized at something like 100 X 100 which would then put it on the left (secondary monitor). If this is actually the case it would be interesting to see if just switching my monitors and setting the xorg.conf to be "secondary" Rightof "primary" would fix it. But I would also like to know if it's possible and how-to actually go about forcing all applications (or an app-by-app scenerio) to launch on the primary screen. 
Thanks in advance.[/QUOTE]


I know this is not you are asking, but if you use **alltray** you can use its **geometry** option to get the app open on the spot you want. Even if this does not help, you got a free bump for your post.

---

