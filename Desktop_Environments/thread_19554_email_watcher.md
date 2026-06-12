---
title: "email watcher"
date: 2005-03-12
forum: Desktop Environments
---

### Post by bigjoe on 2005-03-12
why is the email watcher gone in hoary? it is the main thing in your desktop... 

peace,
bj

---

### Post by bored2k on 2005-03-12
[QUOTE=bigjoe]why is the email watcher gone in hoary? it is the main thing in your desktop... 

peace,
bj[/QUOTE]
 This looks good
[http://www.nongnu.org/mailnotify/](http://www.nongnu.org/mailnotify/)

I'm actually about to compile it btw.

---

### Post by bigjoe on 2005-03-12
found it, but this is not the one was in warty's desktop. why they throw it away? 

bj

---

### Post by dolson on 2005-03-12
[QUOTE=bored2k]This looks good
[http://www.nongnu.org/mailnotify/](http://www.nongnu.org/mailnotify/)

I'm actually about to compile it btw.[/QUOTE]

Why not just install it from Synaptic (assuming you use Hoary)?

---

### Post by bored2k on 2005-03-12
[QUOTE=dolson]Why not just install it from Synaptic (assuming you use Hoary)?[/QUOTE]
 bored@noir:~$ apt-cache search mailnotify
bored@noir:~$


??

---

### Post by dolson on 2005-03-12
[QUOTE=bored2k]bored@noir:~$ apt-cache search mailnotify
bored@noir:~$


??[/QUOTE]
 $ apt-cache show mail-notification
Package: mail-notification
Priority: optional
Section: universe/gnome
Installed-Size: 1116
Maintainer: Pascal Giard <evilynux@yahoo.com>
Architecture: i386
Version: 1.0-1
Depends: libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.9.0), libbonobo2-0 (>= 2.8. 0), libbonoboui2-0 (>= 2.5.4), libc6 (>= 2.3.2.ds1-4), libeel2-2 (>= 2.9.1), lib gail-common (>= 1.6.6), libgail17 (>= 1.6.6), libgconf2-4 (>= 2.7.3.1), libglade 2-0 (>= 1:2.3.6), libglib2.0-0 (>= 2.6.0), libgmime2.1, libgnome2-0 (>= 2.8.0), libgnomecanvas2-0 (>= 2.6.0), libgnomeui-0 (>= 2.8.0), libgnomevfs2-0 (>= 2.9.1) , libgnutls11 (>= 1.0.16), libgtk2.0-0 (>= 2.5.6), libice6 | xlibs (>> 4.1.0), l iborbit2 (>= 1:2.12.0), libpango1.0-0 (>= 1.8.0), libpopt0 (>= 1.7), libsasl2 (> = 2.1.19), libsm6 | xlibs (>> 4.1.0), libsoup2.2-7 (>= 2.2.1), libx11-6 | xlibs (>> 4.1.0), libxml2 (>= 2.6.11), zlib1g (>= 1:1.2.1), debconf (>= 0.5) | debconf -2.0, gconf2 (>= 2.6.2-1)
Filename: pool/universe/m/mail-notification/mail-notification_1.0-1_i386.deb
Size: 247400
MD5sum: 0826fe57392ab0f5aa561fc6fce0eb3b
Description: Mail notification in system tray
 mail-notification works with system trays implementing the
 freedesktop.org System Tray Specification, such as the GNOME Panel
 Notification Area, the xfce4 Notification Area and the KDE System Tray.
 .
  Mail Notification features include:
   * multiple mailbox support
   * mbox, MH, Maildir, Sylpheed, POP3, IMAP and Gmail support
   * SASL authentication support
   * APOP authentication support
   * SSL/TLS support (disabled, see README.Debian)
   * automatic detection of mailbox format
   * immediate notification (depends on your settings)
   * HIG 2.0 compliance
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by bored2k on 2005-03-13
[QUOTE=dolson]$ apt-cache show mail-notification
Package: mail-notification
Priority: optional
Section: universe/gnome
Installed-Size: 1116
Maintainer: Pascal Giard <evilynux@yahoo.com>
Architecture: i386
Version: 1.0-1
Depends: libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.9.0), libbonobo2-0 (>= 2.8. 0), libbonoboui2-0 (>= 2.5.4), libc6 (>= 2.3.2.ds1-4), libeel2-2 (>= 2.9.1), lib gail-common (>= 1.6.6), libgail17 (>= 1.6.6), libgconf2-4 (>= 2.7.3.1), libglade 2-0 (>= 1:2.3.6), libglib2.0-0 (>= 2.6.0), libgmime2.1, libgnome2-0 (>= 2.8.0), libgnomecanvas2-0 (>= 2.6.0), libgnomeui-0 (>= 2.8.0), libgnomevfs2-0 (>= 2.9.1) , libgnutls11 (>= 1.0.16), libgtk2.0-0 (>= 2.5.6), libice6 | xlibs (>> 4.1.0), l iborbit2 (>= 1:2.12.0), libpango1.0-0 (>= 1.8.0), libpopt0 (>= 1.7), libsasl2 (> = 2.1.19), libsm6 | xlibs (>> 4.1.0), libsoup2.2-7 (>= 2.2.1), libx11-6 | xlibs (>> 4.1.0), libxml2 (>= 2.6.11), zlib1g (>= 1:1.2.1), debconf (>= 0.5) | debconf -2.0, gconf2 (>= 2.6.2-1)
Filename: pool/universe/m/mail-notification/mail-notification_1.0-1_i386.deb
Size: 247400
MD5sum: 0826fe57392ab0f5aa561fc6fce0eb3b
Description: Mail notification in system tray
 mail-notification works with system trays implementing the
 freedesktop.org System Tray Specification, such as the GNOME Panel
 Notification Area, the xfce4 Notification Area and the KDE System Tray.
 .
  Mail Notification features include:
   * multiple mailbox support
   * mbox, MH, Maildir, Sylpheed, POP3, IMAP and Gmail support
   * SASL authentication support
   * APOP authentication support
   * SSL/TLS support (disabled, see README.Debian)
   * automatic detection of mailbox format
   * immediate notification (depends on your settings)
   * HIG 2.0 compliance
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu[/QUOTE]
 Thank you, I was searching the wrong filename.

