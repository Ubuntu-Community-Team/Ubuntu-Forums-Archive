---
title: "FTP mount using gigolo opens in Firefox instead of thunar"
date: 2012-07-19
forum: Desktop Environments
---

### Post by kpuz on 2012-07-19
I am recently having an annoying issue with Gigolo.  When I connect to an ftp share on my local network, double clicking on the mounted folder in Gigolo opens the share in firefox.  I want to be able to use Thunar to see the share.  Does anyone know how I can fix this?

---

### Post by Toz on 2012-07-20
In gigolo, under Edit->Preferences, what do you have in the "File Manager" text-box?

EDIT: And what does the following return:
```
xdg-mime query default x-scheme-handler/ftp
```

---

### Post by Morbius1 on 2012-07-20
I don't mean to turn this into a blog entry but I tried a double click in gigolo and it too opened up Firefox.

I tried Toz's command which resulted in:
> > xdg-mime query default x-scheme-handler/ftp
> exo-web-browser.desktopThat made sense but I didn't know what to do with that information but I figured an exo-file-manager.desktop would fix it. I tried to do that in /usr/share/applications ( defaults.list & mimeinfo.cache ) but was not successful so what I did was this:
```
leafpad $HOME/.local/share/applications/mimeapps.list
```And under [Default Applications] added the following line:
```
x-scheme-handler/ftp=exo-file-manager.desktop
```Saved the file, double clicked the gigolo ftp entry and it opened Thunar.

Seems kind of silly to do this by user instead of globally and no doubt I'm supposed to run an update command or something to make the change in the global settings but I can't figure it out.

---

### Post by Toz on 2012-07-20
Hi Morbius1.
To make the change globally on Xubuntu, the file to edit is /usr/share/xubuntu/applications/defaults.list. There is an existing entry there for x-scheme-handler/ftp which points it to exo-web-browser.desktop

---

### Post by Morbius1 on 2012-07-21
> **Toz said:**
> Hi Morbius1.
To make the change globally on Xubuntu, the file to edit is /usr/share/xubuntu/applications/defaults.list. There is an existing entry there for x-scheme-handler/ftp which points it to exo-web-browser.desktop
Ah, Didn't even realize there was a /usr/share/xubuntu/applications - I'll have to give it a go. Thanks.

So is the priority order on this thing:
$HOME/.local/share/applications
/usr/share/xubuntu/application
/usr/share/application

Where the one in one's home directory takes precedence above all others and the one in /usr/share/xubuntu over the one in /usr/share/appliction?

---

### Post by Toz on 2012-07-21
Yes. /usr/share/xubuntu/applications/defaults.list comes from the xubuntu-default-settings package, but I don't see how its setup in the system to take precedence over /usr/share/applications/defaults.list - it just does.

---

### Post by Morbius1 on 2012-07-21
I don't know if kpuz is getting anything out of this but I for one appreciate the information :wink:

---

### Post by Toz on 2012-07-21
Good point.

@kupz, to summarize:

To fix the problem for your specific user account, add the following:
```
x-scheme-handler/ftp=exo-file-manager.desktop
```
...to the end of **$HOME/.local/share/applications/mimeapps.list**

To fix it globally for all users, edit **/usr/share/xubuntu/applications/defaults.list** as root:
```
sudo leafpad /usr/share/xubuntu/applications/defaults.list
```
and change the line:
> x-scheme-handler/ftp=exo-web-browser.desktop
...to read:
```
x-scheme-handler/ftp=exo-file-manager.desktop
```
...and save the file.

---

