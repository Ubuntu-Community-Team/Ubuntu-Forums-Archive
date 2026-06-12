---
title: "Changing from Gnome -&gt; KDE"
date: 2009-07-30
forum: Desktop Environments
---

### Post by suncoolsu on 2009-07-30
Hi All,
I have been using using ubuntu for a while now. I have only used the default Gnome Desktop Environment till now. I want to try KDE for a change.

I am aware that I can use both the environments together but I dont want to have the "cluttered" menus (containing both Gnome and Kde applications.) Is there a way that I can use KDE without being bothered about the applications in my gnome environment. 

I am OK if my thunderbird and other miscellaneous application settings are not "imported" in KDE.

Is there a way to do this? or if I dont want the Gnome applications - then I have to completely uninstall Gnome & its applications?


Thanks for any help
B.

---

### Post by howefield on 2009-07-30
Install Kubuntu side by side with Ubuntu and dual boot, or virtualise with Virtualbox or similar.

---

### Post by Zorael on 2009-07-30
I think you could just edit your menu and delete the GNOME apps' entries, that'd be the easiest way.

The more troublesome way would be to *[edit]* scroll down and read my next post!

And Thunderbird will keep its settings in ~/.mozilla/thunderbird/ (or something along those lines), so regardless of what environment you're running, it'll retain its settings. The same goes for every other app, I believe. KDE apps will keep their settings in ~/.kde/share/config/ even if you're running GNOME.

---

### Post by m4tic on 2009-07-30
Cant the gnome menus be hidden instead?

---

### Post by suncoolsu on 2009-07-30
If i can hide the Gnome Menu Items - that wud be perfect :D

Thanks for the help!

---

### Post by Dullstar on 2009-07-30
How do you hide then though?  I need to remove the clutter added by my desktop environment experimentation from the GNOME menus.

---

### Post by Zorael on 2009-07-30
Mmkay.

