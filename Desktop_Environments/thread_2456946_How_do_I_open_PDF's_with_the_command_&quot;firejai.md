---
title: "How do I open PDF's with the command &quot;firejail okular&quot; rather than just &quot;okular&quot;?"
date: 2021-01-22
forum: Desktop Environments
---

### Post by routebee on 2021-01-22
I know that in Gnome you can associate PDF files to be opened with Okular by right clicking one and choosing: "properties > open with > Okular". Unfortunately this particular PDF is called "Linux Basics For Hackers" and it was given to me by a character called "Malware Guy". How do I...

1. Specify that upon double clicking all PDF files be opened with the command "firejail okular"?

And

2. How do I create a desktop icon that launches "firejail okular"?

This would be very simple in MATE but I can't work out how to do it in Gnome and I'd rather not have to launch Okular from a terminal and manually open the file every time I want to look at it.

Thanks in advance.

---

### Post by TheFu on 2021-01-22
Modify the .desktop file to have the command you want. .desktop files are just text - like the old Win3.0 PIF files.

Gnome3 doesn't support desktop icons.  For that you'll need some 3rd party gnome3 addon.  I don't use Gnome, so cannot recommend. Sorry.

If you need a Linux reference, [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is very useful and covers topics in the correct order for better understanding.  When you are new, jumping into the middle of a topic without sufficient background is very dangerous. Often, this will lead to data loss when (not if) you do something foolish.  I'm down to doing something foolish only a few times a week after 25+ yrs as an admin. TGFB!!!

---

### Post by routebee on 2021-01-23
That is not as simple as you make it out to be, I'll figure it out eventually but if you make a mistake when editing a launcher the icon disappears from the desktop when you click it. I can still see them with "ls" and edit them with "vim" but it have to copy a new launcher across from /usr/share/applications in order to see it again. Not only that but your answer doesn't address point 1 which was... Is there any way to associate a file type with a sandboxed application? In other words I want it to execute "firejail okular file.pdf" when I double click file.pdf on the desktop or in nautilus rather than just "okular file.pdf". I suspect this will be neigh impossible.

My assessment is that Gnome has made desktop launchers overly complicated and in my opinion they are a mainstay of any desktop environment. I like to have all my apps and documents on the desktop and I may even take the time to contribute a menu item that opens a desktop launcher tool when you right click a desktop icon or the desktop itself if I decide to stick with Gnome.

Gnome--

---

### Post by TheFu on 2021-01-23
What?  You've lost me completely.  .desktop files are not specific to Gnome.
Modifying the Exec= line is trivial.  Use sudoedit on the file. Done. I didn't want to be accused of talking down to someone who knew what they were doing, so I didn't provide too many details.

For example, let's find the .desktop file for the chromium browser:
```
$ locate .desktop|grep chromium
/snap/chromium/1461/bin/chromium.desktop
/snap/chromium/1461/meta/gui/chromium.desktop
/usr/share/applications/chromium-browser.desktop
/var/lib/snapd/desktop/applications/chromium_chromium.desktop
```
I don't use any DE or menus, so I can't easily figure out which is being used by any DE, but that's the list on a 20.04 desktop system of some sort.  The 'snap' parts cannot be modified - snap packages suck - but .... 
```
$ ll /usr/share/applications/chromium-browser.desktop
-rw-r--r-- 1 root root 12478 Sep 18 10:14 /usr/share/applications/chromium-browser.desktop

```
looks promising.
```
$ sudoedit /usr/share/applications/chromium-browser.desktop
```
Ok, there are multiple Exec= lines in that file for different menu entries and languages.
Let's see if we can't narrow that down a little.
```
$ egrep Exec=  /usr/share/applications/chromium-browser.desktop
Exec=chromium-browser %U
Exec=chromium-browser
Exec=chromium-browser --incognito
Exec=chromium-browser --temp-profile
```
If I were guessing, I'd guess that the first one above is used with any right-click. Can we get more data?
```
$ egrep 'Name=|Exec='  /usr/share/applications/chromium-browser.desktop
Name=Chromium Web Browser
GenericName=Web Browser
Exec=chromium-browser %U
Name=Open a New Window
Exec=chromium-browser
Name=Open a New Window in incognito mode
Exec=chromium-browser --incognito
Name=Open a New Window with a temporary profile
Exec=chromium-browser --temp-profile
```

Ok, now we have the "name/generic name" and the Exec= line that goes with it.
So ... let's change the "Open a New Window" version to call firejail ... make these changes using sudedit:
```
Name=Open a New Window in Firejail
Exec=/usr/bin/firejail /usr/bin/chromium-browser 

```
I use the full path to ensure the exact program I want gets used, not something else in my PATH environment variable that happens to be first.

Give that a try. See if it works.  

All the "snap" version get replaced whenever the snap package is updated, I think. Also, those located under /snap/chromium/ are created using loop mounts by the snap initialization crapola during boot. I don't really know all the details about snaps and when things happen.  Much easier to avoid them whenever possible. Plus, firejail and snaps create conflicts so it won't work on most systems.  I tweaked my system to run Chromium browser outside a snap.  

Firefox runs fine inside a firejail, however. Just tested it. /usr/share/applications/firefox.desktop is the only location with a firefox.desktop file on my system. It also has multiple Exec= lines for similar startup options.  Just put firejail in front of each.  If you don't want anything written to the disk, use **firejail --private** and an overlay file system will be used. That's great until you want to save a file or print.

---

### Post by routebee on 2021-01-23
There is a bug in Gnome where when you copy a .desktop file to your desktop and edit it it sometimes disappears when you do a variety of things such as save the changes or click the icon but if you do a "killall -s QUIT gnome-shell" all the hidden desktop launchers come back again. The uncertainty I was experiencing was due to this bug but as I said restarting gnome-shell fixes it and I have come up with a semi acceptable work around for the question I asked about file associations too. I edited the contents of my launcher to exactly the following:

```
[Desktop Entry]
MimeType=application/pdf;application/x-gzpdf;application/x-bzpdf;application/x-wwf;
Terminal=false
Name=Linux Basics For Hackers
GenericName=PDF Document
Comment=A gift from Malware Guy from the K3rnel Panic Discord Server
Exec=firejail okular /home/norman/Documents/WARNING\!\ ONLY\ OPEN\ THIS\ BOOK\ IN\ FIREJAIL.pdf
Icon=okular
Type=Application
InitialPreference=8
Categories=Qt;KDE;Graphics;Viewer;
X-KDE-Keywords=PDF, Portable Document Format
NoDisplay=true
```

Then I restarted gnome-shell and found that it was working (it opens the book in a sandboxed instance of okular). I'd still like to know if there is any (relatively) simple way to associate the entire PDF file type with a sandboxed PDF reader rather than having to set up a separate launcher for every suspicious file but if that is not easy the only questions that remain relate to specifying custom icons... Where does Gnome look for the image specified by the line "Icon=okular" and do I have to do anything tricky to update the system after I copy a new icon file to that location?

---

