---
title: "usblp/vmware usb printing"
date: 2006-01-05
forum: General Help
---

### Post by jonathanhayward on 2006-01-05
I have a printer (Lexmark 1100 series) that I want to use either under Ubuntu or under Windows XP via VMware. I can't print under VMware now because VMware detects ucblp doing something with the USB cable, and says "I can't safely take control of the USB port."

Two questions:

1: Have people gotten a Lexmark 1100 series printer working under Ubuntu, and if so how?

2: How can I turn off usblp so that VMware can safely access the USB port?

I'm particularly interested in turning off usblp.

++ Jonathan Hayward, [email]christos.jonathan.hayward@gmail.com[/email]
** To see an award-winning website with stories, essays, artwork,
** games, and a four-dimensional maze, why not visit my home page?
** All of this is waiting for you at [http://JonathansCorner.com](http://JonathansCorner.com)

---

### Post by jonathanhayward on 2006-01-06
No replies?

How can I turn off usblp so vmware will not see the USB port (or is it printer?) as already claimed?

---

### Post by tube on 2006-01-27
You might have already found the solution, but you could try
```
$ sudo rmmod usblp
```
If that helps, just add usblp to /etc/hotplug/blacklist to stop hotplug from automatically loading the kernel module.

---

