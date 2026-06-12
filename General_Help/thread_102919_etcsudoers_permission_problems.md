---
title: "/etc/sudoers permission problems"
date: 2005-12-13
forum: General Help
---

### Post by katrielalex on 2005-12-13
Hi all -

I wanted to change the permissions on some of my folders so that my Windows machine could access them, and in the process I accidentally did a recursive *chmod* on /etc. This would have been alright with me - we have a secure network - but unfortunately I cannot now use the *sudo* command as it returns a permissions error (the permissions on /etc/sudoers/ should be set at 0440). I also can't change the permissions as that would require *sudo chmod*... any ideas on what to do or does this require a Ubuntu reinstall?

Thanks in advance,

Katriel

P.S. I don't know if I will be here if you answer so email me if you want to remind me...** ubuntu AT katriel DOT co DOT uk** - thanks

---

### Post by schilcha on 2005-12-13
This is probably a quick-and-dirty approach:

Boot from a live-cd
Mount your harddisk
Change access permissions
Reboot installed system

I used this procedure, when I messed up my root-password back with suse.

Good Luck!

---

### Post by kaamos on 2005-12-13
You could also boot to rescue mode (choose that in grub), and fix the permissions from there.

---

