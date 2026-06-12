---
title: "Quicklists don't work in Oneiric"
date: 2011-10-16
forum: Desktop Environments
---

### Post by Pirate Zoro on 2011-10-16
In my install of Oneiric, it seems that a few quicklists that I use often, most notably the home folder quicklist to access my bookmarks, which I used quite often in Natty (and various re-spins). When I activated it, the launcher opened nautilus in a separate home folder icon. I double checked the .desktop file, and everything was right, but it wouldn't work. I ended up just deleting the file from ~/.local/share/applications and instead installed the places indicator, and that works fine for now, but I would like to know, is anyone else having this problem? Does that quicklist just not work in Oneiric? I miss being able to open different folders right from the launcher.

---

### Post by mc4man on 2011-10-16
all my quicklists are orig. created on natty & work fine, inc a nautilus one.

When I 1st. did this install I did see nautilus open in "File" icon when using the Home Folder default icon. That disappeared upon log out/in
For the nautilus modded .desktop I never add it to the launcher - I just place in ~/.local/share/applications & do a log out/in. It's automatically used over the one in /usr/share/appkications

If you want post your .desktop, I'll give it a try here..

Edit: what is the 'actual' name of your .desktop - here I use nautilus-home.desktop

---

### Post by Pirate Zoro on 2011-10-16
the file is indeed nautilus-home.desktop, with the quicklist copied from the Natty launcher and put into the Oneiric file. 

```
[Desktop Entry]
Name=Home Folder
Comment=Open your personal folder
Exec=nautilus
Icon=user-home
Terminal=false
StartupNotify=true
Type=Application
OnlyShowIn=GNOME;Unity;
Categories=GNOME;GTK;Core;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=3.0.0
X-Ubuntu-Gettext-Domain=nautilus
X-Ayatana-Desktop-Shortcuts=Scg1;Scg2;Scg3;Scg4;Scg5;Scg6;Scg7;Scg8;Scg9;RootFM;

[Scg1 Shortcut Group]
Name=Documents
Exec=nautilus "file:///home/zoro/Documents"
OnlyShowIn=Unity

[Scg2 Shortcut Group]
Name=Music
Exec=nautilus "file:///home/zoro/Music"
OnlyShowIn=Unity

[Scg3 Shortcut Group]
Name=Pictures
Exec=nautilus "file:///home/zoro/Pictures"
OnlyShowIn=Unity

[Scg4 Shortcut Group]
Name=Videos
Exec=nautilus "file:///home/zoro/Videos"
OnlyShowIn=Unity

[Scg5 Shortcut Group]
Name=Downloads
Exec=nautilus "file:///home/zoro/Downloads"
OnlyShowIn=Unity

[Scg6 Shortcut Group]
Name=Comics
Exec=nautilus "file:///home/zoro/Comics"
OnlyShowIn=Unity

[Scg7 Shortcut Group]
Name=Ebooks
Exec=nautilus "file:///home/zoro/Ebooks"
OnlyShowIn=Unity

[Scg8 Shortcut Group]
Name=Memes
Exec=nautilus "file:///home/zoro/Memes"
OnlyShowIn=Unity

[Scg9 Shortcut Group]
Name=Torrents
Exec=nautilus "file:///home/zoro/Torrents"
OnlyShowIn=Unity

[RootFM Shortcut Group]
Name=Root
Exec=gksudo nautilus
OnlyShowIn=Unity
```

I tried logging out and back in, and it still brings it up in a separate launcher

---

### Post by mc4man on 2011-10-16
Let me try something here, I don't use the 'bookmark' type paths, use the actual here, -  base of my home dir
Ex.'s 
Exec=nautilus --no-desktop .local/share/applications
Exec=nautilus --no-desktop /usr/share/applications

