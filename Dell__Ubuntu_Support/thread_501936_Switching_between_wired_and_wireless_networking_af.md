---
title: "Switching between wired and wireless networking after hibernation (E1505N)"
date: 2007-07-15
forum: Dell  Ubuntu Support
---

### Post by secret901 on 2007-07-15
I was using my laptop with a wired connection when I put it in hibernation.  When it's back on again I'm in a different location with no wired connection, so I want to use the wireless connection.  However, there's no way for me to switch to wireless!  I tried rebooting the laptop, turning it off and on again, etc, but I'm still stuck in wired mode.  Now my laptop can't get online!  

Thanks

---

### Post by scrooge_74 on 2007-07-16
are you using network manager? Set the cards in the network section of the System administration to roaming mode so network manager can handle conections from the panel on your desktop.

If at this time you are stuck check what details you have in /etc/network/interfaces

I had the same kind of problems until I got the hang of it

---

