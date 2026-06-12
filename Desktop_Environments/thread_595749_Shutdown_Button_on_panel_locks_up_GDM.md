---
title: "Shutdown Button on panel locks up GDM"
date: 2007-10-29
forum: Desktop Environments
---

### Post by Fire_Missionary on 2007-10-29
Just as the Topic says:
When I click the Shutdown button on my panel, my whole X Session locks up. Cannot do anything. Alt-F1 then "sudo /etc/init.d/gdm stop" then start again, and it makes it usable.

Any ideas?

---

### Post by Fire_Missionary on 2007-10-29
Das Bump!

---

### Post by Anovadea on 2007-10-29
Hi,

It sounds like the the same problem as I had.

I don't know if this is the same for you, but it turns out that disabling gnome-power-manager from my auto-start broke it for me... turns out I needed it after all ;) You can find out a little more here: [http://ubuntuforums.org/showthread.php?t=583996](http://ubuntuforums.org/showthread.php?t=583996)

Steps to check if this is the problem:
* Go to System->Preferences->Sessions
* Look for "Power Manager"
* If it's not there, then it's most likely the cause of your problem.

If it's not there, just click "Add".

Fill in the fields as follows:
Name: "Power Manager"
Command: "gnome-power-manager"
Comment: "Power Management Daemon"

Click "OK".

Restart your session (this is, hopefully, the last time you'll need to do the bad way), and it should all work!

Hope that's the fix to your problem,
Aoife

---

