---
title: "How do I change/customize theme font color in the Files app?"
date: 2021-01-20
forum: Desktop Environments
---

### Post by zylstra on 2021-01-20
The font color of the Size and Modified columns of the Files app is gray.  How do I change this to black?

I got to the end of [this answer]("https://askubuntu.com/questions/1081207/ubuntu-18-04-file-manager-app-hard-to-read-columns") and almost found it ... but didn't, because the CSS file for Yaru only specified another resource.

... After writing the first two lines I now see the file gtk.gresource, but it's binary.  But it has readable CSS in it.  I am safe in modifying this?  Or can it cause problems that are not immediately noticeable?  Or is this totally the wrong way to do this?

---

### Post by Paddy Landau on 2021-01-21
> **zylstra said:**
> …  How do I change this to black?
You might want to look at installing an alternative theme. There are many themes available, but it's hard to find exactly what you want.

I'll describe the steps below.
> **zylstra said:**
> … it's binary.  But it has readable CSS in it.  I am safe in modifying this?
No, that's unsafe. You can try, of course — as long as you make a backup first! — but you might end up being unable to use your system and having to fix it via a Live disk!

To install an alternative theme…

[LIST=1]
[*]Install and enable the Gnome extension [User Themes]("https://extensions.gnome.org/extension/19/user-themes/").
[*]Also install Gnome Tweaks, either from the Software Store or via the terminal:
```
sudo apt install gnome-tweaks
```
[*]Search for Gnome themes online. I have found two useful resources:
• [Gnome Look]("https://www.gnome-look.org/browse/cat/")
• [Deviant Art]("https://www.deviantart.com/search?q=gnome%20shell")
There are other sources, but take care — these are unofficial themes and are therefore not guaranteed to be safe. Check the reviews and star ratings.
Some themes will be a complete makeover. Some will be just new icons, nothing else (that's probably what you're after). Some, just new cursors. And so on.
[*]Once you've found found a theme that you like, download the files that you want. A good location is your Downloads folder.
[*]Find the files, which are archive files, and extract their contents (each will be extracted into a separate subfolder). You might need to rename the subfolders to avoid duplicate names.
[*]Move the extracted folders into your folder [FONT=courier new]~/.themes[/FONT] (note the leading point). Create the folder if it doesn't already exist. (At this point, you can delete the original downloaded files.)
[*]Go to Gnome Tweaks > Appearance > Themes.
[*]Change the themes as required. They should be enabled immediately; if not, log out and in again (or restart the computer).
[/LIST]

---

### Post by Holger_Gehrke on 2021-01-21
Might [this blog entry]("https://securitronlinux.com/debian-testing/how-to-extract-the-files-from-a-gtk-3-0-gresource-file-to-allow-theme-editing/") be helpful ? If I understand the author right, you can use the program gresource (should be installed by default, if not it should be in the package libglib2.0-bin) to extract the files from gtk.gresource and change the theme to use the extracted files.

Holger

---

