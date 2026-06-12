---
title: "Unity lens freezing, text not inputting"
date: 2016-09-06
forum: Desktop Environments
---

### Post by thenh813 on 2016-09-06
So, I have to oddest problem. It dosen't happen in any other application, except the main search lens of Unity. If I have Firefox and Nautilus open, and then try to search by tapping the WinKey and typing text, either only a few letters of no text appears. Please advise on proper troubleshooting approaches to find the cause of this problem.

Additional info: I use SCIM-Bridge for spellchecking and for inputting characters from other languages. I have a feeling it's related.

---

### Post by thenh813 on 2016-09-06
UPDATE: If I let my computer sit long enough to lock, the lockscreen won't let me type a password. However, if I select switch users, and go the the main logon screen, it allows me to enter my password. The problem also occurs in gedit, but as fas as I can tell affects no other programs yet. I'v always preferred using Geany to edit text anyway. XD

---

### Post by thenh813 on 2016-09-07
I tracked down the problem with a large amount of turning logging options up to max and looking through massive text files. Turns out SCIM, aka Smart Common Input Method, was the cause of the input crashing on the Unity search lens, Gedit and the Login screen. Basically, if SCIM wasn't activated on the lock screen and search, it caused a conflict and froze the input. As the login screen uses the system default and ignores user settings, it was not affected. Other applications such as Firefox were unaffected as they directly used the default input method.
[B]
Solution: Install ibus equivalents (I needed ibus-anthy). Run the command "sudo apt-get purge scim*" to completely remove all program and configuration files of the Smart Common Input Method. **The purge option was absolutely necessary in my case.** Run the command "im-config" and set input method to ibus. Switch to TTY1 (CTRL+ALT+F1) and execute "sudo service lightdm restart" or reboot the computer. After restart of the GUI or a reboot, log in and go into keyboard preferences, add the input methods you desire or install addition ibus plugins beforehand. Remember the default ibus input switch shortcut, or set your own. You can now still use alternate input methods, without the input crashing in Unity, the lock screen or Gedit.[/B]

---

