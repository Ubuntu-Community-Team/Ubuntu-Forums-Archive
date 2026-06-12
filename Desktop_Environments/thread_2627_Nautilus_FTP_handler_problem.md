---
title: "Nautilus FTP handler problem"
date: 2004-10-29
forum: Desktop Environments
---

### Post by cloudless on 2004-10-29
Nautilus supports the FTP protocol, however it seems to support ASCII transfer mode only. If I upload a binary file (e.g. ZIP), it gets corrupted after the transfer. Is it a bug or is there any way I can adjust this behavior?

The second problem with the FTP protocol in Nautilus is that when I open a text file using gedit, the file becomes read-only. I have to use Kate in order to edit the files, however KDE apps don't seem to support font smoothing in Gnome.

Regards,
Sunny
[http://cloudless.net](http://cloudless.net)

---

### Post by kaput on 2004-10-30
I'm having the same problem. I tried using mounting a folder on an FTP server to use for photos for my website. They become terribly corrupted during the upload. Does the new point release fix this?

> Nautilus supports the FTP protocol, however it seems to support ASCII transfer mode only. If I upload a binary file (e.g. ZIP), it gets corrupted after the transfer. Is it a bug or is there any way I can adjust this behavior?

The second problem with the FTP protocol in Nautilus is that when I open a text file using gedit, the file becomes read-only. I have to use Kate in order to edit the files, however KDE apps don't seem to support font smoothing in Gnome.

Regards,
Sunny
[http://cloudless.net](http://cloudless.net)

---

### Post by jdong on 2004-10-30
File a bug report, and perhaps the Ubuntu people can patch it for Warty.

---

### Post by kaput on 2004-10-30
[QUOTE=jdong]File a bug report, and perhaps the Ubuntu people can patch it for Warty.[/QUOTE]

There is an upstream bug filed here:

[http://bugzilla.gnome.org/show_bug.cgi?id=155271](http://bugzilla.gnome.org/show_bug.cgi?id=155271)

---

### Post by dkitty on 2004-12-03
Ditto. I'm having the same problem running the ppc version of ubuntu on a 333mhz iMac DV. It doesn't seem to matter weather I'm using ftp to connect to a windows, linux, or Mac OS X server. The problem is the same. Er... if that information is at all helpful.

Has anyone found a viable solution? A work-around? Is there a graphic ftp program available from the ubuntu servers by apt-get? Will things like gFTP work or do they depend on the processes built into Gnome? I'm fairly new to linux and I LOVE Ubuntu, but I need FTP. Suggestions would be greatly appreciated.

---

### Post by dkitty on 2004-12-03
And thanks for the gnome bug report link kaput!

---

### Post by jdong on 2004-12-03
I personally use gftp for ANY ftp activities beyond just anonymous downloading. GFTP is **not** affected by this, and gftp is in Universe.

---

### Post by kaput on 2004-12-04
Another decent option is using the FireFTP extension for Firefox. You can pull up FireFTP via "Tools" after the extension is installed.

[FireFTP](https://update.mozilla.org/extensions/moreinfo.php?application=firefox&id=272&vid=1270)

---

### Post by dkitty on 2004-12-05
[QUOTE=jdong]I personally use gftp for ANY ftp activities beyond just anonymous downloading. GFTP is **not** affected by this, and gftp is in Universe.[/QUOTE]
 Thanks jdong and kaput. I installed gftp by apt from Universe and am impressed. It's a nice piece of work.

---

### Post by kaput on 2004-12-14
OK. According the bug report, this is fixed in libgnomevfs 2.8.3. However, when I try to install the Debian libgnomevfs 2.8.3 deb, it says it conflicts with libgnome2. 

Anybody figured out an easy way around this? It would be *really* nice to be able to use Nautilus' "Connect to Server" feature.

---

### Post by jdong on 2004-12-14
If you can identify the exact, split-out .diff with this Nautilus FTP patch, file it with the Ubuntu bugzilla, and hopefully we'll get a warty update with this!

P.S. Blatently installing that one .deb won't work!

---