What happens when you left click on your icon - does it open in that icon (Home Folder

Edit: - the bookmark paths work the same here, still open in the Home Folder icon

---

### Post by Pirate Zoro on 2011-10-16
left clicking the home folder opens nautilus in the "files" launcher, as does opening a folder from the quicklist. I also tried changing from the bookmark paths to the direct paths, and it did not help.

---

### Post by mc4man on 2011-10-16
It's probably not your .desktop, I've had this happen a few times in the past, trying to recollect how I fixed -it was hard at times

I guess i'd start by removing the icon & logging out/in
Then try opening nautilus & see if you get the Home or File icon showing up & if Home does it have your lists

If it's the File icon, (likely) then browse to ~/.local... and drag your .desktop onto the launcher, close out nautilus & log out/in.
May work may not.

---

### Post by Pirate Zoro on 2011-10-16
I tried as you suggested, removing it, logging out and in and putting it back, sadly it still did not work.

---

### Post by mc4man on 2011-10-16
So - i took your .desktop, edited the username to mine & just enabled thru Scg5 in the X-Ayatana-Desktop-Shortcuts= line

Am using on a new user I set up & same thing - open the folders correctly but in a 2nd Files icon
So there is something about about the .desktop
Let me see if I can fix. or I can attach the one I use which is similar to a point - you can try it & edit as needed

---

### Post by Pirate Zoro on 2011-10-16
If you can attach yours, I would like to try it, with my user name of course, and see if it will work.

---

### Post by mc4man on 2011-10-16
Not sure exactly, running out of time tonight - but got yours to work by replacing the complete top section (blue)- it may be the Exec= line
Plus I use a different bottom line in each sc group but that wasn't the issue or only issue

So this mod of yours worked - changed username in 1-5
```
[COLOR="Blue"][Desktop Entry]
Name=Home Folder
Comment=Open your personal folder
Exec=nautilus --no-desktop %U
Icon=user-home
Terminal=false
StartupNotify=true
Type=Application
Categories=GNOME;GTK;Core;
MimeType=x-directory/gnome-default-handler;x-directory/normal;inode/directory;application/x-gnome-saved-search;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-Ubuntu-Gettext-Domain=nautilus[/COLOR]
X-Ayatana-Desktop-Shortcuts=Scg1;Scg2;Scg3;Scg4;Scg5;

[Scg1 Shortcut Group]
Name=Documents
Exec=nautilus "file:///home/doug1/Documents"
[COLOR="Red"]TargetEnvironment=Unity[/COLOR]

[Scg2 Shortcut Group]
Name=Music
Exec=nautilus "file:///home/doug1/Music"
TargetEnvironment=Unity

[Scg3 Shortcut Group]
Name=Pictures
Exec=nautilus "file:///home/doug1/Pictures"
TargetEnvironment=Unity

[Scg4 Shortcut Group]
Name=Videos
Exec=nautilus "file:///home/doug1/Videos"
TargetEnvironment=Unity

[Scg5 Shortcut Group]
Name=Downloads
Exec=nautilus "file:///home/doug1/Downloads"
TargetEnvironment=Unity

[Scg6 Shortcut Group]
Name=Comics
Exec=nautilus "file:///home/zoro/Comics"
TargetEnvironment=Unity

[Scg7 Shortcut Group]
Name=Ebooks
Exec=nautilus "file:///home/zoro/Ebooks"
TargetEnvironment=Unity

[Scg8 Shortcut Group]
Name=Memes
Exec=nautilus "file:///home/zoro/Memes"
TargetEnvironment=Unity

[Scg9 Shortcut Group]
Name=Torrents
Exec=nautilus "file:///home/zoro/Torrents"
TargetEnvironment=Unity

[RootFM Shortcut Group]
Name=Root
Exec=gksudo nautilus
TargetEnvironment=Unity

```
If still no go I'll attach mine - need to log in to my real user

edit: after editing your's to match, do a log out, ect.

---

### Post by Pirate Zoro on 2011-10-16
That worked :D thank you so much for the help, marking thread as solved

---

### Post by mc4man on 2011-10-16
Great - maybe tomorrow i'll go line by line in that temp user & see what it was, would be good to know
(good to see people using the quicklists - excellent feature

---

### Post by Ray-Ven on 2011-10-16
It's OnlyShowIn=

---

### Post by Ray-Ven on 2011-10-16
It's the OnlyShowIn= section.
Delete it and it works.
Please post a Bugreport at launchpad!

Thanks,

Ray

---

### Post by yesornot on 2011-12-04
Hi there  :) it's my first post in this forum.
As my issue is correlated, I wont open a new thread if not otherwise suggested.
In my quicklist I replaced the [Desktop Entry] section with the one posted by mc4man but it's still not working for me: when I first open any Nautilus window it became impossible to open the home with the left click on the icon. Even closing the window doesn't help: the quicklist keeps a straight face to my left clicks :(
```
[Desktop Entry]
Name=Home Folder
Comment=Open your personal folder
Exec=nautilus --no-desktop %U
Icon=user-home
Terminal=false
StartupNotify=true
Type=Application
Categories=GNOME;GTK;Core;
MimeType=x-directory/gnome-default-handler;x-directory/normal;inode/directory;application/x-gnome-saved-search;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-Ubuntu-Gettext-Domain=nautilus
X-Ayatana-Desktop-Shortcuts=Documents;Pictures;Music;Downloads;Videos;

[Documents Shortcut Group]
Name=Documenti
Exec=nautilus Documenti/
TargetEnvironment=Unity

[Pictures Shortcut Group]
Name=Immagini
Exec=nautilus Immagini/
TargetEnvironment=Unity

[Music Shortcut Group]
Name=Musica
Exec=nautilus Musica/
TargetEnvironment=Unity

[Downloads Shortcut Group]
Name=Scaricati
Exec=nautilus Scaricati/
TargetEnvironment=Unity

[Videos Shortcut Group]
Name=Video
Exec=gksudo nautilus Video/
TargetEnvironment=Unity
```

---

