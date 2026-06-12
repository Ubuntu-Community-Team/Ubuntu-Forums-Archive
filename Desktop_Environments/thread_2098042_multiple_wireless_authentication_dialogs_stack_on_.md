---
title: "multiple wireless authentication dialogs stack on top of each other"
date: 2012-12-25
forum: Desktop Environments
---

### Post by smiley1983 on 2012-12-25
I'm maintaining a XUbuntu 12.04 LTS install for someone else.

When the wireless is unable to connect, it brings up a wireless authentication dialog. If the machine is left alone, over time it brings up more of them, creating a massive stack of  windows. These appear to the user as if they are not dying when closed, because there are so many stacked directly on top of each other.

1) Can I prevent it from ever bringing up this authentication dialog at all, and get it instead to continue quietly trying to connect in the background? The dialog is never wanted in this case, as it only creates confusion for the user.

2) Failing this, how can I prevent XFCE from attempting to directly manage the wireless connection, so that I can use a different wireless connection tool which doesn't exhibit this broken behaviour?

---

### Post by offgridguy on 2012-12-25
> **smiley1983 said:**
> I'm maintaining a XUbuntu 12.04 LTS install for someone else.

When the wireless is unable to connect, it brings up a wireless authentication dialog. If the machine is left alone, over time it brings up more of them, creating a massive stack of  windows. These appear to the user as if they are not dying when closed, because there are so many stacked directly on top of each other.

1) Can I prevent it from ever bringing up this authentication dialog at all, and get it instead to continue quietly trying to connect in the background? The dialog is never wanted in this case, as it only creates confusion for the user.

2) Failing this, how can I prevent XFCE from attempting to directly manage the wireless connection, so that I can use a different wireless connection tool which doesn't exhibit this broken behaviour?
I can't answer 1}  But 2} has me curious, What other wireless
connection tool do you have in mind ?

By the way, welcome to the forum.

---

### Post by smiley1983 on 2012-12-25
> **offgridguy said:**
> I can't answer 1}  But 2} has me curious, What other wireless
connection tool do you have in mind ?

By the way, welcome to the forum.

Hi, and thanks for the welcome. :)

I'm accustomed to doing my wireless connections with scripts, directly writing the wpa config files and invoking wpa_supplicant then dhcpcd (dhclient equivalent, I use Arch). So in the worst case, I can tie such scripts into the startup procedure, and then provide the user with launchers which will kill and restart the processes when they have connection trouble or want to switch access points.

However, I hope a better solution might be available using wicd, wifi-select or any of the other tools which invoke wpa_supplicant. Even better, I hope the standard tool has a configuration option I haven't found, or that it's not too hard to switch off the "launch dialog" behaviour in the code and get it instead to pretend the user just pressed "connect".

For my own system, I always end up with scripts, because they just Do What They're Told and never hassle me when things go wrong.

---

### Post by offgridguy on 2012-12-25
Thanks for the answer, i didn't know this option was available.

---

