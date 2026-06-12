---
title: "How to Aiglx Compiz Session"
date: 2007-06-05
forum: Desktop Effects &amp; Customization
---

### Post by victorbrca on 2007-06-05
Hi all,


  Is there a way for me to add a separate login session with Aiglx, Compiz and Kiba-dock enabled? 

  I usually have to go to System => Preferences => GL Desktop and click on "Enable GL Desktop". But I would like to have a separate session for it.

  This is what I did:

```
victor@victor-laptop:/usr/local/bin$ cat /usr/local/bin/startcompiz.sh
#!/bin/sh
compiz-tray-icon
sleep 4
exec gnome-session
```

  I think "compiz-tray-icon" is wrong

```
victor@victor-laptop:/usr/local/bin$ cat /usr/share/xsessions/compiz.desktop 
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Compiz
Comment=Start a Compiz Session
Exec=/usr/local/bin/startcompiz.sh
Icon=
Type=Application
Name[en_US]=Compiz
```

  I can see the session and logon to it, however Compiz is not installed.

  I also found another 2 posts for same thing that apparently were not resolved...

[Post 1]("http://ubuntuforums.org/showthread.php?t=220637&highlight=aiglx+session")
[Post 2]("http://ubuntuforums.org/showthread.php?t=246853&highlight=aiglx+session")


Vic.

---

