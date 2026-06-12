---
title: "K-Menu doesn't show menu entries?!"
date: 2006-07-20
forum: Desktop Environments
---

### Post by Eagle3386 on 2006-07-20
Hi,

I recently installed some apps, like KDE TV for example.
This application is shown under "Multimedia", but other applications like "Kmahjongg" (shipped with KDE by default, AFAIK) are not shown?!

Doing a locate-search gives me a kmahjongg.desktop-file, but the path is different to the one of KDE TV:


/usr/share/app-install/desktop/kmahjongg.desktop (only this result)

/usr/share/app-install/desktop/kdetv.desktop
/usr/share/applnk/Multimedia/kdetv.desktop
/usr/share/applications/kde/kdetv.desktop (three results?! :confused:)


Any help would be greatly appreciated! ;)

---

### Post by asimon on 2006-07-20
> **Eagle3386 said:**
> Hi,

I recently installed some apps, like KDE TV for example.
This application is shown under "Multimedia", but other applications like "Kmahjongg" (shipped with KDE by default, AFAIK) are not shown?!
Kmahjong is not installed by default. It's part of the kdegames package, but can also installed by it's own, the package is called 'kmahjongg'.

The[url=http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=kmahjongg&version=dapper&arch=i386]
kmajongg[/url] package contains a .desktop file under /usr/share/applications/kde/ so that it appears in the games submenu.

> **Eagle3386 said:**
> 
Doing a locate-search gives me a kmahjongg.desktop-file, but the path is different to the one of KDE TV:


/usr/share/app-install/desktop/kmahjongg.desktop (only this result)

If you look you'll see that this file is owned by app-install-data, which is part of the simplified application installer.

```

# dpkg -S /usr/share/app-install/desktop/kmahjongg.desktop
app-install-data: /usr/share/app-install/desktop/kmahjongg.desktop

```
The files under /usr/share/app-install/ are just for the application installer, these files will not appear in your KDE or Gnome menu.

> **Eagle3386 said:**
> 
/usr/share/app-install/desktop/kdetv.desktop
/usr/share/applnk/Multimedia/kdetv.desktop
/usr/share/applications/kde/kdetv.desktop (three results?! :confused:)

Here again the first entry is for the adept-installer or under Gnome the gnome-app-install, which both provide an easy interface for users to install software.

The other two entries are indeed from kdetv.
The Freedesktop.org desktop menu standard which both KDE and Gnome use specifies /usr/share/applications as the directory which should contain the desktop files. The old /usr/share/applnk is probably still there because of legacy or compatibility reasons.

---

### Post by Mickeysofine1972 on 2006-07-20
So what the hell does that mean then ?

does the guy copy the .desktop files to the application folder ?

Mike

---

### Post by Eagle3386 on 2006-07-20
> **asimon said:**
> Kmahjong is not installed by default. It's part of the kdegames package, but can also installed by it's own, the package is called 'kmahjongg'.
Sorry, my mistake.. I apologize myself.

> **asimon said:**
> The[url=http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=kmahjongg&version=dapper&arch=i386]
kmajongg[/url] package contains a .desktop file under /usr/share/applications/kde/ so that it appears in the games submenu.
That might be true, but nevertheless, there are still some applications which I've installed and they don't appear in the K-Menu, although there's a .desktop-file on my hard drive..


> **asimon said:**
> If you look you'll see that this file is owned by app-install-data, which is part of the simplified application installer.

```

# dpkg -S /usr/share/app-install/desktop/kmahjongg.desktop
app-install-data: /usr/share/app-install/desktop/kmahjongg.desktop

```
The files under /usr/share/app-install/ are just for the application installer, these files will not appear in your KDE or Gnome menu.
Thanks for this useful information. :)


> **asimon said:**
> Here again the first entry is for the adept-installer or under Gnome the gnome-app-install, which both provide an easy interface for users to install software.

The other two entries are indeed from kdetv.
The Freedesktop.org desktop menu standard which both KDE and Gnome use specifies /usr/share/applications as the directory which should contain the desktop files. The old /usr/share/applnk is probably still there because of legacy or compatibility reasons.
Should I move all files from /usr/share/applnk to /usr/share/applications ? Because IMHO, that would fix the problem, doesn't it? :)

---

### Post by Mickeysofine1972 on 2006-07-20
I agree!

please post what happen though so others will know ;-)

Mike

---

### Post by asimon on 2006-07-21
> **Eagle3386 said:**
> Sorry, my mistake.. I apologize myself.

There is aboslutely no reason to apologize. :-)

> **Eagle3386 said:**
> 
That might be true, but nevertheless, there are still some applications which I've installed and they don't appear in the K-Menu, although there's a .desktop-file on my hard drive..

If this desktop file is under the /usr/share/app-install/ path, then just ignore them. The files there have nothing to do with menues.

Some packages - especially some in universe and multiverse - are missing a right .desktop file and don't appear in the menues. See [NoDesktopFile](https://wiki.ubuntu.com/MOTU/Packages/NoDesktopFile) for a list of such packages. These packages are just waiting for someone making a right .desktop file...

But Some packages do intentionelly not appear in the menues, their desktop files often contain somthing like 'NoDisplay=true'. There are usual programs which start automatically in certain cases (like the bug reporting tool when a application crashes) or do start if one clicks the associated file-type in a file browser. An example is gdebi, an easy frontend to install deb packages. This app is automatically started if you douple-click on a .deb-file in the file manager or download a .deb-file with a browser and the developers think that there is no reason to start the application via menu (i.e. without any .deb-file), thus gdebi doesn't appear in the menu at all, which makes the menu more simple. An other example is kmail. There is no way to start it via menue, the developers think that it's enough to be able to start it via kontact (which is a frontend for different pim-related components including kmail).

