---
title: "Gnome not respecting default programs"
date: 2008-06-22
forum: Desktop Environments
---

### Post by 8086 on 2008-06-22
It seems like Gnome does not respect the default programs I have set to open files. I have installed Acrobat Reader 8.1, and through the properties dialog for some pdf file, I have set Acrobat Reader as the default program to open pdfs.
[IMG]http://folk.ntnu.no/kopseng/bildegalleri/main.php?g2_view=core.DownloadItem&g2_itemId=4382&g2_serialNumber=1[/IMG]
That works good when browsing with Nautilus, but is seems that other Gnome programs does not respect these file specific settings.

If I download a file through "Save as..." in Firefox, and then double click that file in the "Downloads" window of Firefox, it opens using Evince!

I find this behaviour quite strange, because ```
grep evince /etc/gnome/defaults.list
``` gives me
[FONT="Courier New"]application/pdf=evince.desktop
application/postscript=evince.desktop
application/x-gzpostscript=evince.desktop[/FONT]

and .local/share/applications/defaults.list clearly overrides this:
[FONT="Courier New"][Default Applications]
application/pdf=/opt/Adobe/Reader8/Resource/Support/AdobeReader.desktop
application/vnd.adobe.xfdf=/opt/Adobe/Reader8/Resource/Support/AdobeReader.desktop
application/vnd.fdf=/opt/Adobe/Reader8/Resource/Support/AdobeReader.desktop
application/vnd.adobe.xdp+xml=/opt/Adobe/Reader8/Resource/Support/AdobeReader.desktop
application/vnd.adobe.pdx=/opt/Adobe/Reader8/Resource/Support/AdobeReader.desktop
application/fdf=/opt/Adobe/Reader8/Resource/Support/AdobeReader.desktop
application/xdp=/opt/Adobe/Reader8/Resource/Support/AdobeReader.desktop
application/xfdf=/opt/Adobe/Reader8/Resource/Support/AdobeReader.desktop
application/pdx=/opt/Adobe/Reader8/Resource/Support/AdobeReader.desktop[/FONT]

and the mime type association is also added in .local/share/applications/mimeapps.list:[FONT="Courier New"]
[Added Associations]
application/pdf=AdobeReader.desktop;[/FONT]

What can I do to make Firefox (and other programs) respect my settings?

---

### Post by diaa on 2008-06-22
Try the solution I proposed in [this thread]("http://ubuntuforums.org/showthread.php?t=831690")

---

### Post by 8086 on 2008-06-24
Thanks for the answer, but your solution will just replace "application/pdf=/opt/Adobe/Reader8/Resource/Support/AdobeReader.desktop" with "application/pdf=acroreader.desktop" in the defaults.list file.

I did try it out, though, just in case it did some magic I didn't think of in the first place, but unfortunately, no. My biggest problem seems to be that Firefox does not respect the mime type database supplied from Gnome.

---

### Post by 8086 on 2008-06-24
I found a wealth of information about the mime.cache and defaults.list files here:
[http://www.ces.clemson.edu/linux/fc4_desktop.shtml](http://www.ces.clemson.edu/linux/fc4_desktop.shtml)

Unfortunately nothing that can explain why Firefox does not respect my mime type settings...

---

### Post by 8086 on 2008-09-03
I found the solution! I still find that Gnome doesn't respect the hierarchy of the various locations, but that is a bug report for Launchpad. Anyway, here goes.

I searched for other versions of defaults.list, and it seems I missed one:
```

$ locate defaults.list|xargs ls -l
lrwxrwxrwx 1 root      root        24 2008-05-31 22:56 /usr/share/applications/defaults.list -> /etc/gnome/defaults.list
-rw-r--r-- 1 root      root      7283 2008-06-24 23:45 /etc/gnome/defaults.list-rw-r--r-- 1 root      root       242 2008-08-28 15:01 /usr/local/share/applications/defaults.list
-rw-r--r-- 1 root      root       242 2008-08-28 15:01 /usr/local/share/applications/defaults.list

```

I had fond the one in /usr/share (symlinked to /etc/gnome/) and the local one (in ~/.local/...), but had missed the one in /usr/local/share. This for some reason takes presedence over the local one, but by replicating the line in the local version into this file, I could finally click on pdf-files in the downloads panel of Firefox and have them open in Adobe Reader!

So these are know the relevant parts of the various defaults.list files:
```
 locate defaults.list|xargs grep -i --color pdf
/etc/gnome/defaults.list:application/pdf=/opt/Adobe/Reader8/Resource/Support/AdobeReader.desktop
/usr/local/share/applications/defaults.list:application/pdf=AdobeReader.desktop
/usr/local/share/applications/defaults.list.org:application/pdf=evince.desktop;AdobeReader.desktop
/usr/share/applications/defaults.list:application/pdf=/opt/Adobe/Reader8/Resource/Support/AdobeReader.desktop

```
You can see I renamed the old defaults.list file to defaults.list.org

---

