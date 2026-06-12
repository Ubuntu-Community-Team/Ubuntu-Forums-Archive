---
title: "Auto-launch torrents from Firefox in uTorrent"
date: 2008-12-22
forum: General Help
---

### Post by chrisamiller on 2008-12-22
RSS feeds plus bittorrent makes auto-downloading video content from the web easy, and keeps our library full of shows to watch through the Xbox.  I struggled for a while to find a bittorrent client that was simple and had the features I wanted, though.

Azureus is a bloated mess, Transmission is far too simple, Deluge made feeds a pain in the *** . . . you get the idea.  Finally, I found that uTorrent had all the features I wanted in a lightweight, easy to use client.  The only problem is, it doesn't run natively on linux.  Thankfully, it runs almost perfectly through Wine, with a taskbar icon and everything.  

The only problem I had was that when I clicked on a torrent in my browser, I couldn't get it to auto-launch in uTorrent.  The extra layers added by wine complicated things.  I finally solved the problem by writing this little bash script:

```
#!/bin/bash
cd ~/.wine/drive_c/Program\ Files/uTorrent
echo ""
if [ "$1" != "" ]; then
    dt=`date +%s%N`
    cp "$1" /tmp/$dt.torrent
    var="Z:\\tmp\\"$dt".torrent"
    wine utorrent.exe "$var"
else
    wine utorrent.exe
fi
```

It takes the torrent file given as an argument, saves it to a wine-accessible location, then opens it using uTorrent.  Save the script, make it executable, and then set firefox so that it uses the script to open any torrent files.  Problem solved.

---

### Post by Bakon Jarser on 2008-12-30
Worked perfectly, thanks.

---

### Post by darkfires on 2009-02-24
Thanks for posting your script.  I revised your script to work with CrossOver (It seems to run utorrent better for me than regular wine) and also revised it for wine as well.  It's a little cleaner, and doesn't rely on running sed.

If you're running CrossOver, it uses something called bottles by default it will put utorrent in one labeled Unsupported, so if you have it installed in a different one, change the bottle variable.  You can verify its location by right clicking on the utorrent icon and checking the command box under Launcher tab.

CrossOver script:

```
#!/bin/sh
bottle="Unsupported"
runpath="$HOME/.cxoffice/${bottle}/desktopdata/cxmenu/Desktop.C^5E3A^5Fwindows^5Fprofiles^5Fcrossover^5FDesktop/^C2^B5Torrent"
args="$1"

if [ "$args" ]; then
        gpath="Z:${args//\//\\}"
fi

${runpath} "$gpath"

```


Wine script:

```

#!/bin/sh
cd ~/.wine/drive_c/Program\ Files/uTorrent
args="$1"

if [ "$args" ]; then
        gpath="Z:${args//\//\\}"
fi

wine utorrent.exe "$gpath"

```


Enjoy!

---

### Post by Bakon Jarser on 2009-03-22
Works great in jaunty too.

---

### Post by mrjerryk on 2009-09-20
> **chrisamiller said:**
> RSS feeds plus bittorrent makes auto-downloading video content from the web easy, and keeps our library full of shows to watch through the Xbox.  I struggled for a while to find a bittorrent client that was simple and had the features I wanted, though.

Azureus is a bloated mess, Transmission is far too simple, Deluge made feeds a pain in the *** . . . you get the idea.  Finally, I found that uTorrent had all the features I wanted in a lightweight, easy to use client.  The only problem is, it doesn't run natively on linux.  Thankfully, it runs almost perfectly through Wine, with a taskbar icon and everything.  

The only problem I had was that when I clicked on a torrent in my browser, I couldn't get it to auto-launch in uTorrent.  The extra layers added by wine complicated things.  I finally solved the problem by writing this little bash script:

```
#!/bin/bash
cd ~/.wine/drive_c/Program\ Files/uTorrent
echo ""
if [ "$1" != "" ]; then
    dt=`date +%s%N`
    cp "$1" /tmp/$dt.torrent
    var="Z:\\tmp\\"$dt".torrent"
    wine utorrent.exe "$var"
else
    wine utorrent.exe
fi
```

It takes the torrent file given as an argument, saves it to a wine-accessible location, then opens it using uTorrent.  Save the script, make it executable, and then set firefox so that it uses the script to open any torrent files.  Problem solved.

How do you set firefox to use this script?

---

### Post by Chronon on 2009-09-20
Make sure it's executable and point firefox to the script in the Applications tab of Preferences, I believe.

---

