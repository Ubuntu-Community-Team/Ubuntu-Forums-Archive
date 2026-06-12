---
title: "Xubuntu network support?"
date: 2006-07-17
forum: Desktop Environments
---

### Post by rodrigo666 on 2006-07-17
I'm using Xubuntu in a network with another Ubuntu and a third one with Ubuntu/WindowsXP.

The one with just Ubuntu is browsing network fine.

The one with Ubuntu/WindowsXP, when it's on the second OS, don't, but that's my fault caused by lack of time.

Neverless, I don't have any clue on how to configure my Xubuntu to network and, specially, browse others PC's.

I'm starting to believe that Xubuntu don't do that, but if it's true, than it's a serious fault, don't you agree?

---

### Post by alanphil on 2006-07-17
I just started playing with Xubuntu, but I believe you have at least two options:

1. Install SSH client and server on your Ubuntu machines. From the command line on the Xubuntu machine, you will be able to SSH into the other machines and browser, copy files, etc. Google "SSH", "scp", to get more information. You could probably also FTP into the other machines, but it isn't as sexy. ;) 

2. I believe there may be GUI network clients that you can run on Xubuntu to browse the network as you do under Ubuntu. Hopefully someone jumps into this thread with the names of popular network tools that work under Xubuntu.

---

### Post by Liam on 2006-07-17
No, it's not a fault. You can install something that'll browse a Windows network graphically (like Nautilus) or use command line tools.

xfce attempts to be something of a middle-ground between GNOME/KDE and WM's like fluxbox and blackbox. It assumes that you'll be using command-line tools for many of the tasks that you would "normally" use a GUI for in GNOME.

Try opening up a terminal, and entering:
```

smbclient -L MACHINENAME

```

...where the machine name is either the NT name or the IP of the machine you want to browse. It'll give you a list of all the shares on that particular machine.

If you just want to see everything that's available, try:

```

smbtree

```

---

