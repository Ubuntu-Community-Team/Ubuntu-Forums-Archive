---
title: "Application icon and .ini file troubleshooting"
date: 2018-06-28
forum: Desktop Environments
---

### Post by jorgezapatero on 2018-06-28
I want to change the icon for [nixnote2]("http://nixnote.org").
Ubuntu 16.04 on my Thinkpad x240.

What I've tried:
I prepared my new icon image called evernote_icon.png and placed it in:
/usr/share/nixnote2/images/

I located the .desktop file and tried to reassign the Icon: ```
george@george-TP-X240:~$ cat /usr/share/applications/nixnote2.desktop 
[Desktop Entry]
Name=NixNote2
Comment=Use with Evernote to remember everything
GenericName=Evernote-clone
Exec=nixnote2
#Icon=/usr/share/nixnote2/images/windowIcon.png
Icon=/usr/share/nixnote2/images/evernote_icon.png
StartupNotify=true
Terminal=false
Type=Application
Categories=Qt;Utility;Network;
Keywords=NixNote2;Text;Evernote;note;

Actions=NewNote;
[Desktop Action NewNote]
Name=New Note
Exec=nixnote2 --newNote
OnlyShowIn=Unity;
```

No dice. I still see the original icon after rebooting. [Other tutorials I've found]("https://askubuntu.com/questions/894990/how-to-change-an-icon-in-16-04") only mention the steps I tried.

I discover there is a theme.ini file that references folders within /usr/share/nixnote2/images/ to define different themes I suppose.
Here is the first of many themes in theme.ini
```
george@george-TP-X240:/usr/share/nixnote2$ cat theme.ini 
[Classic NixNote]
windowIcon = /usr/share/nixnote2/images/classic-theme/windowIcon.png 
stackIcon =/usr/share/nixnote2/images/classic-theme/stack-green.png 
notebookSmallIcon = /usr/share/nixnote2/images/classic-theme/notebook-green.png
[...]

```
the other themes are
[Material Light], [Ubuntu Purple - 1] through [Ubuntu Purple - 5] and [Dark Editor]

I'm guessing one of these themes is being used by default. How do I know which one? Can I turn the themes off? What is a good resource to learn more about themes and .ini files?

First time posting. Open to critiques.
Cheers,
George

---

