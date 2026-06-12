---
title: "Never-ending &quot;Software updates installed&quot; notification. How can I remove it?"
date: 2024-05-09
forum: Desktop Environments
---

### Post by Paddy Landau on 2024-05-09
For a while now (probably a few weeks, though I'm unsure of that), **every time** I boot my computer, Gnome Software Store gives me the notification, "Software Updates installed. Important OS updates have been installed."


[CENTER][IMG]https://ubuntuforums.org/attachment.php?attachmentid=293743&stc=1[/IMG][/CENTER]


When I click on the notification, I get the following list. It's always the same list, even though there have been many updates since this notification started happening.


[CENTER][IMG]https://ubuntuforums.org/attachment.php?attachmentid=293742&stc=1[/IMG][/CENTER]


Automatic Updates and Automatic Update Notifications are turned off.


[CENTER][IMG]https://ubuntuforums.org/attachment.php?attachmentid=293741&stc=1[/IMG][/CENTER]


What's curious is that the current installation of Grub is version 2.06-2ubuntu7.2.

```
**$ apt list --installed 'grub*'**
Listing... Done
[COLOR=#008000]grub-common[/COLOR]/jammy-updates,now 2.06-2ubuntu7.2 amd64 [installed]
[COLOR=#008000]grub-efi-amd64-bin[/COLOR]/jammy-updates,jammy-security,now 2.06-2ubuntu14.4 amd64 [installed]
[COLOR=#008000]grub-efi-amd64-signed[/COLOR]/jammy-updates,jammy-security,now 1.187.6+2.06-2ubuntu14.4 amd64 [installed]
[COLOR=#008000]grub-gfxpayload-lists[/COLOR]/jammy,now 0.7 amd64 [installed]
[COLOR=#008000]grub-pc-bin[/COLOR]/jammy-updates,now 2.06-2ubuntu7.2 amd64 [installed]
[COLOR=#008000]grub-pc[/COLOR]/jammy-updates,now 2.06-2ubuntu7.2 amd64 [installed]
[COLOR=#008000]grub2-common[/COLOR]/jammy-updates,now 2.06-2ubuntu7.2 amd64 [installed]
```

I've tried this:

[LIST=1]
[*]Uninstall Gnome Software with
```
sudo apt purge gnome-software
```
[*]Reinstall Gnome Software with
```
sudo apt install gnome-software
```
[/LIST]
But that didn't help.

I'm using **Ubuntu 22.04**.

Do you know how I can get rid of this notification, please?

---

### Post by #&amp;thj^% on 2024-05-09
Hi Paddy have a look here for Jammy: [https://askubuntu.com/questions/1469200/how-can-i-dismiss-software-updates-installed-notification](https://askubuntu.com/questions/1469200/how-can-i-dismiss-software-updates-installed-notification)

---

### Post by Paddy Landau on 2024-05-09
Thank you, @1fallen. I deleted the oddly-named file [FONT=courier new]/var/lib/PackageKit/offline-update-competed[/FONT], and that did the trick!

---

### Post by nicolasdentremont on 2024-05-09
> **Paddy Landau said:**
> Thank you, @1fallen. I deleted the oddly-named file [FONT=courier new]/var/lib/PackageKit/offline-update-competed[/FONT], and that did the trick!

The same thing happens to me. I have to delete that file every time I install updates through Gnome software.

---

### Post by #&amp;thj^% on 2024-05-09
You could just disable it:
```
systemctl disable packagekit.service
```

More info on that here: [https://www.freedesktop.org/software/PackageKit/pk-intro.html](https://www.freedesktop.org/software/PackageKit/pk-intro.html)

I'm glad I don't rely on GUI software anything.

---

### Post by nicolasdentremont on 2024-05-09
> **1fallen said:**
> You could just disable it:
```
systemctl disable packagekit.service
```

More info on that here: [https://www.freedesktop.org/software/PackageKit/pk-intro.html](https://www.freedesktop.org/software/PackageKit/pk-intro.html)

I'm glad I don't rely on GUI software anything.

I kinda want to remove it altogether. It came in when I installed (flatpak) lutris. I do most of my installing and updating through command line but I didn't want to mess up Lutris.

---

### Post by #&amp;thj^% on 2024-05-09
> **nicolasdentremont said:**
> Ibut I didn't want to mess up Lutris.
I'll have to study that one. :)

---