---

### Post by dolson on 2005-03-13
No problem. You know, if you use Synaptic, it's really cool. For example, I read this thread because I did a search on the board when I discovered my mail notification thingy was gone. I saw the link you posted and read it. It looked good, just like you said. I opened Synaptic and did a search for mail and then scrolled down the list of results until I saw it. :)

I used to hate Synaptic and did everything by the command-line utilities (when I was running Sid), but man, I can see the benefits of the GUI utilities now. :) (This isn't to say that you couldn't have found it via apt-cache search mail | grep noti or something, but anyhow.)

---

### Post by bored2k on 2005-03-13
[QUOTE=dolson]No problem. You know, if you use Synaptic, it's really cool. For example, I read this thread because I did a search on the board when I discovered my mail notification thingy was gone. I saw the link you posted and read it. It looked good, just like you said. I opened Synaptic and did a search for mail and then scrolled down the list of results until I saw it. :)

I used to hate Synaptic and did everything by the command-line utilities (when I was running Sid), but man, I can see the benefits of the GUI utilities now. :) (This isn't to say that you couldn't have found it via apt-cache search mail | grep noti or something, but anyhow.)[/QUOTE]
 the idea of that application + debian never crossed my mind at all.

I also prefer command line, but sometimes I have to select-unselect several files and its easier in GUI.

---

### Post by thtde on 2005-03-15
[QUOTE=bored2k]This looks good
[http://www.nongnu.org/mailnotify/](http://www.nongnu.org/mailnotify/)

I'm actually about to compile it btw.[/QUOTE]

Is it possible to configure this tool to watch all IMAP folders on a server? There is only an option to watch one specific folder but I have some more folders I want to watch.

---

