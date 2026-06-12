---
title: "How to make a shell script run through the terminal"
date: 2011-03-04
forum: Desktop Environments
---

### Post by robro on 2011-03-04
Hi community,
I have a lot of shell script's on my desktop, and they don't launch the terminal to run them, they are executable, and I can run a terminal and cd to the desktop and run them from there, when I run gnome it does run them through the terminal.

Thanks for your help :)

---

### Post by vivek.pandey on 2011-03-04
your question is bit confusing but going by your threads title
its how  i run shell scripts...ofcourse they are stored with an extension sh
on terminal i type  sh myfilename if the file is in  my home directory and if some where else sh path_to_the_file

hope this helped

---

### Post by robro on 2011-03-04
ok let me explain more, I have shell scripts on my desktop, and in kde they only run if I start up the terminal manually and run them from there, in gnome it starts the terminal automatically and runs them.

---

### Post by robro on 2011-03-05
bump

---

### Post by robro on 2011-03-07
anyone help?

---

### Post by deconstrained on 2011-03-07
Do you want to run them by clicking on them? 
[http://kde-apps.org/content/show.php/run-in-terminal?content=105660](http://kde-apps.org/content/show.php/run-in-terminal?content=105660)
Or do you want to run them without having to cd into the desktop? Add :$HOME/Desktop to your path by putting this in your ~/.bashrc:

```

export PATH=$PATH:"$HOME/Desktop"

```

If you run them on a regular basis you could also just add them to cron and have them execute periodically on their own.

---

### Post by robro on 2011-03-07
i want to click on it to run it, when ever i try the script it gives me this error: run-in-terminal.desktop has no Type=... entry.
i have places in the right dir

---

### Post by deconstrained on 2011-03-07
If that's because you're using the run-in-terminal application then I can't help you; I'm not a developer of that program and don't have time to debug and test it for you.

I find myself wondering why KDE doesn't have this functionality in a working form while it's natively a part of GNOME.

---

### Post by krowe on 2013-02-18
This thread is old but it looks like no one actually posted an answer to the question. It looks like you just need to add a Type=Application line to your shortcuts. Here is the full contents of my links to a script file:

```
[Desktop Entry]
Comment[en_US]=
Comment=
Exec=/home/krowe/Scripts/web-sync-up.sh scsitest
GenericName[en_US]=
GenericName=
Icon=arrow-up-double
MimeType=
Name[en_US]=Sync SCSI-Test Up
Name=Sync SCSI-Test Up
Path=/home/krowe/Scripts
StartupNotify=true
Terminal=true
TerminalOptions=\s--noclose
Type=Application
X-DBUS-ServiceName=
X-DBUS-StartupType=
X-KDE-SubstituteUID=false
X-KDE-Username=

```

---

