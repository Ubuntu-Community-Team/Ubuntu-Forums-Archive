---
title: "xgl and a &quot;how do i&quot;"
date: 2006-09-19
forum: Desktop Environments
---

### Post by whitty on 2006-09-19
Alright, i know there are a million bajillion gazillion guides on this out there, and i'm almost positive at least some of you are sick of this type of question, but how in the heck do i install xgl and compiz on my 6.06 system? That asked, i did this before as par a guide and it worked out fine - the guide i'm pretty sure just ended in having xorg-xgl and all the compiz bits installed, then started compiz with the default session with a .Xsession file in my home dir. This worked fine for me until yesterday when i did a regular update. After a reboot the default xglified session would wig out when redrawing windows as if my graphics card was overclocked way beyond its capacity (i am positive it is not). Needless to say this made my old xgl setup useless and i reverted to the standard session. I want my xgl back though, so i uninstalled everything xgl related figuring i'd follow one of the more recent tutorials accounting for all these new software bits and ways of doing things. There is where i had issues. What guide in the bloody blue blazes do I use?! I can't find one anywhere that is consistent! I guess i only need to know how to actually start compiz properly on a new session, since i think i have everything installed, but i simply cannot figure out how to do it! I know this is not an issue for ubuntu support, as this is not a ubuntu package, but i know many of you have experience with this, and this is the only place i know of to even seek help, so thanks right from the off for even looking at this.

I hope someone can guide me in the right direction, Alex

---

### Post by hellfried on 2006-09-19
> **whitty said:**
> Alright, i know there are a million bajillion gazillion guides on this out there, and i'm almost positive at least some of you are sick of this type of question, but how in the heck do i install xgl and compiz on my 6.06 system? That asked, i did this before as par a guide and it worked out fine - the guide i'm pretty sure just ended in having xorg-xgl and all the compiz bits installed, then started compiz with the default session with a .Xsession file in my home dir. This worked fine for me until yesterday when i did a regular update. After a reboot the default xglified session would wig out when redrawing windows as if my graphics card was overclocked way beyond its capacity (i am positive it is not). Needless to say this made my old xgl setup useless and i reverted to the standard session. I want my xgl back though, so i uninstalled everything xgl related figuring i'd follow one of the more recent tutorials accounting for all these new software bits and ways of doing things. There is where i had issues. What guide in the bloody blue blazes do I use?! I can't find one anywhere that is consistent! I guess i only need to know how to actually start compiz properly on a new session, since i think i have everything installed, but i simply cannot figure out how to do it! I know this is not an issue for ubuntu support, as this is not a ubuntu package, but i know many of you have experience with this, and this is the only place i know of to even seek help, so thanks right from the off for even looking at this.

I hope someone can guide me in the right direction, Alex


this may hopefully provide some clues to your problem. i too had similiar problems of compiz breaking after the latest update. i posted regarding this but no one replied to my post. it is logical to think that not many people were affected by this unlike the previous update that broke x server earlier this month. however if you look hard enough there are sporadic posts of ubuntu behaving weirdly after this last update.
i did 'fglrxinfo' in terminal last night and found that it has reverted back to the mesa driver. as far as i know you absolutely need the ati driver to be installed before attempting to install compiz. i came to the conclusion that somehow the new update had screwed up my previously installed ati driver. rather then going through the whole process of reinstalling the ati driver and not being sure that it might not break something else in the future, i took the corwardly way out and did a clean install of dapper. after completing this i was notified of 20 updates and some of them included the new linux image which was the update that broke compiz. i updated everything anyways and will install the ati driver after i get home tonight and then compiz. hopefully it will work. i will keep you posted on my progress. hopefully some ubuntu gurus will also chip in and help us out.

ps - i follow this thread for installation of ati driver [http://www.ubuntuforums.org/showthread.php?t=143283&highlight=ati+driver](http://www.ubuntuforums.org/showthread.php?t=143283&highlight=ati+driver) and for compiz/xgl i follow [http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389).

---

### Post by hellfried on 2006-09-21
ok i have successfully installed the ati driver and compiz/xgl. both are running again on my dapper. i even updated to the latest ati driver 8.28.8 with this link [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

### Post by whitty on 2006-09-22
So here's a bit of good and bad news: 1. i went to the link you sent for the driver tutorial, and method two worked perfectly, i'm now running the fully accelerated ati driver. Unfortunately though, not one xgl guide i can find seems to work because of what seems to be a repo issue - every single repo i can find that has compiz/xgl on it is now missing cgwd. Where did it go?!

---

### Post by hellfried on 2006-09-22
> **whitty said:**
> So here's a bit of good and bad news: 1. i went to the link you sent for the driver tutorial, and method two worked perfectly, i'm now running the fully accelerated ati driver. Unfortunately though, not one xgl guide i can find seems to work because of what seems to be a repo issue - every single repo i can find that has compiz/xgl on it is now missing cgwd. Where did it go?!

did u follow the second howto in the link for compiz/xgl in my post? you may also find some answers by visiting [www.compiz.net](www.compiz.net).
more specifically try looking at this thread [http://www.compiz.net/topic-4690-where-get-cgwd](http://www.compiz.net/topic-4690-where-get-cgwd)

---

