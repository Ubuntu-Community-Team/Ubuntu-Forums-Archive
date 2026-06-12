---
title: "Hang on shutdown problem"
date: 2009-04-09
forum: General Help
---

### Post by Rofii on 2009-04-09
I've used Ubuntu and Mint for quite some time now, but have recently run into a troubling problem. Every time I go to shutdown or reboot the computer hangs up and needs powering off via the power button.

This began happening after a reinstall, no upgrades or anything else were applied. Also, I don't know if it matters but I recently installed and then removed a PCI NIC.

I've done some googling and found a suggestion to place acpi=force in the GRUB string, but this doesn't seem to have fixed it either.

Every time I shut down, it brings me to the little graphical shutdown screen where the bar starts full and empties as it shuts down. The bar makes it to the point where it's 1/3 emptied and then hangs for 7-10 seconds before taking me to a black screen with a blinking text cursor.

By trial and error I've discovered that by pressint ALT+F4 I can bring up a prompt that says the following, but will not accept any input:

```
Ubuntu 8.10 user-desktop tty4
user-desktop login:
```

Does anyone have any suggestions on what to try to fix this? As I said, the acpi line in the GRUB did nothing, and that only seems like a workaround anyways. I've used both Ubuntu 8.10 and Mint 6 without this problem before and no new hardware has been installed except that which has been removed. Is there something I should check for in the BIOS or something?

Thanks in advance for any suggestions. Also, sorry about the many paragraph breaks but mt technical communication professor says it's better to use tons of whitespace to keep people from being overwhelmed and not reading lol ;)

[edit]I'm not sure that it matters, but I also tried installing openSUSE 11 and it doesn't have the same problem Ubuntu and Mint are having.[/edit]

---

### Post by maheshasolkar on 2009-04-09
I am sure there are more than a few reasons this could happen. I ran into this problem when I installed Intrepid (Ubuntu 8.10) on my system with a RTL8187 wireless on board component (Asus P5K-e wi-fi/AP). Apparently, rtl8187 driver would not play well with the kernel that ships with Intrepid.

Since mine is a desktop, and I solely use wired Ethernet connection to access the network, it was a simple enough solution for me to blacklist the rtl8187 driver.

May be this helps.

---

### Post by Rofii on 2009-04-09
Yeah, but I don't understand why it would work one day and not the next after a reinstall. No hardware was changed except the NIC I installed and promptly uninstalled. I didn't even upgrade from 8.04 to 8.10 or anything.. it's the exact same disc I used last time.

Could the installation and uninstallation of the NIC have done something to my BIOS? I think I'm gonna try pulling the CMOS battery and see if that fixes anything.

---

### Post by Rofii on 2009-04-09
Oh goodness, I'm ashamed to admit it but simply running mint update fixed this problem. :S I was in such a hurry to try everything under the sun to fix it that I didn't think to take 20 minutes out of my day to let mint update itself :S

Sorry for my nubish mistake lmao

---

