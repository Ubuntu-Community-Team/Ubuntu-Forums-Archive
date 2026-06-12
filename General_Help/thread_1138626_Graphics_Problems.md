---
title: "Graphics Problems"
date: 2009-04-26
forum: General Help
---

### Post by Lex-Man on 2009-04-26
I've tried to set a second graphics card into my computer.  So now I have a ati 3850 and x800 running on the same machine.  Although now I can't log into Ubuntu.  I have version 9.4 installed and I used Wubi to install the OS and upgraded from 8.10.  Once I set the second card in my machine and tried to log into Ubuntu the log in screen is just a mess.

I have tried to run the OS with only one graphics card in my machine, this didn't help.

I have run dpkg to reinstall packages as well as fsck and xfix from the recovery menu.

I have booted to the command line and tried sudo dpkg reconfigure server-xorg

this asked me a load of questions about my keyboard!!!

Any ideas what else I could try?

---

### Post by Lex-Man on 2009-04-26
I managed to get back into the gnome IDE by uninstalling all the ATI stuff with

```

sudo apt-get --purge remove xorg-driver-fglrx fglrx-control

```

But now if I try and reinstall the ATI drivers I get the same problem again.

Anyway to stop this?

---

