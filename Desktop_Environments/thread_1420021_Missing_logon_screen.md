---
title: "Missing logon screen"
date: 2010-03-02
forum: Desktop Environments
---

### Post by subratabiswas on 2010-03-02
Hi,

I re-installed ubuntu-desktop after trying kubuntu. Now I do not get the logon screen after rebooting the machine. The machine used to work using gnome before I tried kubuntu. After booting, the screen shows something similar to a dark stage with a purple floodlight from the top. The mouse pointer shows and responds to mouse movement. I tried re-installing gdm. ctrl-alt-f1 shows the text mode logon prompt and allows me to logon successfully.

Can you please help?
Thanks.

---

### Post by Barriehie on 2010-03-07
> **subratabiswas said:**
> Hi,

I re-installed ubuntu-desktop after trying kubuntu. Now I do not get the logon screen after rebooting the machine. The machine used to work using gnome before I tried kubuntu. After booting, the screen shows something similar to a dark stage with a purple floodlight from the top. The mouse pointer shows and responds to mouse movement. I tried re-installing gdm. ctrl-alt-f1 shows the text mode logon prompt and allows me to logon successfully.

Can you please help?
Thanks.

See if this link helps: (only need the term. to fix it!)
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by subratabiswas on 2010-03-10
> **Barriehie said:**
> See if this link helps: (only need the term. to fix it!)
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Thank you very much for your help. Followed the link and executed the commands mentioned there. Many objects got removed and some new were installed. The situation after reboot remains the same though.

Thank you sincerely for your kind help; looking forward to some more leads.

---

### Post by subratabiswas on 2010-03-12
Executed gnome-control-center and chose 'Login Screen' option in the window that popped up. Another smaller window popped up, where I clicked on the unlock button. Had to install newer versions of glib and gtk on the way.

It appears that logon was locked, which ggot unlocked by the above sequence. Things are working fine now.

---