If you hit such a package and you really think that this is plain wrong and the application should appear in the menue, then you could try to report that as bug in [Malone](https://launchpad.net/distros/ubuntu/+bugs). But you should have some convincing use cases and reasons which make it clear that many users will want or need to start this app via the menue, otherwise the chance that the developers will change this is nil.

An example of such a case is the print job viewer in KDE. Somewhen when Dapper was still in development it didn't appear in the menu because it's started automatically if you print something with a KDE app. So it looked there was a good reason to not clutter the menu with this. But it's not automatically started if you print something from a non-KDE app. And sometimes you want to view the printing queues of printers in a network to decide with what printer to print before actually press the 'print' button or you just want to look when you print job is finished. Thus there are good use cases when you want to start this print job viewer from the menu. After a respective bug report this was changed by the developers and dapper now has KjobViewer appear in the Utilities menu under KDE (it's not shown under Gnome because Gnome has it's own print job viewer).

So if an app is missing a menu entry it's either because it's missing a desktop file -- in this case it should be already in the list above and waiting for someone to make a .desktop file -- or it's because the developer think there is good reason to not show it in the menu. If you disagree and have good reasons you can try to change this via a bug report in Malone.

> **Eagle3386 said:**
> 
Thanks for this useful information. :)

You're welcome.

> **Eagle3386 said:**
> 
Should I move all files from /usr/share/applnk to /usr/share/applications ? Because IMHO, that would fix the problem, doesn't it? :)
Don't do it. You'll end up with a lot of .desktop-files in /usr/share/applications for software which you don't have installed. Well, that wouldn't do any real harm, but it's dirty. ;-)

Another easy way would be to use a menu editor and just make the entry which you're missing. Under KDE right-click at the K-Button in the panel and choose Menu Editor. Under Gnome the menu editor is called Alacarte or something like that and should appear somewhere in Gnome's menu.

---

### Post by Eagle3386 on 2006-07-25
> **asimon said:**
> There is aboslutely no reason to apologize. :-)
OK, thanks anyway! :)

> **asimon said:**
> If this desktop file is under the /usr/share/app-install/ path, then just ignore them. The files there have nothing to do with menues.
Just once more: thank you, this information is very useful for me!

> **asimon said:**
> Some packages - especially some in universe and multiverse - are missing a right .desktop file and don't appear in the menues. See [NoDesktopFile](https://wiki.ubuntu.com/MOTU/Packages/NoDesktopFile) for a list of such packages. These packages are just waiting for someone making a right .desktop file...

But Some packages do intentionelly not appear in the menues, their desktop files often contain somthing like 'NoDisplay=true'. There are usual programs which start automatically in certain cases (like the bug reporting tool when a application crashes) or do start if one clicks the associated file-type in a file browser. An example is gdebi, an easy frontend to install deb packages. This app is automatically started if you douple-click on a .deb-file in the file manager or download a .deb-file with a browser and the developers think that there is no reason to start the application via menu (i.e. without any .deb-file), thus gdebi doesn't appear in the menu at all, which makes the menu more simple. An other example is kmail. There is no way to start it via menue, the developers think that it's enough to be able to start it via kontact (which is a frontend for different pim-related components including kmail).

If you hit such a package and you really think that this is plain wrong and the application should appear in the menue, then you could try to report that as bug in [Malone](https://launchpad.net/distros/ubuntu/+bugs). But you should have some convincing use cases and reasons which make it clear that many users will want or need to start this app via the menue, otherwise the chance that the developers will change this is nil.

An example of such a case is the print job viewer in KDE. Somewhen when Dapper was still in development it didn't appear in the menu because it's started automatically if you print something with a KDE app. So it looked there was a good reason to not clutter the menu with this. But it's not automatically started if you print something from a non-KDE app. And sometimes you want to view the printing queues of printers in a network to decide with what printer to print before actually press the 'print' button or you just want to look when you print job is finished. Thus there are good use cases when you want to start this print job viewer from the menu. After a respective bug report this was changed by the developers and dapper now has KjobViewer appear in the Utilities menu under KDE (it's not shown under Gnome because Gnome has it's own print job viewer).

So if an app is missing a menu entry it's either because it's missing a desktop file -- in this case it should be already in the list above and waiting for someone to make a .desktop file -- or it's because the developer think there is good reason to not show it in the menu. If you disagree and have good reasons you can try to change this via a bug report in Malone.
AFAICS, "KDETV" isn't in the list.. Maybe the installation went wrong.. - The tip regarding the menu editor is great, I'm going to give it a try! :D

> **asimon said:**
> Don't do it. You'll end up with a lot of .desktop-files in /usr/share/applications for software which you don't have installed. Well, that wouldn't do any real harm, but it's dirty. ;-)
Good advice - especially, because of that I was just about doing it.. ;)

> **asimon said:**
> Another easy way would be to use a menu editor and just make the entry which you're missing. Under KDE right-click at the K-Button in the panel and choose Menu Editor. Under Gnome the menu editor is called Alacarte or something like that and should appear somewhere in Gnome's menu.
As already stated above, I'm going to try it out ASAP.. :)


I'm writing "ASAP", because my internet connection was broken some days ago (That's the cause for the late reply, too.) - so give me some time, because some exams are in the queue for the next days.. ;)

---

