---
title: "Audacious starts instead for Nautilus"
date: 2010-07-27
forum: Desktop Environments
---

### Post by Nimo on 2010-07-27
Whenever I try to click any of the places under the "Places"-menu in the panel under Gnome audacious gets started instead. How strange!

Only way to stop it is to uninstall audacious. This seems very strange, it started today and I have no idea of why it started.

Does anyone have clue about how to solve this?

Ubuntu 10.04. Do you need any more information?
I am pretty new to the Gnome environment, I have always been running Fluxbox before.

---

### Post by quixote on 2010-07-30
Somehow, the mimetypes must have become crosslinked. The file /etc/gnome/defaults.list contains all the file associations.  For instance, toward the end in mine is "x-directory/normal=nautilus-folder-handler.desktop".  Somewhere in yours "audacity" or maybe some other sound program is trying to handle directory display functions!  I'm not sure what the solution would be.  I'd try looking through that file and seeing whether anything looked wrong.  You could edit it by opening a terminal and typing "gksudo gedit /etc/gnome/defaults.list" (command without quotes of course).

---

### Post by Linye on 2010-07-30
I had a similar problem but it was VLC what opened when I clicked for Nautilus.

Here's the thread I made. Hope it helps.

[http://ubuntuforums.org/showthread.php?t=1524885](http://ubuntuforums.org/showthread.php?t=1524885)

---

### Post by Nimo on 2010-07-30
Thanks for the replies!

I found the problem with Ubuntu Tweak. When looking for "directory" in File Type Manager it for some reason was "open with audacious" instead for simple "open folder".

I have no idea how that happen. Now it seems to work at least!

---

### Post by quixote on 2010-07-30
Good to hear you got it sorted!  I just had a "D'oh!" moment when I remembered the supposedly easy way of doing this.  Open nautilus (eg by going to Places > Home), right-click on a folder.  It would have probably said "Open with Audacity", and below that "Open with other application."  Choose the second.  A menu of possible applications appears.  If nautilus is there, select it, and tick the "always use this application" box at the bottom.  If not, click the dropdown for "use a custom command", enter "nautilus" (without quotes), and tick the "always use this application" box.

I've used that on occasion, and sometimes it doesn't "take" for some reason, but, for what it's worth, there it is.

---

