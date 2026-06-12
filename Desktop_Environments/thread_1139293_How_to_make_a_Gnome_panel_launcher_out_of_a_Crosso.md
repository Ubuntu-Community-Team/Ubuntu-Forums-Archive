---
title: "How to make a Gnome panel launcher out of a Crossover command..."
date: 2009-04-26
forum: Desktop Environments
---

### Post by johnnyhostile on 2009-04-26
I am using Crossover Office professional to run utorrent.exe in Ubuntu8.04.

I have used the 'Run a Windows Command' option to create a shortcut to the .exe by making a launcher that I can run by clicking on via Nautilus..

I want to achieve two things:

1) Add utorrent to the Gnome menu.
2) Add a launcher for utorrent to my gnome panel.

I have achieved the first by placing the following in /home/larry/.local/share/applications

```
$ cat utorrent.desktop
[Desktop Entry]
Encoding=UTF-8
#Version=1.0
Name=uTorrent BitTorrent Client
Type=Application
Comment=Lightweight Windows BitTorrent client, includes encryption
Exec=/home/larry/.larry/utorrent.exe.desktop
TryExec=/home/larry/.larry/utorrent.exe.desktop
Icon=/home/larry/.larry/utorrent/utorrent.png
MimeType=application/x-bittorrent;
Categories=Internet;Network;FileTransfer;P2P;GTK;
```

Problem is, the launcher does not recognize the command '/home/larry/.larry/utorrent.exe.desktop' because that is not the command Crossover is running - here it is:

```
"/home/larry/cxoffice/bin/wine" --bottle "xp" --untrusted --workdir "/home/larry/.larry/utorrent" -- "/home/larry/.larry/utorrent/utorrent.exe"
```

So the question is, how do I make a launcher run the above command?

I tried dragging the Crossover-made launcher to the panel and it works until I reboot and then it becomes a blank launcher...

Whew :P

---

### Post by johnnyhostile on 2009-04-26
> **johnnyhostile said:**
> So the question is, how do I make a launcher run the above command?

...And I have just figured out that I can right-click on the launcher icon and past the correct command into the command field and what do ya know - it works!

PEBKAC after all :P

:guitar:

---

### Post by frereonline on 2011-03-13
After reinstalling CrossOver Linux 10.00 on Ubuntu Lucid, the default menu shortcuts were all messed up, and it took me a lot of fiddling (newbie ;o) to find the proper command and create manual shortcuts... Here it goes:

/opt/cxoffice/bin/wine --bottle "[BOTTLE NAME]" --cx-app [APPLICATION NAME]
Example:
/opt/cxoffice/bin/wine --bottle "Microsoft Office 2000" --cx-app WINWORD.EXE

The icons are normally under
~/.cxoffice/[BOTTLE NAME]/windata/Associations

To get a list of all Crossover Win applications, run this in a terminal:
find ~/.cxoffice -iname "*.exe"
___
I hope this helps...

---

