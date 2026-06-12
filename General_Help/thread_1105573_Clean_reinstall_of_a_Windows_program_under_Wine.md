---
title: "Clean reinstall of a Windows program under Wine?"
date: 2009-03-24
forum: General Help
---

### Post by L a r r y on 2009-03-24
[COLOR="DarkRed"]**Solved!**[/COLOR]

I am trying to get back to a clean install of a Windows program under Wine on Ubuntu.  EchoLink, an amateur radio software, has started exhibiting some odd behavior, and when I go into Wine, I run the Uninstall Wine Software (a Windows Add/Remove Software function)and run the uninstaller for EchoLink.  It does nothing substantial, just running through the motions on the screen.  After the software is removed it is still there.

I went to C:\Program Files in Wine and put the EchoLink folder in the trash. The program still ran.  I put it in the trash again and emptied the trash.

The program no longer runs, but the installer, even a fresh copy off the Web, still wants to modify or repair or remove.  I want** a new**  install.

So obviously there is something somewhere in the Registry or its equivalent.  What do I need to look at or edit?

Please help me understand this.

Thanks

---

### Post by 3Miro on 2009-03-24
The wine uninstall supposedly purges the wine registry, but the concept of registry in itself is corrupt, hence it doesn't work well in general.

You can remove the folder with your program and manually edit the registry to remove all references to your program.

You can call wine and tell it to use specific directory other than .wine, that way you can have two separate registries and settings altogether. The uninstall is to simply delete the corresponding folder.

env WINEPREFIX="/home/me/.wine_myprog" wine myprog

---

### Post by Tim Sharitt on 2009-03-25
If you want to start with a clean version of wine, you can remove the .wine folder. The next time wine is run, it will generate a new ~/.wine directory without the nee to reinstall.

---

### Post by L a r r y on 2009-03-25
> **3Miro said:**
> The wine uninstall supposedly purges the wine registry, but the concept of registry in itself is corrupt, hence it doesn't work well in general.

You can remove the folder with your program and manually edit the registry to remove all references to your program.

You can call wine and tell it to use specific directory other than .wine, that way you can have two separate registries and settings altogether. The uninstall is to simply delete the corresponding folder.

env WINEPREFIX="/home/me/.wine_myprog" wine myprog

3Miro, you have an interesting idea, to assign a separate Wine folder and set of Registries to each program, then just blow away the corresponding folder.

I ran RegEdit and edited all references to "EchoLink" out of existence, and restarted the computer, and still the installer wanted to modify, repair or remove.  AGGGGHHHH!!

So I turned to a fresh copy of "Windows" with this command to run the EchoLink installer:

env WINEPREFIX="/home/myaccount/.wine_EchoLink" wine "Z:\home\myaccount\installers\EchoLink\EchoLinkSetup_2_0_908.exe"

(The installer is located in my home directory, under installers/EchoLink, and Wine assigns Drive letter Z to the root of the Linux file system.)

I could have gone with the other suggestion by Tim Sharitt to just blow .wine away and let everything re-create in the new environment, but I didn't want to blow away my Winamp setup, which works after a fashion!  But I may eventually set up another Windows environment for Winamp and then blow away the original .wine setup, and let the rest of my programs  re-create.

Thank you to both.

---

### Post by L a r r y on 2009-03-25
[COLOR=Magenta][SIZE=5]Solved[/SIZE][/COLOR]

Where are the Talk-uptation links and the Solved widget?  I want to add to both of these responders' Talk-uptation!

Edit:  This link gives the answer:
["Where Are The 'Thank-You' And 'Solved' features?"]("http://ubuntuforums.org/showthread.php?t=1044714")

---

### Post by 3Miro on 2009-03-25
Just a note:

It makes no sense to reboot to clean wine registry, restarting wine is enough, it is in fact a reboot of the wine environment equivalent to a reboot of windows.

Some programs such as Cedega would assign different root folders to different programs. If a program requires a lot of tweaking, then you might consider using separate folders so that the tweaks do not overlap with each other.

---

