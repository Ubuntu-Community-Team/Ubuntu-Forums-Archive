---
title: "Installing Drivers- A Ubuntu Newbie..."
date: 2009-03-07
forum: General Help
---

### Post by armaman on 2009-03-07
Hi guys, I'm new to Ubuntu OS (I've just started to use it!) and I would like to know 2 things :

1-How to install my videocard (Nvidia Geforce 6200) drivers ? I go to the "Hardware Driver" option and I click "Activate" and nothing happens!

2- Are my others drivers installed ?

Thanks in advance,

---

### Post by Nano_ext3 on 2009-03-07
Hi,

Your graphics card is the main thing, and probably only (unless you have a wireless card that is not recognized or something extra like a TV tuner card) want to see about installing that.

The best program, hands down, in Ubuntu is EnvyNG.  You can install this by opening up "terminal" in your applications menu, and typing in "sudo apt-get install envyng-gtk" or by using synaptics package manager to find the same.

One installed launch EnvyNG from you applications menu and choose whether you have an ATI or NVIDIA graphics card.  Make sure the option is set to "automatically install driver" as well.  Hit install and hopefully everything will go smoothly.  reboot and you should be good to go.  EnvyNG adds a special function to your repository, so when the EnvyNG developers update the current stable driver, you will receive the new driver in your updates for Ubuntu.

If you want to make sure all hardware is recognized , in terminal, type "sudo lspci -v" and this will show you all your hardware.  Make sure nothing is marked "unknown" in its description.

Cheers!

-Nano

---

