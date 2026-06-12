---
title: "nm-applet in secondary x-screen"
date: 2012-06-26
forum: Desktop Environments
---

### Post by Birbone on 2012-06-26
First of all hello to everybody, as this is my first post here!

Then the problem, for which I really need your help.
I'm running Ubuntu Lucid 64 in a dual screen set up, TV and PC monitor in different rooms with x-screen nvidia drivers, it was not easy but now it works like a charm except for one thing: no way to have the nm-applet on the second monitor. I really searched everywhere but I only found unresolved bug reports.

Clearly the notification area is also in the second TV screen, but it remains completely empty unless I kill nm-applet and then start again from a terminal in the second screen. Is there a way to have the network manager applet on both screens??

By the way I need it for a UK VPN, and I need to connect and disconnect from the TV screen depending on the channel I'm watching, even a workaround to manage the VPN connection without nm-applet would be really appreciated!!

Hope to hear from you soon

Ciao, Birbone

---

### Post by Birbone on 2012-06-29
Looks like there's no solution, and with all its other flaws this confirm me that x-screen and nvidia drivers are really badly made. But as far as I know it is the only way to have two screens with different resolutions without resizing similar  tricks...

By the way I did find a workaround that could be useful for somebody: with nmcli (a command-line tool for controlling NetworkManager) I created 2 launchers to connect and disconnect the VPN.
It was not easy to have the launchers in the second screen, I had to create them in the first screen, move in a folder, open nautilus in the second screen and then move the launchers from the folder to the second screen.

Maybe not so snappy, but at least now I can laze on the couch!!

---

