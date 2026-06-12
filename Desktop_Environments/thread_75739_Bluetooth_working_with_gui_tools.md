---
title: "Bluetooth working with gui tools ?"
date: 2005-10-14
forum: Desktop Environments
---

### Post by YanH on 2005-10-14
Has anybody managed to get Bluetooth working using the gnome desktop tools? I have installed gnome-phone-manager and using a usb bluetooth dongle my Desktop it is able to sucessfully talk to my Nokia Mobile but is never able to authenticate, entering of the pin always fails:( . I am able to succesfully connect using the command line. 

Additionally once you are connected there is no sign of the connection in the places menu or in nautilus. There is no option such as 'Send to Bluetooth'. Is this correct ?

---

### Post by GeneralZod on 2005-10-14
Does your computer prompt you for the PIN number? Both your phone and your computer should do this.

---

### Post by YanH on 2005-10-14
No it doesn't. The phone prompts for the PIN there is then a pause for a few seconds and then the connection fails.

---

### Post by GeneralZod on 2005-10-14
[QUOTE=YanH]No it doesn't. The phone prompts for the PIN there is then a pause for a few seconds and then the connection fails.[/QUOTE]

Aha - I had this problem with kdebluetooth - you have to alter a setting called something like "PIN helper" in one of the config files.  It's easily fixable, but unfortunately I'm away from my computer at the moment :( Hopefully this post will act as a clue to someone else so they can solve your problem before I get back home in 8 hours time!

Edit:

A stopgap solution would be to hard-code a PIN for your computer; use

```

sudo gedit /etc/bluetooth/pin

```

and change the number there to another 4-digit number.  Enter this as the PIN on your phone and you should be good to go.

---

### Post by YanH on 2005-10-14
Thanks for that. I'm at work at the moment so I'll give it a go when I get in this afternoon.

---

