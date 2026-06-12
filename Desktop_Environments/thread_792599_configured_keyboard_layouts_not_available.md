---
title: "configured keyboard layouts not available"
date: 2008-05-13
forum: Desktop Environments
---

### Post by nikosm on 2008-05-13
Dear community,

I have customized my keyboard according to this guide:

[http://ubuntuforums.org/showthread.php?t=188761&highlight=layout]("http://ubuntuforums.org/showthread.php?t=188761&highlight=layout")

This layout worked fine with gutsy. I also added two further layouts (without changing them). Now, after reboot they do not seem to be available:

 - left alt + shift doesn't do anything (yes, I configured it to be the layout switching combination)
 - clicking with the mouse on the keyboard layout indicator switches to the next group, but when I type it's still the old one.
 - only two out of three groups are rotated through when I click with the mouse
 - right clicking on the keyboard layout indicator and clicking "show current layout" opens the usual window with the buttons but it is empty! (see attachment)

Is there some daemon that doesn't get started? Any ideas on how to diagnose the problem?

Thanks a lot,
Nikos

---

### Post by hermes0710 on 2008-05-13
Hi,
  remove the keyboard layout, restart gnome and see if this still happens. Is this a clean install or upgrade? In case of upgrade, old settings might be incompatible with hardy

---

### Post by nikosm on 2008-05-13
> **hermes0710 said:**
> Hi,
  remove the keyboard layout, restart gnome and see if this still happens.

Hi Herme,

Thanks for the suggestion. When I was trying to do what you suggested, I saw that the layouts were being recognized correctly. Anyway, I removed my layouts and added "USA default" and rebooted, there was no problem. I then added again my own layouts and removed the "USA default", again without problems.

It's nice if the error disappeared, but I would realy like to understand how and why... What should I do if this happens again? Is there a deamon / service responsible for the keyboard layouts that I could try to restart?

Thanks again,
Nikos

> Is this a clean install or upgrade? 

It's a clean install.

---

### Post by nikosm on 2008-05-14
The problem reappeared, exactly as described above.

---

