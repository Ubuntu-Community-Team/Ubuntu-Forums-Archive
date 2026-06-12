---
title: "Compiz = No title bars / borders in Evolution only?"
date: 2007-10-26
forum: Desktop Effects &amp; Customization
---

### Post by timbobsteve on 2007-10-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/153458](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/153458) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi All,

I did find a thread regarding this exact issue, but it had been closed because it was talking about a gutsy problem pre-release, ([http://ubuntuforums.org/showthread.php?t=578020&highlight=compiz+evolution+title](http://ubuntuforums.org/showthread.php?t=578020&highlight=compiz+evolution+title))

Basically the problem is with evolution+compiz. When I have compiz enabled and start evolution, there are no titlebars (or they dissappear if I was switching from Metacity). The original thread linked to a bug, but it was no help. Has anyone got anyideas on fixing this problem ?

I am running the latest compiz{-fusion} from the tuxfamily,org repositories and Gutsy gibbon.

Thanks.

-Timbobsteve

---

### Post by bribaetz on 2007-10-26
ts very similar to my problem, 
okay so i install all the stuff for the advanced settings but i messed up my card driver when i messed with it to see if any of them would work because i hadn't read all the threads so my comp is fine at this piont its a little crapy with the video. my card environment thingy will have a blank at the top of the window bar where you move it or close it. so i just disable it and i messed with my driver some more and i also mess with my screen settings size etc. now every time i try to log in it takes me back to the log in screen unless i use the failsafe_gnome thing with out using any extra scripts which would be okay if my mouses left click and right click weren't backwards. by the way my video card is "ATI rage 128" how might i fix this problem.

---

### Post by molgyk on 2007-11-27
Try this link:
[http://www.moleculargeek.net/blog/compiz-fusion-workarounds-for-workarounds.html]("http://www.moleculargeek.net/blog/compiz-fusion-workarounds-for-workarounds.html")

---

### Post by Znort_Ubern00b on 2007-11-27
timbob, what graphics card do you have???

---

### Post by blackcougar on 2007-12-16
I had this too, upgraded from Feisty to Gutsy and had the latest version of Compiz-Fusion. 
First time and every subsequent time I started evolution, while running compiz, it lacked window decorations.
It worked fine when I did metacity --replace but not with compiz.
However turning off the "Legacy Fullscreen Support" option in the compiz workaround plugin fixed it using compizconfig-settings-manager

---

### Post by Cr0wley on 2008-04-20
You're a genius - I installed the fusion-icon package while Evolution was open and it forced it to fullscreen when compiz restarted. Of course, Evolution is not an F11-aware app, so it's been drivng me crazy for the last two days having to alt-tab back to my other apps.

Sorry for rez'ing the old post, but I really hope anyone else suffering from the same problem finds this post

---

