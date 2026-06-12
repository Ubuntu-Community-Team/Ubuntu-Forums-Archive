---
title: "Wine And Ubuntu Don't Really mix."
date: 2010-11-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lorrdavkas on 2010-11-30
I am having major issues getting wine to cooperate with ubuntu. Whenever I go to the Places tab on my start panel, and try to open a folder, wine tells me that there is no directory. Also, when I try to run my software in wine , it does not open up. I went to the wine wiki and to the wine hq forum, but I am still having major issues getting it to work. If someone could help me, I would be greatly appreciative. Thank you much.:popcorn:

---

### Post by akand074 on 2010-11-30
What are you trying to run? It's generally just Wine that is the issue. Did you check your particular software at WineHQ to see if it runs in wine/what parts of it run in wine?

---

### Post by misfitpierce on 2010-11-30
I stopped using Wine for that reason and learned to use just linux alternatives. Been windows app free for a long time myself. Only thing I still see it somewhat useful for is games basically. I experienced similar issues awhile ago on Fedora and Ubuntu though alike so I'm sure its a Wine issue and not a wine+ubuntu issue.

---

### Post by misfitpierce on 2010-11-30
Also what do you mean it does not open the windows application? You have to right click the app to my knowledge now and somewhere in the right click settings you have to check make application executable in order to run them now.

---

### Post by uriel1998 on 2010-11-30
> **lorrdavkas said:**
> I am having major issues getting wine to cooperate with ubuntu. Whenever I go to the Places tab on my start panel, and try to open a folder, wine tells me that there is no directory. Also, when I try to run my software in wine , it does not open up. I went to the wine wiki and to the wine hq forum, but I am still having major issues getting it to work. If someone could help me, I would be greatly appreciative. Thank you much.:popcorn:

It sounds like you've pooched your Wine install;  I have never had a problem such as you describe using Ubuntu 10.04 & Wine 1.2 from the repositories & 1.3.x.  

I'm trying to understand exactly what your problem is - you can't open *any* of the Places using Nautilus?  If so, *you* made Ubuntu do that;  sorry.  Try a full uninstall and reinstall of Wine (not nearly as painful as it sounds).

If you're saying that you can't get to your Documents folder from a Wine program, then you need to change a few things in winecfg.  From a terminal, type
```
winecfg &
```Give it a minute to update.  Then go to the **Drives** tab and point H: to your home directory (mine is /home/steven):

 [ATTACH]177068[/ATTACH]

Then go to **Desktop Integration** and point My Documents at /home/Documents and so on:

[ATTACH]177069[/ATTACH]

---

