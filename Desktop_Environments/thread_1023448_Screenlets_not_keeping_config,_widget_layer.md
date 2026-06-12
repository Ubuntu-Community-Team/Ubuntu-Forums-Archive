---
title: "Screenlets not keeping config, widget layer"
date: 2008-12-27
forum: Desktop Environments
---

### Post by RodrigoRodrigues on 2008-12-27
Hi guys, I installed Ubuntu 8.10 Desktop, I'm still fighting with some drivers but I have basic functions running....

I installed some screenlets and I am using some Ubuntu already have, I want to use the widget layer in compiz fusion and I use the cube.

The first strange thing I noticed is that the Widget Layer(I'll use WL) and the cube are kind of independent, if you are using one screen in WL and go back to normal desktop, then change desktop and go to the WL the screen on the WL is the same you were seeing before, it only change when you chance the screen in the WL, at the beginning I didn't like it but now I see it is really better this way...

I started to configure some screenlets, change the size, position and move it to WL but in some screenlets when I restart the config is gone... I tryied to delete the screenlet and config again but it didn't work, so I tried to close it and edit the .ini file in ~/.config/screenlets/screenletname/ but when it starts again it overwrites the file...

any ideas???

at now the ones with this problem are: amarokControl, digitalClock,FeedReader, and only one of two Output I have running

I dont know if there is a limit or something like this, but when I have a lot of screenlets, this start to happens randomly as I add.

Thanks

---

### Post by ChrisB111 on 2008-12-28
I have the same problem, I think it might have something to do with compiz as I think the problem started when I told all my screenlets to not work as widgets. Mine also just lose all their settings.

Chris

---

### Post by ChrisB111 on 2008-12-29
I think telling them to work as widgets somewhat fixes the problem but I still cant add more than 7 as when I do some of them lose their settings.

Chris

---

### Post by RodrigoRodrigues on 2009-01-01
I thought it was an isolated problem, I removed all files from auto-start and .config/Screenlets and started to reconfigure...

after a while the screenlets started to lost the config, I had to work so I just ignored them, after some time It became so  instable that I had to remove all screenlets...

It seems that after it loses its config you cant config back, and the others start to behave the same way in a viral effect, I would like to fix this, I always wanted to contribute with the free software, especialy Linux with some significant modification ou fix, all I did so far was some little patches...

But I am not sure about what exactaly is wrong so I will write a script to reconfig my screenlets every time I login, if it work I will post here, and keep trying to fix it the right way.

I asked a friend to config his pc like mine and he said the screenlets are instable too...

If you are not having this problem try to add something like 20 screenlets distributed to all sides of the cube and in widget layer, see if after logout/in they move or goes back out the WL.

---

