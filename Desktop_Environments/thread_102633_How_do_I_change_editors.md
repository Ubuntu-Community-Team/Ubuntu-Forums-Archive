---
title: "How do I change editors?"
date: 2005-12-12
forum: Desktop Environments
---

### Post by ardchoille on 2005-12-12
When I type crontab -e, the nano editor opens up, so this tells me that the default editor for my system is nano. I like vi much better. So, how do I make the vi editor the default editor for my system? I tried EDITOR=vi and it worked for that session, but when I rebooted, the nano editor was back. Is there a way to permanently make the vi editor my system default editor?

---

### Post by grendelkhan on 2005-12-12
Let me know when you figure this out - I can't stand Nano

---

### Post by ardchoille on 2005-12-12
[QUOTE=grendelkhan]Let me know when you figure this out - I can't stand Nano[/QUOTE]
Just put this line in your .bashrc, if you want to use vi (for exemple) when you type crontab -e:

```

export EDITOR=vi

```

I added that line at the bottom of my .bashrc file (not the .bashrc file in root's home dir) and it works great.

---

