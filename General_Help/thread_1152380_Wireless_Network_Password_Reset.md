---
title: "Wireless Network Password Reset"
date: 2009-05-07
forum: General Help
---

### Post by pete-soper on 2009-05-07
I have a niggling problem, which I would like to solve. I use a Belkin USB WiFi stick for  internet access on my desktop pc (since the cable I installed in the floor broke...).

It works fine, with no glitches - unlike the constant drop outs that I get under Windows. However, every time I boot into Ubuntu, it seems to 'forget' the WiFi network password. I have to go into the manual network configuration for Eth1 (the USB stick), and retype the password over what is already there (which is longer than the password, but I obviously can't see what it is).

Any ideas??

Thanks,

Pete

---

### Post by pastalavista on 2009-05-07
In network manager, edit connections and delete all saved wireless connections. Next time you connect, click the box at top of the setup..'connect automatically'. Enter the password to connect and when it asks for a keyring password, click 'cancel'. No keyring, no password worries.

---

