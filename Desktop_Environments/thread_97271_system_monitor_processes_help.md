---
title: "system monitor processes help"
date: 2005-11-30
forum: Desktop Environments
---

### Post by xdustin on 2005-11-30
[FONT=Lucida Sans Unicode]Hello World,
I am a long time M$ user, and have been running ubuntu 5.10 exclusively for over a month now. Having a great time on this learning curve :D

My system monitor shows two /usr/bin/gdm processes running.
Is this normal? If so, can someone explain why ubuntu needs both?

Also, what is the Priority "nice" data meaning? (eg. Priority High -nice -4)

I am looking to understand in more detail what each process is and what it does.

Thanks for any assistance!
[/FONT]

---

### Post by Xian on 2005-11-30
[QUOTE=xdustin]
Also, what is the Priority "nice" data meaning? (eg. Priority High -nice -4)[/QUOTE]
Nice is the setting for how resource intensive an application is on your system. The lower the number the more aggresive it is in using your resources. A setting of zero would be "average".

---

### Post by GeneralZod on 2005-11-30
As per the two copies of gdm: I'm running Kubuntu, and have two copies of kdm running, so I'm guessing this normal, but don't quote me on that ;) I remember Mandrake 10.1 would always keep two copies of mdkdm running, too, but I'm not sure what this gains you.  Perhaps if one crashes, the other takes over...?

Anyway, the "nice"-ness of a process is roughly a measure of its "priority" - when several apps are all vying for CPU time, high priority apps will be given the most, whereas low priority apps will be passed over in favour of the higher ones.  The "Folding At Home" client uses 100% of your CPU but runs at such a low priority that it yields in favour of other apps as soon as they request it - in fact, just waggling your mouse around while F@H is running will decrease its usage from 100% to about 90% :)

---

