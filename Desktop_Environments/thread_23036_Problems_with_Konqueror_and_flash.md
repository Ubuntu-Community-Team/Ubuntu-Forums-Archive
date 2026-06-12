---
title: "Problems with Konqueror and flash"
date: 2005-03-30
forum: Desktop Environments
---

### Post by Randabis on 2005-03-30
I've being trying to get flash working in Konqueror with no luck for the past few days. I go into Configure Konqueror, navigate to plugins, and add the paths to my flash plugins for mozilla suite (~/.mozilla/plugins, /usr/lib/mozilla/plugins), and tell it to scan for new plugins. I then go to the plugins tab and it says "Netscape Plugins"...So I try a flash site, no dice; it asks me to download the plugin. Has anyone had this issue, and what can I try to fix it?

Thanks in advance. I've presented this problem in several IRC channels and have not been able to solve it so I'm bringing it here. :)

edit: I solved the problem on my own finally. Apparently, it does not like you to use ~. I used the direct path /home/randabis and it worked.

Mods can do what they want with this. I attempted to delete it, but I don't think it will let me.

---

### Post by lao_V on 2005-04-13
[QUOTE=Randabis]
edit: I solved the problem on my own finally. Apparently, it does not like you to use ~. I used the direct path /home/randabis and it worked.

Mods can do what they want with this. I attempted to delete it, but I don't think it will let me.[/QUOTE]

Well done for solving the problem! don't delete the post, allow others to find a solution to the problem!

---

### Post by neonleif on 2005-04-25
[QUOTE=Randabis] I attempted to delete it, but I don't think it will let me.[/QUOTE]
 Yeah, thanks for not being able to delete this post! :D

It did help me, only I didn't specified any paths. 
I just opened Konqeror config, browsed to plugins and discovered that $HOME/.netscape/plugins was on the scan-list. 
Then i told it to scan and *BAM* i got Flash in Konqueror.

---

