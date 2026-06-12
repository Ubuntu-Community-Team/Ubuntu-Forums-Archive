---
title: "Intrepid Upgrade Broke Bluetooth"
date: 2009-01-11
forum: General Help
---

### Post by John Jason Jordan on 2009-01-11
On Hardy x86_64 I had a bluetooth mouse that used to disconnect every few days. I could reconnect it from the command line with hidd --connect <address>. I also have a Sony BT-50 bluetooth audiophile headphones that worked flawlessly.

After upgrading to Intrepid the mouse no longer disconnects. Yay! But the headphones no longer work at all. Worse, the blueman utility that I used to use to pair things up no longer works and Synaptic just lists an option to uninstall, not to reinstall. Furthermore, "hidd" now cannot find the headphones.

I tried System > Preferences > Bluetooth, but it is hopeless. There is no documentation and I can't figure out what the icons mean. The headphones are still listed, but they have a gold star and a key next to them. At the bottom of the dialog box there is a gold star also. Clicking it removes the gold star from the headphones in the list. There is a "Bluetooth Device Wizard," but when I click on Forward it says "Select the device you want to setup" (sic). The only device listed is the mouse. Since the headphones are not listed I cannot select them to set them up.

Note that the mouse is working perfectly. Therefore, the bluetooth device inside the laptop is working fine. And the headphones used to work perfectly in Hardy, so the problem must be due to changes in the way bluetooth is configured in Intrepid.

Can someone tell me what the icons in the GUI mean? Is there a way to set up my headphones from the command line? Is there a way to reinstall blueman? Are there any other utilities for bluetooth on Intrepid?

---

