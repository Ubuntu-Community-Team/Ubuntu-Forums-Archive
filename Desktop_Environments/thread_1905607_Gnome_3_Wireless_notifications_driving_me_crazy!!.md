---
title: "Gnome 3 Wireless notifications driving me crazy!!"
date: 2012-01-07
forum: Desktop Environments
---

### Post by dewgong on 2012-01-07
I'm really liking the new Gnome desktop, it's sleek and looks cool, However I'm having a problem that is likely gonna make me switch if i can't solve it. I use a usb adaptor to connect to the internet, this means that there are essentially two modems on the computer when i plug it in. the problem is that when i connect to my internet provider with this, the original laptop keeps trying to connect to any network it can find and pops up all the time with notifications that disable what i'm doing. this is ridiculous and I can't turn off that modem without turning of the entire wireless network.


any suggestions, or can i just turn off notifications?

---

### Post by lswb on 2012-01-07
Can you identify the built-in modem or adapter that you want to disable? You could blacklist the driver for it so the system does not recognize it. Open a terminal and run the command ```
lspci | grep -i net
```. Post the output here.

---

### Post by dewgong on 2012-01-07
Ok I figured out the problem. for some reason one of the wireless networks was on auto connect so i went to network manager (the one that lists all the networks you've ever connected to) and deleted it) seems to be working.

---

