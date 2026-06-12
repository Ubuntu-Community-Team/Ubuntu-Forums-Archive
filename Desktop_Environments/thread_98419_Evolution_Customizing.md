---
title: "Evolution Customizing"
date: 2005-12-03
forum: Desktop Environments
---

### Post by Sonobull on 2005-12-03
Hi all,

as the subject suggests, I am having some problems with customizing Evolution Mailclient. I was wondering if there is any way to change the looks of Evolution, meaning i.e. smaller Icons, display Icons without text and so on without changing the whole Gnome Theme. Somehow the really easy customizing as with the panels don't work and I didn't see anything in the options Menu that would help.
Plus I am looking for a way to "Minimize to Systray". Is that possible?
Thanks in advance for reading and hopefully answering and helping.

Take care
Sono

---

### Post by ad noiseam on 2005-12-03
[QUOTE=Sonobull]as the subject suggests, I am having some problems with customizing Evolution Mailclient. I was wondering if there is any way to change the looks of Evolution, meaning i.e. smaller Icons, display Icons without text and so on without changing the whole Gnome Theme. Somehow the really easy customizing as with the panels don't work and I didn't see anything in the options Menu that would help.[/QUOTE]

I think the only thing you can customize in this sense is the way the various buttons for each part of evolution (Calendar, Tasks, Mail...) are displayed (either text only, button only, or everything).

[QUOTE=Sonobull]
Plus I am looking for a way to "Minimize to Systray". Is that possible?
[/QUOTE]

I don't think there is such a feature, but you can have an icon and tray notification with this: [http://www.nongnu.org/mailnotify](http://www.nongnu.org/mailnotify) (it is in the repositories).

Nicolas

---

### Post by ahave2005 on 2005-12-03
As for minimize to tray, you can use the application Alltray. Its in the repositories. If you wish, you can use Synaptic.

With this application you can put everything in the tray, its just a click away.

Good luck.
/ahave

---

### Post by Sonobull on 2005-12-03
Ok, thanks you guys.
I found AllTray here : [http://alltray.sourceforge.net/](http://alltray.sourceforge.net/)
Works pretty good, but I would like to activate it when starting evolution rather than clicking on the evolution window now. So I tried adding the command to the starter using:

alltray evolution --component=mail

But that doesn't seem to work. Somebody got any idea what is wrong?
And although I was doing research there doesn't seem to be a way to customize the buttons in evolution without changing the Gnome theme.
Did I miss something? Is there any kind of trick ?

Take care,
Sono

---

### Post by hyg53 on 2005-12-04
> alltray evolution --component=mail

But that doesn't seem to work. Somebody got any idea what is wrong?

try ```
alltray "evolution --component=mail"
```

---

### Post by Sonobull on 2005-12-04
That works :) Thanks m8

Sono

---

### Post by EinZteiN on 2007-05-24
whoaaaaa
i had alltray installed, but the "click the window you wish to minimize" thingie wasn't doing anything!!!
your tip got it working!! :D

thnkx =)
~EinZteiN

---

### Post by DonCoryon on 2008-04-07
[QUOTE=hyg53]```
alltray "evolution --component=mail"
```[/QUOTE]

That worked for me as well.

Nitpicking, but with this code Evolution starts minimized.  Is there a way to adjust the command so that when it's clicked it starts open but minimizes to the tray when closed/minimized?

PS:  I'm new to Ubuntu and Linux, where do you learn these commands?

---

