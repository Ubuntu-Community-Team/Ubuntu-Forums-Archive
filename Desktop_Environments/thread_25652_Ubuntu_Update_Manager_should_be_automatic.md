---
title: "Ubuntu Update Manager should be automatic"
date: 2005-04-10
forum: Desktop Environments
---

### Post by mathjazz on 2005-04-10
In next release it would be really great if we could have a feature like "Automatic Upadate". It should install all of the updates in background without even asking the user to confirm the update.

What do you think?

---

### Post by Leif on 2005-04-10
I'm not sure I'm a big fan of the idea. Not that it will make a big difference, but I'd rather be the one choosing when to dedicate my bandwidth/cpu to it. Also, I do generally browse thru what's being updated, so if something goes wrong, at least I'd have a starting point.

Then again, I'm not against people having the choice, as long as it remains a choice I can opt out of.

---

### Post by mathjazz on 2005-04-10
It could be optional. Actually it already is, but we have no fancy GUI.

However I think security update should be installed automatically.

---

### Post by paul cooke on 2005-04-11
[QUOTE=mathjazz]In next release it would be really great if we could have a feature like "Automatic Upadate". It should install all of the updates in background without even asking the user to confirm the update.

What do you think?[/QUOTE]

no, never, ever force things on the user behind their backs... however, we could have the update manager icon flash bright red if a major security update has been available for over a week and the user hasn't reviewed the list to ascertain if it should or should not be updated.

---

### Post by mathjazz on 2005-04-11
Why not?

People would like to use computers not maintain them. Just look at the OS X, it updates automatically. The only thing users notices is the icon jumping up and down to show that the update is being made.

---

### Post by yusufk on 2005-04-11
The ubuntu update manager can already auto-download updatable packages, so all that one needs is script to start the install auotmatically,

---

### Post by lao_V on 2005-04-11
I agree. I don't want anyone messing with my computer without my knowledge, be it Ubuntu themselves. 

Notify me when updates are available and I will chose whether I want to install or not!

---

### Post by godsunderstudy on 2005-04-11
[QUOTE=mathjazz]Why not?

People would like to use computers not maintain them. Just look at the OS X, it updates automatically. The only thing users notices is the icon jumping up and down to show that the update is being made.[/QUOTE]

No it doesn't. The security update program comes up, asking you to choose, then download updates.

---

### Post by djg on 2005-04-11
[QUOTE=mathjazz]In next release it would be really great if we could have a feature like "Automatic Upadate". It should install all of the updates in background without even asking the user to confirm the update.

What do you think?[/QUOTE]
 You could simply set up a cron job with the following line:

echo "<SUDOER'S PASSWORD>" | sudo -S apt-get update && sudo apt-get -y dist-upgrade

Obviously this is stupidly insecure, but it's an option.

---

### Post by matid on 2005-04-11
For people interested in Automatic Updates, I made this HOWTO:
[http://ubuntuforums.org/showthread.php?t=25994](http://ubuntuforums.org/showthread.php?t=25994)

---

