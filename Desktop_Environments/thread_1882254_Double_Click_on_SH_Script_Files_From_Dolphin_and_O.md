---
title: "Double Click on SH Script Files From Dolphin and Open and Run Them From Konsole"
date: 2011-11-17
forum: Desktop Environments
---

### Post by own3mall on 2011-11-17
Anyone know how I can double click on .sh script files from Dolphin and have them run in konsole / the terminal like they do in gnome using Nautilus?  I'm running Kubuntu 11.10

I've changed the file association of sh scripts to run the following:

```

[Desktop Entry]
Comment[en_US]=
Comment=
Exec=konsole --noclose -e "%f"
GenericName[en_US]=
GenericName=
MimeType=application/x-shellscript;
Name[en_US]=konsole
Name=konsole
NoDisplay=true
Path=
StartupNotify=true
Terminal=false
TerminalOptions=
Type=Application
X-DBUS-ServiceName=
X-DBUS-StartupType=
X-KDE-SubstituteUID=false
X-KDE-Username=

```

When I right click on sh files, I can choose open with, and then use konsole.  It launches konsole and runs my scripts properly....  however, when I double click on sh files when using the Dolphin File Manager, it does nothing.  I don't want to have to right click on my sh scripts and choose open with all the time.   I want them to open with konsole every time I double click on  any sh script.

What needs to be done?

All help is appreciated.

---

### Post by frijj2k on 2012-10-05
Here's a partial fix for your shell script problem...

[LIST]
[*]Right clink on a shell script and select "**Open With / Other...**"
[*]    In the "**Open with**" dialog, type "**bash**" (without the quotes) in the top field (titled "Open with...")
[*]    Put a tick in the box that reads: "**Run in terminal**"
[*]    Put a tick in the box that reads: "**Do not close when command exits**"
[*]    Put a tick in the box that reads "**Remember application association for this type of file**"
[*]    Click "**OK**"
[*]    Right clink on a shell script and select "**Properties**"
[*]    Select the "**Permissions**" tab
[*]    Un-tick the box that says: "**Is executable**"
[*]    Click "**OK**"
[/LIST]

Your script will now run in a terminal as you want it to. :)

Only one problem with this approach... Your scripts wont be executable from the terminal (command shell), so to run them you would have to type for example:

"**sh script.sh**" or "**bash script.sh**" (without the quotes)

rather than:

 "**./script.sh**" (without the quotes)

Hope this is of some use... Not great but works.

---