Applications, when installed via proper packages (and such applications that comply with freedesktop.org/XDG standards) install a *.desktop file into **/usr/share/applications/** (and possibly **/usr/share/applnk/**).

Whenever your menu gets *enumerated*, it goes through the *.desktop files in there, parses them, and compiles its own internal list which it saves in a cache someplace. It enumerates like that every now and then, for instance at every time you install a new application, as the install scripts triggers a signal saying "hey, new app here, plx invite" after it has copied its own .desktop file to said directory(-ies). Perhaps at each login, too? Regardless.

If you go into the menu editor (right-click the kickoff icon) and make changes to an entry there - say, Firefox - a copy of the "original" .desktop file found in **/usr/share/applications/** will be saved, with your modifications, in **~/.local/share/applications/**. These user-specific .desktop files override the systemwide ones. By extension, if you remove all those .desktop files found in your home directory, it will only read the systemwide ones, so that's a neat trick if you want to revert to defaults.

This is the reason why, after removing an application, its menu entry will sometimes stick around. That happens if you've edited that menu entry (moved it around, changed the text/icon, etc), causing it to *create* a user-specific .desktop file. The script that's run when removing an application will never (as far as I'm aware) remove files from your user directory, so these get left behind; modified copies of no-longer-existing .desktop files pointing to uninstalled apps. So the place might use a bit of cleaning every now and then.

These .desktop files will also contain file association settings, so some files won't deal with menu entries at all, whereas local copies also be made if you change association settings (*"What to open .mpg files with"*, etc).

Now, these .desktop files are standard text files, so you can open them up in Kate, or kwrite, or gedit, or whatever. This is an example of my **jockey-kde.desktop** file; Jockey being the "restricted drivers manager", and jockey-kde in particular being very KDE specific.
```
[Desktop Entry]
Categories=Qt;KDE;System;
Comment=Configure third-party and proprietary drivers
Encoding=UTF-8
Exec=jockey-kde
GenericName=Jockey
Icon=jockey-kde
Name=Hardware Drivers
NoDisplay=false
**OnlyShowIn=[COLOR="DeepSkyBlue"]KDE[/COLOR];**
StartupNotify=true
Terminal=0
TerminalOptions=
TryExec=jockey-kde
Type=Application
X-KDE-SubstituteUID=false
X-KDE-Username=
X-Ubuntu-Gettext-Domain=jockey
```
As you can see, they're fairly self-explanatory. **GenericName** and **Name** defines the name and the description of the entry. **Icon** defines what icon it should have. And _**OnlyShowIn**_ decides if it should only be shown in a specific environment.

Naturally, setting it to **OnlyShowIn=[COLOR="SandyBrown"]GNOME[/COLOR]** thus hides it in KDE. (Unsure whether the trailing semicolon **;** is needed - likely not.) So if you hunt down the .desktop files of the GNOME apps you want to hide in KDE, and add that tag to it, it should hide once you force an enumeration of the menu entries. Run **kbuildsycoca4** in a terminal or in a run box (alt+f2) to do this. Or just **kbuildsycoca** if you're running KDE. If you're in GNOME, I don't know the command. Perhaps just login and logout, or install a small app?

If you change the systemwide **/usr/share/applications/** files, you'll first need superuser permissions, *and* you have to make sure you don't have user-specific **~/.local/share/applications** .desktop files overriding your new changes. Furthermore, if there are updates to an application, its **/usr/share/applications/** .desktop file *will* be overwritten, so if you take the systemwide route, you have to go back and readd the **OnlyShowIn=[COLOR="SandyBrown"]GNOME[/COLOR]** line after updating.

Editing such files and removing file associations you don't want is an easy way to avoid having to manually (via GUI) change associations for common filetypes (like .mpg, .mpeg, .mp3, .mp4, etc ad nauseam). For instance; I detest the "Enqueue in SMPlayer" file action that, due to starting with an **E**, is placed higher in alphabetic priority than the **S** in "SMPlayer" itself. So by default, when opening a multimedia file in Dolphin, it will *default* to opening it with "**E**nqueue in SMPlayer" instead of just opening it with **S**MPlayer. Your preferences may differ, obviously, but I like it to start when I doubleclick it, and not put the new file at the end of a playlist. So then I could simply delete **/usr/share/applications/smplayer_enqueue.desktop**, and it won't be parsed and added as a file action. Alternatively I could retain it as an action, but stop it from being automatically added to filetypes by removing or commenting the **MimeType** definitions in it;
```
MimeType=audio/ac3;audio/mp4;audio/mpeg;audio/vnd.rn-realaudio;audio/vorbis;audio/x-adpcm;audio/x-matroska;audio/x-mp2;audio/x-mp3;audio/x-ms-wma;audio/x-vorbis;audio/x-wav;audio/mpegurl;audio/x-mpegurl;audio/x-pn-realaudio;audio/x-scpls;video/avi;video/mp4;video/flv;video/mpeg;video/quicktime;video/vnd.rn-realvideo;video/x-matroska;video/x-ms-asf;video/x-msvideo;video/x-ms-wmv;video/x-ogm;video/x-theora;
```
Noteworthy is that nowhere in your menus should you have an "Enqueue in SMPlayer" entry, even though it has a .desktop file right next to **smplayer.desktop**, which *does* have its own "SMPlayer", *"A great MPlayer front-end"* entry. Looking at the contents of enqueue's file, you'll see that it has **NoDisplay=true** set, which is a neat way of doing the opposite; hiding something from the menus while retaining file association actions.

So, pick your approach and toy around. Either set your user up the way you want it and be happy that way, or set the system defaults up and have every user be affected (once their user-specific files are removed). But then you'd have to deal with redoing your changes after updates.

Make backups of the .desktop files if you want to change the systemwide ones and you fear you might bork them. Maybe make backups of your "fixed" files for easy overwriting when updates undid them. And be generally careful when wielding superuser privileges, obviously.

---

