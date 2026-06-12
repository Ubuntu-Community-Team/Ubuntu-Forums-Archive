---
title: "Another MPlayer question"
date: 2005-02-03
forum: Desktop Environments
---

### Post by gw90se on 2005-02-03
okay, I followed the HowTo and installed Mplayer. Everything went fine....

except....

Everytime I start it or everytime a song starts playing, I get the following error message.

 Cannot load font:  /usr/local/share/mplayer/font/font.desc

Any ideas where to start looking?

---

### Post by Chrisb319 on 2005-02-03
I know this is not going to fix your problem but I personaly use XMMS, it play almost eveything.

---

### Post by gw90se on 2005-02-03
All right, being a newbie I'll ask. Does XMMS play video files too? I thought it was only audio.

---

### Post by buldir on 2005-02-03
I think I had this problem too.  Open up a terminal and type:

# sudo find / -name font.desc

I think I remember finding it in some other mplayer or home directory.  Then create a symlink in /usr/local/share/mplayer/font/ to the full path to the font.desc located by the find command.


Example:
ln -s /place/where/you/found/the/file/font.desc /usr/local/share/mplayer/font/

---

