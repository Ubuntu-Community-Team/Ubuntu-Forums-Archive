---
title: "Editable menu shortcut keys not staying after a reboot"
date: 2008-02-13
forum: Desktop Environments
---

### Post by lmarr28 on 2008-02-13
**[I'm using Ubuntu: Gutsy (Gnome)]**

I want to change the "go forward" and "go backward" shortcut keys in Nautilus.  After going to _System -> Preferences -> Appearance -> Interface_ and checking the "_Editable menu shortcut keys_" box, I go into Nautilus and hover over the "forward" and "backward" menu items and set whatever I want the new shortcut to be.  After I've got them set, I go back and uncheck the "Editable menu shortcut keys" box so I won't accidentally set any other menu shortcuts.

After setting them that way, they work perfectly until I reboot.  After I restart the computer, the two custom menu shortcut keys that I had set are back to their default values.

Why would they be resetting themselves to their default values after a reboot?  Can anyone tell me how I might get them to stay?

For what it's worth, I'm trying to set Nautilus' "back" to keysym F19 (keycode 234) and "forward" to keysym F20 (keycode 233).  These are the two "back" and "forward" keys on my laptop that I have defined in [xmodmap]("http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#xmodmap_configuration").

Thanks!
-Lee

---

### Post by lmarr28 on 2008-02-20
I hate to "bump" a thread, but can anyone help?

Thanks!

---

### Post by mekura on 2008-02-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/151407](https://bugs.launchpad.net/ubuntu/+bug/151407) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Since the bug is '[_incomplete_]("http://news.launchpad.net/general/of-bugs-and-statuses")', any specific information you could give would be helpful.

I'm having the same problem, except that the shortcut keys are reset each session, which I'm guessing happens to **lmarr28** as well. 'gconf-editor' was no help, and Nautilus 2.20.0 is set on hiding access to the default settings.

---

### Post by lmarr28 on 2008-02-27
Interesting.  That sounds like my problem, alright!

Do you know of any other way to re-map hotkeys in Nautilus?  I guess I may have to start a new thread to get this question noticed, but I figured I'd try here first...

Thanks for the head-up on the bug!

---

