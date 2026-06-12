---
title: "compiz/xgl not working again"
date: 2006-09-17
forum: Desktop Environments
---

### Post by mwolfe on 2006-09-17
Alright so i booted up yesterday and compiz has not window borders.. A few days before someone posted a fix to add something like
/usr/bin/startcompiz to the startup.  I did this, and i also deactived the old script that started compiz. I wasnt sure if i was supposed to deactive the other one or not.. but the weird thing is that it worked fine after i did that. Then a day or so later it doesnt work again. I dont know what is wrong.   i've tried starting the gnome-window-decorator with no luck

and unforuntely i can't open another window while typing this message so i dont remember exactly what the error said, something about --replace.

I have my video drivers installed just fine, using radeon x600 graphics. Does anyone know what might be wrong, or can point me in a tutorial that is up to date on the instructions. I love xgl/compiz and i'm happy people are actively working on making it better, but its starting to bug me how the developers break it every other week.. hopefully they'll get all the bugs worked out soon so we don't have to go through this..

---

### Post by The Pinny Parlour on 2006-09-17
Follow this thread:
[http://www.compiz.net/topic-4511-update-just-trashed-compiz-xgl](http://www.compiz.net/topic-4511-update-just-trashed-compiz-xgl)

Basically, I went into Synaptic Package Manager and reloaded everything.  I then searched for compiz.  It listed a heap of things and I just marked for installation the following:
csm, compiz, compiz-core, compiz-gnome, compiz-plugins, compiz-manager, cgwd and cgwd-themes
Even if I had them installed I marked them for reinstallation.  I had never used the cgwd-themes before, I like them very much.  Make the window borders a darn sight better.

Don't use /usr/bin/compiz-start anymore, instead code in terminal:
```
compiz-manager 
```

---

### Post by mwolfe on 2006-09-18
Alright i got it working. What happened is that first compiz got broken, i fixed it and a day or so later the kernel got updated
i forgot that with the ATI proprietary driver i have to recompile the driver into the kernel when i do a kernel update. I actually ended up redoing my compiz install completely taking the updated instructions from 
[http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)
using method 2, and compiled the ati drivers into the kernel and all is well.

Thanks for your help

---

