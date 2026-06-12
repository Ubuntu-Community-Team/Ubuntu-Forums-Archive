---
title: "Help on installing things?"
date: 2009-04-23
forum: Desktop Environments
---

### Post by Logank9k on 2009-04-23
Well, I've just installed Ubuntu, and think it's way better than windows. I'm still learning and could use some help. I looked up some tutorials for installing things, and I tried to install BitTorrent for Linux. ( program that downloads things about 10x as fast ) I get as far as unzipping it and doing the ./configure command, but after that it says:

[FONT=monospace]bash: ./configure: No such file or directory
[FONT=Verdana]
I thought it was a command to configure it on your system, but it's a file I guess. This is very confusing for me, and would be excellent if someone could point out what I'm doing wrong. :D

Thanks in advance, Logan
[/FONT][/FONT]

---

### Post by coffeecat on 2009-04-23
You've downloaded the source code for Bittorrent and you're trying to compile it? Oh dear. Don't worry - a lot of newcomers make the same mistake.

Do you have a good internet connection? Go to Applications > Add/Remove. Select 'All Available Applications' in 'Show'. Search for 'bittorrent', mark it for installation, and 'Apply changes'. That's it. :)

When you've finished exploring Add/Remove, have a look in System > Adminstration > Synaptic.

**Edit:** but if you know all this and **really** want to do it the hard way, you have to cd into the directory that was created when you unpacked the source code package. 'configure' is a small exectable script, and you have to preface 'configure' with ./ to tell bash to run it in the current directory.

---

### Post by Logank9k on 2009-04-23
Ah, thank you very much! It works now.

---

### Post by groovete on 2009-04-23
Transmission-gtk, a lightweight BitTorrent client, is installed by default in Ubuntu. If you prefer Bittorrent you may install it through Synaptic.

---

### Post by coffeecat on 2009-04-23
> **Logank9k said:**
> Ah, thank you very much! It works now.

By the way, I'm sure you've realised this by now, but it needs to be made clear. Add/Remove didn't install what you had downloaded. It downloaded a pre-compiled package of bittorrent. You will probably only need to download and compile source-code for a few unusual apps not in the Ubuntu repositories. Or you may never have to do that at all.

---

### Post by oldos2er on 2009-04-23
> **Logank9k said:**
> Well, I've just installed Ubuntu, and think it's way better than windows. I'm still learning and could use some help. I looked up some tutorials for installing things, and I tried to install BitTorrent for Linux. ( program that downloads things about 10x as fast ) I get as far as unzipping it and doing the ./configure command, but after that it says:

[FONT=monospace]bash: ./configure: No such file or directory
[FONT=Verdana]
I thought it was a command to configure it on your system, but it's a file I guess. This is very confusing for me, and would be excellent if someone could point out what I'm doing wrong. :D
  [/FONT][/FONT]

 What you're doing wrong is you're not using Ubuntu's package manager. See 

[https://help.ubuntu.com/community/Applications](https://help.ubuntu.com/community/Applications)

[https://help.ubuntu.com/8.10/add-applications/C/index.html](https://help.ubuntu.com/8.10/add-applications/C/index.html)

[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

---

