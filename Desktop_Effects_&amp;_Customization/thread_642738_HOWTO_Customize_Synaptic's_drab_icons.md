---
title: "HOWTO: Customize Synaptic's drab icons"
date: 2007-12-17
forum: Desktop Effects &amp; Customization
---

### Post by soliac on 2007-12-17
This guide will help you improve the look of Synaptic, the default package manager of Ubuntu, when the Human icon theme is used.
The default icons in Synaptic seem a bit drab to me:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=53461&stc=1&d=1197866923[/IMG]

The attached [_synaptic-actions_]("http://ubuntuforums.org/attachment.php?attachmentid=53459&d=1197866923") icons are from [_this bug report_]("https://bugs.launchpad.net/synaptic/+bug/162043") and are the work of Hylke Bons. The "[_system-upgrade_]("http://ubuntuforums.org/attachment.php?attachmentid=53460&d=1197866923")" icon is by [_Lauri Taimila_]("http://www.taimila.com/?q=node/3").
The end result of this guide:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=53462&stc=1&d=1197866923[/IMG]

To use these icons, download the attached [_**synaptic-actions-icons.tar.gz**_]("http://ubuntuforums.org/attachment.php?attachmentid=53459&d=1197866923") and [_**synaptic-upgrade-icon.tar.gz**_]("http://ubuntuforums.org/attachment.php?attachmentid=53460&d=1197866923") files to your home directory, and then run the following commands:

```
sudo tar -zxvf ~/synaptic-actions-icons.tar.gz -C /usr/share/icons/Human/16x16/actions/
sudo tar -zxvf ~/synaptic-upgrade-icon.tar.gz -C /usr/share/icons/Human/24x24/apps/
sudo gtk-update-icon-cache -f /usr/share/icons/Human/

[I](What do these commands do?
Decompress both archives into the appropriate icon folders and then update the icon cache.)[/I]
```

Now open up Synaptic to see the new icons.
To undo the changes, you just need to delete these icons - the old icons will automatically be used again after these commands:

```
sudo rm /usr/share/icons/Human/16x16/actions/package-* -v
sudo rm /usr/share/icons/Human/24x24/apps/system-upgrade.png -v
sudo gtk-update-icon-cache -f /usr/share/icons/Human/

[I](What do these commands do?
Remove the custom icons and update the icon cache.)[/I]
```

---

### Post by FuturePilot on 2007-12-17
Wow, that looks beautiful! Thanks for sharing. :D

---

### Post by soliac on 2007-12-17
You're most welcome :)

---

### Post by Espreon on 2007-12-17
These icons should be included in 8.04.., I shall try these in a few mins

---

