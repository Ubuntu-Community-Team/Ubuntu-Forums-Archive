---
title: "editing standard launcher for network users"
date: 2012-08-09
forum: Desktop Environments
---

### Post by kuronekokira on 2012-08-09
Hey guys,

whenever I had a problem with Ubuntu, this forum helped me out a lot, so I wondered if you could help me with this problem as well:

I'm a system admin at our company and we decided to switch from 11.04 with Ubuntu Classic to 12.04 which unfortunately doesn't have the classic interface.
Now we want to customize the launcher for our all our users so it won't show LibreOffice Impress, the Software-Center, Ubuntu One and especially the system configuration (although they won't be able to edit it either way). Instead we want them to have other programs attached to it.

The problem is that we want this customization on every computer and I have absolutely no idea where I can edit that. I know that the .desktop files are saved in /usr/share/applications and ~/.local/share/applications but being there doesn't mean they show up automatically in the launcher.

For better understanding: our users log in to our server where they have their home directory. Ubuntu and all programs are installed localy on every computer. We intend to save these launcher standard settings localy as well.

I hope you can help me.

Thanks in advance,
Kira


Edit: Here is an update: 
I just found out you can get your own settings with *gsettings get com.canonical.Unity.Launcher favorites* via the terminal.
Do you know where I can find and edit the default settings?

---

