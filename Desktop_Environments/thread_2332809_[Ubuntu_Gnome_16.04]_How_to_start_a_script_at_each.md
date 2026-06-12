---
title: "[Ubuntu Gnome 16.04] How to start a script at each login?"
date: 2016-08-04
forum: Desktop Environments
---

### Post by actionmystique on 2016-08-04
I've unsuccessfully tried to call it from ~/.profile.
Any suggestion?

---

### Post by ajgreeny on 2016-08-04
What is the script and what do you expect, or want, it to do?
It might be useful to show us the script content, removing anything personal to you that you want kept away from public view.

Does it need to run as root?  If so you will need to think again.

Tell us in more detail everything you are trying to do and we will try to help you.

---

### Post by mdbratch on 2016-08-04
> **actionmystique said:**
> I've unsuccessfully tried to call it from ~/.profile.
Any suggestion?
Can you clarify "unsuccessfully"? How did you try to call it? Was the script file marked executable? Was it in your current PATH, or in the same folder as `~/.profile`?

---

### Post by actionmystique on 2016-08-06
Thanks for your answers. I realized afterwards that some of the commands needed to be run as root, so it's my mistake.
I've removed the call from ~/.profile and installed a daily cron job for the user root through **gnome-schedule**, rebuilt from sources since it has disappeared from the latest Ubuntu 16.04.

---

