---
title: "Automatically connect to wireless network"
date: 2009-05-23
forum: General Help
---

### Post by Big_Croc7 on 2009-05-23
Network manager doesn't connect to my network automatically when resuming from suspend (either to ram or disk). It does on boot. I have a script to stop network manager and unload the modules before suspending and bring them back afterwards (otherwise it doesn't suspend at all). I can connect to the network manually by clicking on it in the list and entering the wep key, but it's a pain to have to do that every time. How do I make it connect automatically on resume?

Details:
/etc/init.d/NetworkManager restart
then it doesn't connect, but the box for 'connect automatically' is ticked and it works on boot.

---

