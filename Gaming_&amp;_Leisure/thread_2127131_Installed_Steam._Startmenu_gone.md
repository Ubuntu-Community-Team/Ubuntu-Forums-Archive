---
title: "Installed Steam. Startmenu gone?"
date: 2013-03-19
forum: Gaming &amp; Leisure
---

### Post by sshaddoww on 2013-03-19
Hi. Today I installed "Steam" from "Ubuntu Software center". It had the button "Buy" which i found weird because I remember Steam as a free program. Then it started to update and wanted my password. Then I restarted the computer because Steam wanted it. After I logged in to my Ubuntu I saw only the Desktop Background and one icon which was "Steam". The icon Steam did not work, nothing happens when I press it. The problem is that by installing Steam I have made my Ubuntu 12.10 installation useless because my account does not show the Startmenu anymore and the Guest account is sabotaged too. There is no startmenu on the Guest account and the Steam icon is not there. So now I wonder how to fix my Ubuntu 12.10 installation and get Steam working. How can I fix my Startmenu so that the Ubuntu 12.10 installation can be used by me (Im lucky that I had an old ubuntu installation on one of my hdd's)?

---

### Post by myromance123 on 2013-03-19
This sounds more like your graphics driver attempted to be installed/updated in the background, and when you restarted it broke itself. When you install Steam, it also installs Jockey (I believe it's called something else now). This might be the reason.

Do you know how to go into a fullscreen Terminal? You just hit Ctrl+Alt+F4 and you're in the fullscreen Terminal (a.k.a Virtual Terminal).
From here, I'd like you to install this just as a precaution:
```
sudo apt-get install linux-headers-generic
```

After that restart your computer, and let me know if you're still getting only the Desktop Background.

Also, please let me know what graphics card you have. Is it an Intel Integrated card/ AMD ATi Radeon card/ Nvidia card?

---

### Post by sshaddoww on 2013-03-19
> **myromance123 said:**
> This sounds more like your graphics driver attempted to be installed/updated in the background, and when you restarted it broke itself. When you install Steam, it also installs Jockey (I believe it's called something else now). This might be the reason.

Do you know how to go into a fullscreen Terminal? You just hit Ctrl+Alt+F4 and you're in the fullscreen Terminal (a.k.a Virtual Terminal).
From here, I'd like you to install this just as a precaution:
```
sudo apt-get install linux-headers-generic
```

After that restart your computer, and let me know if you're still getting only the Desktop Background.

Also, please let me know what graphics card you have. Is it an Intel Integrated card/ AMD ATi Radeon card/ Nvidia card?
Okay thanks for the reply. I will install like you have said today but right now my PC is updating my old Ubuntu. I have a Nvidia Geforce card.

**Edit:** Okay now I have installed the "linux-headers-generic" and after restart I have my startmenu back. Now it is in a cooler color, it is transparent blue instead of that red color that the original one was.
**Edit2:** Now I have almost everything working. Steam is installed and updated. However it cant show the flash-content. I have successfully started a violent Half-Life modification and could play the game. The textures seemed more crisp than I remember them on Windows.

---

### Post by Perfect Storm on 2013-03-19
To get steam flash to work on 64-bit: [http://www.webupd8.org/2013/01/how-to-get-flash-player-to-work-with.html](http://www.webupd8.org/2013/01/how-to-get-flash-player-to-work-with.html)

---

### Post by efflandt on 2013-03-19
**sshadoww**, if you did not have nvidia drivers installed before, you may find graphics in 12.10 in general being quicker than default nouveau drivers.

**Artificial Intelligence**, that link is the first method that actually gets flash working in Steam on a 64-bit system.  I have been running Steam since it was still beta sometime in January and everything I had tried in it for flash before did not work.  But I don't remember those mentioning creating a plugins directory.

---

### Post by myromance123 on 2013-03-19
> Now I have almost everything working. Steam is installed and updated. However it cant show the flash-content. I have successfully started a violent Half-Life modification and could play the game. The textures seemed more crisp than I remember them on Windows. 

I'm glad you got it working :)
I don't know how to get Flash working in Steam Linux. I tried your method A.I. However, both my 32Bit Ubuntu 12.10 and 64Bit installs do not have Flash working in Steam. Youtube Flash and everything else works, just Steam Flash doesn't.
EDIT: I'm probably putting it in the wrong folder, I'll just keep trying.
EDIT2: Thanks A.I and efflandt. It was my mistake, just needed to restart Steam. Simple solution, but my mind skipped it.

---

### Post by Perfect Storm on 2013-03-20
Strange... It's working on mine. 
The libflashplayer.so I copied is in .local/share/Steam/ubuntu12_32/plugins

---

### Post by efflandt on 2013-03-20
Steam itself is 32-bit. Have you downloaded **install_flash_player_11_linux.i386.tar.gz** from adobe.com (even for 64-bit Linux)?

Once I did: **mkdir -p ~/.local/share/Steam/ubuntu12_32/plugins**

and extracted **libflashplayer.so** from the above tar.gz file into that **plugins** directory, and started Steam, flash worked in Steam (64-bit 12.04). Although, not sure if or why that would be necessary in 32-bit Ubuntu.

---

### Post by sshaddoww on 2013-04-01
Today I decided to use an old Ati graphics card that has 30 watts in idle (2D) consumption instead of over one hundred watts (the Nvidia I have been using). The graphics card is is working and I started my Ubuntu 12.10. But after login I did not see my Startmenu anymore. The same problem as before. I am currently in my old Ubuntu 11.10 installation that I have on a separate harddrive. So what should I do to fix my Startmenu back and get Ati drivers instead of Nvidia?

---

