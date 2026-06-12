---
title: "Spurious notifications about Slow Keys or Sticky Keys"
date: 2020-05-14
forum: Desktop Environments
---

### Post by &amp;KyT$0P# on 2020-05-14
I got Xubuntu 20.04 VM set up with some launchers on the panel.  Sometimes, if I click one of those launchers quickly after logging in, I see a notification informing me about the state of Slow Keys or Sticky Keys.  Seems random whether the notification is about Slow Keys or Sticky Keys, and whether it says enabled or disabled.  It doesn't reflect system state - checking Settings > Accessibility, both Slow Keys and Sticky Keys are always disabled (by default, and explicitly disabling them doesn't seem to make any difference).

Based on looking at xfce4 Notification settings, it looks like these notifications are coming from "xfce4-settings-helper".

This doesn't happen in Xubuntu 18.04.  Why are these notifications happening in 20.04?

---

### Post by &amp;KyT$0P# on 2020-05-21
I tried deleting my 20.04 install and reinstalling Xubuntu 20.04 from scratch.  This time I made sure to set up the panel as one of the first steps, and test this again before tweaking much of anything.  And this issue still exists.

Is it relevant that this is a VM running in VirtualBox 6.0.22, on a Xubuntu 18.04 host?

---

### Post by &amp;KyT$0P# on 2020-05-24
Asked about this on irc and was told this is probably some bug and it's safe to ignore these notifications.  So this is a minor issue, so knowing I can just ignore this I'm marking this thread solved.

Thanks diogenes_ !  :KS

---

### Post by Yellow Pasque on 2020-05-25
I was hoping you found a better solution than "ignore it" because this was annoying me too. (I'm also running Xubuntu 20.04 in a VM.)
I tried removing as many packages as I could related to accessibility and deleting the sticky keys setting in xfconf. No dice... :(

---

### Post by &amp;KyT$0P# on 2020-05-25
> **Yellow Pasque said:**
> I was hoping you found a better solution than "ignore it" because this was annoying me too.

Well my question wasn't how to stop this as much as "*Why is this happening?  Did I cause this?  Is this a symptom of something been hosed somehow?*".

You could silence the notifications by turning off xfce4-settings-helper in Settings > Notifications > Applications.

---

### Post by Yellow Pasque on 2020-05-26
> **halogen2 said:**
> You could silence the notifications by turning off xfce4-settings-helper in Settings > Notifications > Applications.

Ahhh. Thank you. Now that's what I call a solution!

---

### Post by &amp;KyT$0P# on 2020-05-26
You're welcome :cool:

---

