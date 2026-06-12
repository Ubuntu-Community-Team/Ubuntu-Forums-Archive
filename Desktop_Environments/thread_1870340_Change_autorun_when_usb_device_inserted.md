---
title: "Change autorun when usb device inserted"
date: 2011-10-27
forum: Desktop Environments
---

### Post by boardman on 2011-10-27
Hi all,

I have recently upgraded to Oneiric Ocelot which went pretty smoothly aside from some issues I have now with Ubuntu automatically running apps when devices are inserted.

My main problem relates to my iPod. If I plug the iPod in while virtualbox is running a windows install the ipod correctly appears in 'windows'.

If I plug the ipod in and virtualbox is not running ubuntu starts to try to sync the ipod to something (I only know this because the ipod says it is syncing). The result is that it wipes the ipod.

I have no idea where to find out either which application is syncing or how to stop it from doing this without risking my ipod data again.

I would really appreciate it if anyone knows where I can find the list of devices and default behavior so I can edit it, or really any ideas on how to fix this.

Thanks!

---

### Post by Healey on 2011-10-27
Hi
Not sure if it is what you are looking for but, you could try this:
Open File Browser (Nautilus) then Edit, then Preferences, then Media Tab

Please note I am using Lucid Lynx so things may have changed in newer versions !

You can then select what you want ubuntu to do with inserted devices

Not sure how this will affect Virtual Box though !

Good Luck

Healey

---

### Post by boardman on 2011-10-28
Thanks Healey,

Bad news is they have changed it for Ocelot. If I follow your instructions there is no media tab.

Good news is that your post gave me some new words to try in a google search and I managed to find where the default behavior _is_ set.

Control (in the top right of the screen) > System Settings > Removable Media.

In my case it already said "Music Player" - "Do nothing" but I tried ticking the "never do anything with anything" box and it made my problem go away.

Not sure why I had the problem given the settings already but at least I know where to look now.

Leslie

---

### Post by Healey on 2011-10-28
Hi

OK - Sorry I could not help further - I tend to play it safe these days and stick with the LTS versions of Ubuntu as the come out. 

I am pleased that you found a solution

Healey

---

