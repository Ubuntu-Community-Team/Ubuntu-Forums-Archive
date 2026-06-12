---
title: "Dual boot xubuntu/windows 10 - circular xubuntu login"
date: 2019-10-21
forum: Desktop Environments
---

### Post by makem2 on 2019-10-21
I have xubuntu 18.04 dual booted with windows 10 and each time I log into xubuntu the login returns so effectively I am locked out.

I was ssh'ing to a Pi and may have issued a sudo startx command that somehow got to my xubuntu? That is the only thing I can think of which could have triggered this. I am aware I should not startx with sudo but was having problems starting x  from a ttyl log in. Why I ws logging into a gui from ttyl is another story.
 Seems like I have jumped out of the frying pan into the fire! two problems for the price of one lol.

I can get to grub but don't know where to go from there to prevent the circular logging in. I hope someone can get me out of the fire. (I am atually using windows urgh to write this post)

---

### Post by oldfred on 2019-10-21
Can you boot recovery mode? Second entry in grub?

May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by makem2 on 2019-10-21
Thanks oldfred, I did work out how to correct the problems myself.

As you say, via recovery mode, accessing the ~/folder (home) and chowning .Xauthority back to me from root:root.

I learned the chown part whilst tying to log into xfce gui from ttyl (another story)

---

