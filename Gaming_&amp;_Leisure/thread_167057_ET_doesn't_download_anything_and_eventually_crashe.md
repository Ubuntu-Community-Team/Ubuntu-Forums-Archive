---
title: "ET doesn't download anything and eventually crashes"
date: 2006-04-27
forum: Gaming &amp; Leisure
---

### Post by Kronoz on 2006-04-27
ET runs fine until I try to join a server, it does the connecting to server stuff, but it trys to download the content like maps and stuff but the content doesn't download and eventually the game crashes. I installed PunkBuster as a .run and the game installer also installed it, not sure if the problem is PunkBuster related or not.

---

### Post by minisori on 2006-04-27
Check if .etwolf folder or any folder inside it, in your home has root as owner is so then chown kronoz:kronoz -R .etwolf

I suposse kronoz is your username.

---

### Post by Kronoz on 2006-04-28
Thanks! that fixed my problem.

---

### Post by minisori on 2006-04-28
You welcome :). Youn only have to be careful when using the install script, they all usually give the option to play the game after intall, and most of us always install them with sudo. So the owner of the files created in your home folder is root.

---

