---
title: "Ubuntu, Xubuntu and update notifications"
date: 2005-12-31
forum: General Help
---

### Post by Suger on 2005-12-31
I am more and more dropping Gnome for XFCE (not that I have ressources problem, but I do like XFCE...), but there is one question I haven't find the answer to : In plain ubuntu, whenever there are updates available, I get a notification in the systray. Can I get the same "service" in XFCE ?

---

### Post by DaMasta on 2005-12-31
You can run update-notifier and it should load in the tray. Mine loads an extra space though. It's like a gap of nothingness.

---

### Post by Galoot on 2005-12-31
[QUOTE=Suger]I am more and more dropping Gnome for XFCE (not that I have ressources problem, but I do like XFCE...), but there is one question I haven't find the answer to : In plain ubuntu, whenever there are updates available, I get a notification in the systray. Can I get the same "service" in XFCE ?[/QUOTE]
I don't know if there's another package like it (and someone please mention it if there is!), but I just use Gnome's update-notifier in Xfce.

[LIST=1]
[*]Add the Systemtray to your Xfce panel if you haven't already.
[*]Hit [ALT]+F2 and type "update-notifier" and click on "Run" (assuming you still have update-notifier installed, of course).
[*]Notice that your Systemtray has widened. The notifier actually takes up a bit of panel space whether or not there are updates.[/LIST]
Caveat: I can't swear that this actually works, as I've been messing around a lot with Aptitude lately and have manually pulled in a lot of updates.
[edit: Yes, it works.]

---

### Post by Suger on 2005-12-31
Thanks, m8s

---

### Post by Suger on 2005-12-31
Oh, by the way, while I'm asking stupid questions : how do I stop xfce from asking me my password when I shutdown ? I guess I should set a NOPASSWD in sudoers, but as I don't know which command it invokes, I don't want to go messing around to much.

---

