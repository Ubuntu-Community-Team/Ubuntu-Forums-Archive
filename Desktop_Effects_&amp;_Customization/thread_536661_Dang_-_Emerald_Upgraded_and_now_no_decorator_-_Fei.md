---
title: "Dang - Emerald Upgraded and now no decorator - Feisty 64"
date: 2007-08-28
forum: Desktop Effects &amp; Customization
---

### Post by Applegeek on 2007-08-28
Had _everything_ working with the -100 NVidia drivers with Beryl and Emerald 2.1...NVidia 7100 card on Amd64 Feisty system.

I made the mistake of upgrading Emerald - and I can see the themes in the Emerald manager, but nothing I can do  will make the decorator come on.  Whenever Emerald is selected for the windows decorator, the windows border is missing.  If Metacity is selected, everything works fine.  Beryl is working fine, the cube spins, windows wobble, etc.

Any clues?  I've played around with various changes to xorg.conf, but nothing has produced any result.

Are we supposed to upgrade to Compiz Fusion now to use Emerald 5.2 or ????  It seems like there's a lot of problems with this lately...

---

### Post by Applegeek on 2007-08-29
I fixed my CF install by doing this:

Go to Synaptic package manager, and removed ALL references to compiz, beryl, emerald, and all their dependencies.  Reboot machine, then reinstalled CF using Kevin's guid, and all is running really swell again.

---

### Post by spaceship.rodeo on 2007-08-30
This happened to me when I first installed CompizFusion.  First in the terminal type ```
compiz --replace -c emerald &
```
and that should change the window borders to you Emerald theme.  If it does, hit Alt-F2 and enter the same thing, and you should be set to go.

I don't know if you'll need it, but to make sure your theme gets applied each time you boot, go to System > Preferences > Sessions, and on the Startup Programs tab, select "New."  Enter Compiz for the name and ```
compiz --replace
``` for the command.  Make another new one, and put Emerald for the name and ```
emerald --replace
``` for the command, and you should be good to go.

---

