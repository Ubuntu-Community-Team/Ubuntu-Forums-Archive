---
title: "Nautilus is set as desktop manager but it doesn't work"
date: 2015-04-12
forum: Desktop Environments
---

### Post by lastopier on 2015-04-12
Hi, I replaced PacmanFM with nautilus, mostly due to Dropbox integration. However, I can get neither PacmanFM nor Nautilus to manage the desktop. I tried to put @nautius -n into ~/.config/lxsession/Lubuntu/autostart, but it doesn't work. Setting it in lxsession-default-apps didn't work either. Is this some kind of bug or I am doing something wrong? Anyone else having similar issues?
PS: I managed to do it on my laptop some time ago, but I have no idea how.

---

### Post by dino99 on 2015-04-12
when you says 'replaced' pacmanFM, did you mean that it was purged ? (might be scary) or is nautilus installed alongside ?
if nautilus does not work, then purge it then reinstall it

---

### Post by lastopier on 2015-04-12
I didn't remove PcmanFM, I tried, but somehow it resulted in lubuntu-desktop being broken or removed(I had to install it in order to jump into standard Lubuntu - I was only able to start Openbox in my login screen).
Nautilus works fine when it comes to file browsing. The problem is that desktop doesn't work and no files are listed. However, when I force it open with nautillus --force-desktop, it starts up. I'll try purging it to see whether it helps.

---

### Post by lastopier on 2015-04-18
So I think I solved this. I think the problem was that I edited ~/.config/lxsession/Lubuntu/autostart as root which resulted in this file being unusable by the system. I changed the owner to me and reset user rights to standard and it seems to work now.

---

