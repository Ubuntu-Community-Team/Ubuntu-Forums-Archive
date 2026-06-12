---
title: "networking icon disappeared on top panel"
date: 2008-11-02
forum: Desktop Environments
---

### Post by billmoseley on 2008-11-02
The icon that showed what wireless network I'm connected to and my signal strength disappeared.  How do I get it back?  I tried right clicking and doing "add to panel"  There is a similar thing I can add, but I'd rather have the default one back.  The new one doesn't say which network I'm on.  I'd rather avoid being on my neighbor's wifi.  Thanks for any help!

---

### Post by Blackwolf_Oz on 2008-11-03
Hi. I think it's Network Manager that's missing. To add it back, press ALT+F2 and enter:
nm-applet --sm-disable
If it still won't show up, perhaps you're missing the Notification Area. To add it back, right-click on the top panel, select "Add to Panel..." and you can find it there.

---

### Post by billmoseley on 2008-11-04
Worked!  Thanks a bunch!

---

### Post by cives on 2011-10-18
> **legend1264 said:**
> Hi. I think it's Network Manager that's missing. To add it back, press ALT+F2 and enter:
nm-applet --sm-disable
If it still won't show up, perhaps you're missing the Notification Area. To add it back, right-click on the top panel, select "Add to Panel..." and you can find it there.

Guy, you saved my life. Nearly one whole year I have been with this problem, I now install the new 11.10 and immediately I lose once again the icon. But I was so lucky enough that all of a sudden I found your solution, hopefully.
Thanks again and best regards.

---

### Post by jmate24 on 2011-10-18
my notification area applet is not there and your trick did not work for me. is there a way to re-install the network manager applet and the notification applet?

---

### Post by cives on 2011-10-20
> **jmate24 said:**
> my notification area applet is not there and your trick did not work for me. is there a way to re-install the network manager applet and the notification applet?

I have lost too my network icon and have not discovered yet how to bring it back to the panel.

---

### Post by notgoingbackto_ms on 2011-10-20
Worked for me too, thanks.

---

