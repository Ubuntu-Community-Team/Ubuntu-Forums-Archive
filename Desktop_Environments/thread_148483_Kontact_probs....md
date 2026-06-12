---
title: "Kontact probs..."
date: 2006-03-22
forum: Desktop Environments
---

### Post by avantgardaclue on 2006-03-22
kontact is starting to become a bit irritating at the moment! It would appear that i have to press the kontact launch button twice now to load it. It appears to be loading ok but then nothing, so i click the launch button a second time and up it pops in record time!

Now i wouldn't have to keep doing this if it didn't keep shutting (quitting) when i click on the X button. Randomly but about 50% of the time it goes to the 'system tray' and the rest of the time appears to shut completely (quit). I have set it so that the kontact icon appears in the system tray even if there are no unread emails

Is this a KDE problem or a Kontact one? Either way your advice is greatly appreciated.](*,)

---

### Post by Jucato on 2006-03-22
I'm not sure about the first problem that you have, but it might be related to the second.

Kontact doesn't have it's own system tray and depends on the system tray settings of it's individual components, particularly any of these: KOrganizer, KMail, or Akregator. Usually what happens when you close the main Kontact window is that it gets to the background and can be called back using any of the system tray icons of those three parts I mentioned. I think that system tray is on by default in KOrganizer. You can set KMail to have a system tray icon even if there are no new mails (configure KMail > Appearance > System Tray tab > Enable system tray icon, Always show KMail in system tray). Similarly, you can set Akregator to do the same (Configure Akregator > General > Show tray icon).

I'm not sure but probably what happens in your first problem is that when you run Kontact for the first time, it probably runs in the background (probably with KOrganizer in the system tray) and calling Kontact the second time just restores it to be visible.

---

