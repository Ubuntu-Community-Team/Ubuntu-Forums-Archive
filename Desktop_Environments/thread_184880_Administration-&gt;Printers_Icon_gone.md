---
title: "Administration-&gt;Printers Icon gone"
date: 2006-05-30
forum: Desktop Environments
---

### Post by celem on 2006-05-30
The Icon for System->Administration->Printers has disappeared. It was present in Dapper and I used it to set up a network printer shared on my Windows XP machine. However, simultaneously with Samba problems of not being able to see shares, the Icon disappeared. The shares have magically started working again after swapping out one perfectly working pcmcia Wifi card for a second, perfectly working cardbus WiFi card.

My only printer is a Deskjet 895Cse on my Windows XP box, via Samba share. It still works but the System->Administration->Printers Icon is gone so I cannot add more printers or change the printer defaults. I suspect that the Samba share problem partially remains and since it isn’t “seeing” the share, it removed the Printer Icon. Thus, I feel that this related to the Samba share issue.

---

### Post by disturbed1 on 2006-05-30
Do you have cups installed and running? Haven't added any Samba Printers, but here's my screen shot.

[img]http://ubuntuforums.org/attachment.php?attachmentid=10282&stc=1&d=1149011801[/img]

You can run the printers program with this command
gnome-cups-manager

---

### Post by celem on 2006-05-30
Yes, the printing is via CUPS and it prints to the printer on the Windows box correctly via Samba. It is important to know that the Printer Icon disappeared when the Samba's share name problem started. I feel that since Samba doesn't "see" the printer, Dapper doesn't "see" a printer and thus removes the Icon. The printer currently works because "that" printer is set-up. However, without the Icon I cannot easily set-uup another printer or make changes to the existing one.

---

### Post by llamakc on 2006-05-30
That menu option (and icon) is available & present even if no printers are ever installed.

Does the gnome-cups-manager run from commandline?

---

### Post by celem on 2006-05-30
gnome-cups-manager did not run from commandline. I checked  Administration->Services, and cupsys is running. I checked Synaptic and gnome-cups-manager was not installed. I installed it and now gnome-cups-manager does run from commandline and the Printing icon is restored.

I appreciate your help. I remain curious as to how it disappeared since it used to be installed.

---

### Post by Scythe!? on 2006-08-06
Tried the Menu Editor? Go to Apps - Accessories - Alacarte Menu Editor

Look at shot for more info
[[IMG]http://img205.imageshack.us/img205/9629/screenshotsm5.th.png[/IMG]](http://img205.imageshack.us/my.php?image=screenshotsm5.png)

---

