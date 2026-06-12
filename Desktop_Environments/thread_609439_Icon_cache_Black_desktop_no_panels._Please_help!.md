---
title: "Icon cache Black desktop no panels. Please help!"
date: 2007-11-11
forum: Desktop Environments
---

### Post by SirBlain on 2007-11-11
So I upgraded to Gutsy recently. It's great and perfect. I got the OsX_MoD icon theme and it was okay. Nicest one I saw. After applying it I decided to customize it further. I replaced a lot of icons and noticed the Applications 'Ubuntu' icon didn't change. And found I had to replace it in Tango or something. After getting all the icons to the way I want them I update the icon cache and restart... that's when I saw the error message that read: Could not generate Icon cache. (or something similar) and the entire desktop is black... no panels, can't right click. But Pidgin starts up because it's to do so automatically and Compiz starts up fine. 

The only way for me to access the terminal is to start a failsafe terminal session. 

After that I try things like Sudo gtk-update-icon-cache -f OR -t OR -q and then I type in the icon directory. I've tried different directories like gnome, default, tango, tangerine and of course OsX_MoD. Every time it tells me: Generated cache invalid or Could not find cache..

I really don't know what to do. Due to problems that I can't fix and no one else is willing to I have to reinstall the entire OS. I have for Feisty about 7 times and this will be my 3rd for Gutsy. If I have to do it again I'll just go back to Vista.. I literally had less problems:mad::confused:


The startup message I get after logging on says: The NetworkManager applet could not find some required resources. It cannot continue.

I can see Ubuntu laughing at me. What the funk?

---

### Post by tartley on 2008-01-31
Bump! I see exactly the same thing. When logging in:
  - black desktop
  - no panels
  - pigin starts OK (it is set to autostart)
  - compiz looks slightly weird but seems to be running (I can cube-rotate desktops)

No idea what caused it. Last night I was messing with my Nethack config, so can't see how that could cause it. But I haven't rebooted for ages so presumably it's some old change I made to something.

I can still launch stuff because fortunately I have a keyboard shortcut to launch gnome-terminal from my black desktop (Winkey-T for me, dunno if that's an out-of-the-box default)

Anyone got any clues? I'm not even sure where to look for startup messages to try and diagnose. Thanks.

---

### Post by tartley on 2008-01-31
Correction: That shortcut key for terminal is Alt-T, not Winkey-T.

Anyhow, I fixed the black desktop part, using:
[FONT="Courier New"][INDENT]  sudo pkill -HUP nautilus
  nautilus &[/INDENT][/FONT]
Which were suggestions I saw here:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/148962](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/148962)
(although I wasn't aware of any equivalent update happening)

I have rebooted and the desktop is no longer black - the fix seems to stick. Hooray!

However, I still have no panel / taskbar thingy. I'll hunt around for the equivalent commands that might fix it.

---

### Post by tartley on 2008-01-31
The command:
[INDENT]gnome-panel[/INDENT]
restored my panel, and it stays restored after a reboot.
No idea what caused it, but problem is solved. This has been a lonely conversation. :-)

---

### Post by Tom G Marseille on 2008-03-25
Not exactly the same problem, but I was feeling lonely too and your solution fixed mine.  I still had wallpaper and icons, but no launch / tool bars.  Now they are back, not as I had tweaked them but back nevertheless.

Thanks very much :-)

---

### Post by wdla on 2008-04-02
I bumped into this problem after trying to print a document as a PDF file.  Some process hooked onto Nautilus (I think) looking for some input; probably having to do with name of the PDF file I wanted to create.  I was in a rush and rebooted.  (That will teach me.)

Bugger of a problem to diagnose.  Can't really find a log entry that pinpoints what the problem might be during startup.  You're solution to restarting Nautilus is a hint.

There must be a permission problem of some sort during the user login because killing Nautilus and restarting it as the local user works.  Might also be related to a directory path that Nautilus can't get to until the user is logged in.

Thanks for the pointer.  If my problem persists through another reboot cycle, I've got something else to look into.

---

