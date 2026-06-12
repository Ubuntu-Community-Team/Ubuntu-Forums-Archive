---
title: "Konqueror ftp not pasv stopped working"
date: 2007-11-05
forum: Desktop Environments
---

### Post by scott.craig on 2007-11-05
Hi All,

I have been using konqueror to connect to an FTP site that refuses passive connections. It was working fine until last Wednesday. I may have upgraded inadvertently.

When I try to connect, I get the connection dialog asking for the password. When I enter the correct password and hit enter, i receive the message dialog "Could not connect to host (the host name)"

I have unchecked the "Enable passive mode (PASV)" under System Settings > Network Settings > Connection Preferences (and rebooted after that, as well), but this does not help.

The curious thing is that I can connect to this server both by command line, and with gFTP in active mode. gFTP fails in passive mode, after asking for the password.

Is konqueror actually respecting the settings in System Settings? Is there a way to see the ftp commands that konqueror is attempting, like the log that gFTP displays?

---

### Post by TeaSwigger on 2007-11-05
> **scott.craig said:**
> Hi All,

I have been using konqueror to connect to an FTP site that refuses passive connections. It was working fine until last Wednesday. I may have upgraded inadvertently.

When I try to connect, I get the connection dialog asking for the password. When I enter the correct password and hit enter, i receive the message dialog "Could not connect to host (the host name)"

I have unchecked the "Enable passive mode (PASV)" under System Settings > Network Settings > Connection Preferences (and rebooted after that, as well), but this does not help.

The curious thing is that I can connect to this server both by command line, and with gFTP in active mode. gFTP fails in passive mode, after asking for the password.

Is konqueror actually respecting the settings in System Settings? Is there a way to see the ftp commands that konqueror is attempting, like the log that gFTP displays?

Good question. Is it as easy as launching Konq from a terminal? Perhaps it'd display actions and/or errors in the terminal? KDE has Kasablanca and Kftpgrabber for ftp, both in the repositories, if you need ftp in the meantime.

---

### Post by scott.craig on 2007-11-05
> Is it as easy as launching Konq from a terminal?
No, that only displays interaction between konqueror and the OS.

What I really need is to sniff the traffic between konqueror and the FTP site. I was hoping there is a simple way to do that already built in.

Thanks for the tip about the other clients. It was nice using konqueror while it worked. The remote files are treated the same as local files. They can be edited with the kate editor, and upon saving, konqueror sends them back to the remote server transparently. I wish it were still working.

---

