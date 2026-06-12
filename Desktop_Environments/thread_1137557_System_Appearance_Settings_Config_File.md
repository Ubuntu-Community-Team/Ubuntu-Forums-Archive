---
title: "System Appearance Settings Config File?"
date: 2009-04-25
forum: Desktop Environments
---

### Post by BJ_Covert_Action on 2009-04-25
Howdy All,

I recently installed Savage 2 on my Ubuntu 8.04 machine and am trying to get it running without graphical errors. I updated my video card drivers (ATI Radeon 9800 128 MB Pro) using the Envy tool. When I run Savage 2 from either the applications menu or the terminal, the menu screen pops up with numerous pixels set to black that are not supposed to be. The only reason I know this is the case is because most of the menu screen is unreadable.

I have had similar things happen in Stellarium before and noticed that if I go to System > Preferences > Appearance and navigate to the Visual Effects tab, I can turn off all visual effects (using the None option) and both programs will start just fine without any black pixelation issues.

Thus, I would like to develop a workaround for launching these programs by writing a shell or perl script for each one that will both disable Visual Effects and then launch the respective program. However, I do not know where the config file is that the Appearance menu configures to be able to automate editing it.

This kind of thing only started happening after I installed Compiz and, though I have most of the Compiz effects turned off, I think it might have something to do with the issues which is why turning off visual effects altogether is remedying the situation. Anyways, to the point of my question, does anyone know if there is a file that the Appearance GUI edits when changes are made to it? If not, does anyone know of any terminal commands that just automatically toggle visual effects on and off that I could  use to launch Savage 2? If neither of those two options are viable, perhaps I could write a shell script that would exit the gnome desktop entirely before launching Savage 2 and maybe that would do the trick? Any ideas?

I did do some google searching on this and the best thing I found was something called the Compiz switch icon. It looks nifty, but I don't want to have to mouse click it, then mouse click my applications...2 clicks is just too much, I would much rather just mouse click a script if I could :P

Thanks in advance everyone,
Brady

---

### Post by BJ_Covert_Action on 2009-04-26
Update: With the Visual Effects off, Savage 2 runs fine in FPS mode, but in the RTS view, the map doesn't draw, does this help anyone in figuring this out?

---

