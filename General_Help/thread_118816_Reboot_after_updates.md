---
title: "Reboot after updates?"
date: 2006-01-17
forum: General Help
---

### Post by Roman27 on 2006-01-17
I haven't been rebooting after updates.  Should I be?  What's the generally accepted practice?

The reason I ask is because today I got home from work and surfed around for a bit on my computer and then a message came up saying that the system monitor applet has shutdown and would I like to reload it.  I have the system monitor and the weather applets on my task bar at the top.  Anyway, clicking reload would only bring up the message again.  So, I clicked the button to not reload.  Then I tried to start up VMWare player and it wouldn't start.  I ran it in a terminal window and it came up with a strange error that one of the libraries couldn't find this or that version of something.

So, I decided to reboot.  The shutdown messages were very strange.  There were a lot of errors and even something that looked like an abend message with hex codes and the whole bit.  It was quite ugly.  I rebooted and everything started up fine.  VMWare runs fine.  System monitor is working just fine in the task bar at the top.  I'm thinking all this trouble was due to not rebooting after such a long time and running updates.  What do you think?

---

### Post by dcstar on 2006-01-17
[QUOTE=Roman27]
.......
I'm thinking all this trouble was due to not rebooting after such a long time and running updates.  What do you think?[/QUOTE]
Maybe, maybe not.

There could be processes running that have (slow) memory leaks, there could have been a power spike that corrupted memory, there could have just been something in your hardware that misbehaved.

---

### Post by matthew on 2006-01-17
A reboot should only be necessary if one of the upgrades involved your kernel. For all other upgrades a reboot is generally not needed.

That said, on rare occasion something weird may happen like what you experienced and a reboot may fix it. I have no explanation.

---

