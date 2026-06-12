---
title: "Network Manager"
date: 2006-03-02
forum: Desktop Environments
---

### Post by pchan42 on 2006-03-02
I have installed automatix and it works fine for updates and add-ins.
I have loaded Network Manager with Synaptic, and I cannot find a gui or menu item to start it.  It indicates that it loaded ok, (no error messages)

I have added nm-applet to sessions and startup.

I am new, so what am I not doing correctly?

---

### Post by Ramses de Norre on 2006-03-02
Do you mean the network settings in system > administration > networking?

---

### Post by pchan42 on 2006-03-02
No. Network Manager, which is supposed to display differ wireless networks and allow easy connection.  I have my wireless connected at home, but want to use NetworkManager for road trips to show available networks.

---

### Post by Ramses de Norre on 2006-03-02
What was the package name? Try to type it in terminal to launch it, otherwise: ```
sudo updatedb
locate manager|grep network|less
```
Does it find anything in /usr/bin? That's were it probably is.

---

### Post by pchan42 on 2006-03-02
Will try this evening and respond back.

Thanks

---

### Post by pchan42 on 2006-03-02
Tried both, no results.  /usr/bin did have nm aplet, but not program.  Do I need to try to reinstall?

---

### Post by darkmatter on 2006-03-02
just run nm-applet during a session (run dialog)... does it appear in the panel???

---

### Post by pchan42 on 2006-03-02
How do I do that?  When I am in session what do I type to run nm-applet?

I have it current session, session options, and session startup.

Current session shows restart.  Where does the applet show?

---

### Post by darkmatter on 2006-03-02
[QUOTE=pchan42]How do I do that?  When I am in session what do I type to run nm-applet?

I have it current session, session options, and session startup.

Current session shows restart.  Where does the applet show?[/QUOTE]

well... look in the notification area (systray)... you should see a funny-little-plug icon (kinda looks like an ethernet cable.. sorta)... that would be the applet :)

If not... then Alt+F2 and run the command nm-applet... it should pop up in the tray almost instantly if not running..

---

### Post by pchan42 on 2006-03-02
The applet is now present nest to the terminal display at the top left of the screen, it must have happened whenI tried to refresh the nm-applet in session.

Thanks for your support.  I hope it keeps working.  I am enjoying my experience with Ubuntu (in spite of my lack of knowledge of linux) being a MS user since dos after it replaced cpm..

---

