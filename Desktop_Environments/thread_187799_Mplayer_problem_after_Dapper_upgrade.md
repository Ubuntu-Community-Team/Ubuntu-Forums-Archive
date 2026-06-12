---
title: "Mplayer problem after Dapper upgrade"
date: 2006-06-03
forum: Desktop Environments
---

### Post by fischer98 on 2006-06-03
I upgraded to Dapper from Breezy last night. Everything went smoothly, for the most part. Had to manually reinstall office, which was no big deal. But I have a problem with mplayer. I've tried this on a wma file, wav file, and avi file, all with the same results. When I right-click the file and choose "Play with Mplayer" option, a small error box appears in the middle of the screen, has no text, and disappears in less than a second. I've checked /var/log/messages and /var/log/syslog and found no related error messages. This was working in breezy.

Funny thing is I can still run these files from the command line no problem. Just no right-click, run ability. Any ideas? Where else could I look for error messages? I looked at the modified dates for everything in /var/log, and nothing had been modified since several minutes before the errors.

---

### Post by tonyr on 2006-06-03
You could try reinstalling **mplayer**. In **Synaptic**, search for **mplayer**,
select it, and right-click to get the drop-down actions menu. There should be
an entry there that says **Mark for Reinstallation**.

---

### Post by fischer98 on 2006-06-03
Sorry, should have mentioned that. I'm a windows monkey, so reinstalling and rebooting are standard tools in my utility belt. ;)  Reinstall did not help.

---

### Post by marciano on 2006-06-03
[QUOTE=fischer98]Sorry, should have mentioned that. I'm a windows monkey, so reinstalling and rebooting are standard tools in my utility belt. ;)  Reinstall did not help.[/QUOTE]

If you are using w32codecs, check to see that the /usr/lib/win32 directory actually contains the DLL's. I had to copy them from /usr/lib/codecs (I think) to make things work.

M

---

### Post by fischer98 on 2006-06-03
I don't think I even have a win32 directory there. Guess I can create one without any problems? I'll try that once I get back in front of the computer.

---

### Post by gw90se on 2006-06-04
I am having the same proble, so I'll be watching this thread, too.

---

### Post by learning curve on 2006-06-04
Try and use Automatix to load all your Codecs and re-install Mplayer.  I had the same problem and it worked for me.  :)

---

### Post by unnes on 2006-06-05
I had the same problem with the quick popup window and MPlayer not working after upgrading to Dapper. An uninstallation via Synaptic and reinstallation via either Synaptic nor Automatix seemed to work.

I finally got it working by uninstalling MPlayer, skins, and fonts using Synaptic, and compiling from source. There is a good how-to here:

[http://www.ubuntuforums.org/showthread.php?t=187709](http://www.ubuntuforums.org/showthread.php?t=187709)

After compiling, it worked like a charm, like it always had.

---

### Post by manemannen on 2006-06-06
Same problem here - but I found out that for me it was only that the player didn't have a default Skin. The "/usr/share/mplayer/Skin/default" directory was empty (the last step in the howto mentioned above). Copied another skin in there and then it worked as before.

---

### Post by jturnbul on 2006-06-09
I have the same problem with mplayer complaining about the default skin, and of course the same directory is empty

---

