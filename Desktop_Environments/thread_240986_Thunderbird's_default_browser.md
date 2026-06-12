---
title: "Thunderbird's default browser"
date: 2006-08-21
forum: Desktop Environments
---

### Post by jis on 2006-08-21
If I click a link at a mail/news message in Thinderbird, the link is opened in Dillo browser. How can I set links to be opened in Firefox, instead? I have already checked that Firefox is selected in "Preferred Applications", although changing the setting seems to have no effect when I open html files by clicking one on thunar file manager; files are always opened in Firefox.

---

### Post by aysiu on 2006-08-21
Try [this](http://www.ubuntuforums.org/showthread.php?t=60427).

---

### Post by jis on 2006-08-21
Thanks, but I wouldn't touch the Thunderbird-specific file since Dillo is also used to show Gimp's help. I unistalled Dillo. Now Gimp and Thunderbird use Gnome Web Browser, which is IMO better. I wonder why not Firefox is used? Is it because I installed the other browsers later?

---

### Post by jis on 2006-09-05
I unistalled Gnome Web Browser (Epiphany), too. Now links open in Opera. I still wish there were some more elegant way to change used browser since I need to have several browsers.

---

### Post by jis on 2006-09-08
I wonder if this has something to do with xfbrowser4. There is a menu item called "Web Browser" below thunar in my Applications menu, that runs command xfbrowser4. Currently it runs Opera. If I run xfbrowser4 (which is a shell script located at /usr/bin) from terminal, I get the following output:

jarnos@jarnos-desktop:/etc/cups$ ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

---

### Post by jis on 2006-09-08
I found out that xfbrowser4 is sensible to the setting in "Preferred Applications" dialog. So I guess Thunderbird and Gimp are using some other method to launch a web browser. Is the only way to go to set the browser for each application individually?

---

### Post by jis on 2006-09-11
I have answered to the question [here]("http://www.ubuntuforums.org/showpost.php?p=1488004&postcount=24").

---

### Post by jis on 2006-09-11
> **jis said:**
> I have already checked that Firefox is selected in "Preferred Applications", although changing the setting seems to have no effect when I open html files by clicking one on thunar file manager; files are always opened in Firefox.

This is little bit off topic, but the default application for any kind file in Thunar can be changed in the dialog that you can get by right-clicking such a file and selecting "Open With Other Application..."

---

### Post by pressman57 on 2006-12-10
This miss-match between Thunderbird and Firefox has been going on for years in several different distributions I've tried. It seems that since the great majority of the prefs file is written with the gui the preference of which web browser to use should be also. I think it's these annoying little things that are so hard to solve sour many people toward Linux. It's really a bit much to ask a new user to edit a hard to find text file just to use the appropriate browser.

---

