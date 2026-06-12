---
title: "server with no monitor gives me a tiny screen...."
date: 2008-12-23
forum: General Help
---

### Post by Kain000 on 2008-12-23
hey everyone, 

I've recently re-configured the way my computers are set up and now I am runing my server without a monitor, using instead vnc to see my desktop over the LAN.   I used this before but my server was connected to a tv so the picture i got over vnc was fine, but now without a monitor the desktop is very tiny and I am unable to raise the resolution as there is no monitor.  does anyone have any ideas?

thankyou everyone

-sean

ps anyone listen to the linux action show?

---

### Post by Titan8990 on 2008-12-23
Have you considered ssh? Typically, you wouldn't log in to a server graphically (vnc, rdp, etc) because it usually wouldn't have a GUI.

---

### Post by dcstar on 2008-12-23
... (slow server response)

---

### Post by dcstar on 2008-12-23
> **Kain000 said:**
> hey everyone, 

I've recently re-configured the way my computers are set up and now I am runing my server without a monitor, using instead vnc to see my desktop over the LAN.   I used this before but my server was connected to a tv so the picture i got over vnc was fine, but now without a monitor the desktop is very tiny and I am unable to raise the resolution as there is no monitor.  does anyone have any ideas?


Try hardcoding the resolution you want in the xorg.conf file.

---

### Post by Kain000 on 2008-12-23
> **Titan8990 said:**
> Have you considered ssh? Typically, you wouldn't log in to a server graphically (vnc, rdp, etc) because it usually wouldn't have a GUI.

yes, originally the server was used as a file server and media center, (why it was hooked into my tv) so I needed the GUI.    and I like the gui as a hand rail if you will, i'm still getting my sea legs for complete command line.

---

### Post by Titan8990 on 2008-12-23
Then give dcstar's suggestion a shot.

---

