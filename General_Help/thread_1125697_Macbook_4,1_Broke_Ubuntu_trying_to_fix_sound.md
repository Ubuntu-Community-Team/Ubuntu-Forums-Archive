---
title: "Macbook 4,1: Broke Ubuntu trying to fix sound"
date: 2009-04-14
forum: General Help
---

### Post by queerperson on 2009-04-14
Hello

For some reason I changed the home directory of the my main user account. I didn't change it back properly, and now it states that I don't own it, and I can not get into the GUI.

Can I fix this? 

This started because I want to change the etc/modprobe*/options file because a site told me to because my sound doesn't work, and the machine said I can't because I don't have sufficient permission and I said, we'll see about that, and now we've seen and I need help.

Thanks!

---

### Post by James_Lochhead on 2009-04-14
Yea you can. It is not such an easy thing to do though if you are a beginner because you have to use the terminal.

[LIST]
[*]When grub pops up (you might need to press esc), choose the option for recovery.
[*]Another screen will pop up in a few minutes. Choose root terminal here.
[*]In the root terminal type:

```

chown -R <your_username>:<your_username> /home/<your_username>/

```
Then press enter.
[*]Now type exit and press enter.
[*]Choose the option to resume boot.
[/LIST] 

If for some reason you so not have the grub entry you can use a live cd with a terminal to do this as well. Just pop sudo in front (sudo chown etc).

---

### Post by queerperson on 2009-04-17
Thank you very much

---

