---
title: "How do i find what command an icon runs"
date: 2009-02-24
forum: General Help
---

### Post by darkenemy on 2009-02-24
Specifically, I am trying to figure out how to run a specific VirtualBox machine from a quick launch icon, but the process of doing so has lead me to another question.

How could I find the command that any given program runs, executed by my clicking an icon.  When I actually open VirtualBox through the command line, I then click a "start" button to start a virtual machine, but isn't it true that the button I click is somewhere translated to a command by the program (a process that the user doesn't see).

maybe i have my philosophy wrong, but i would like to know how to find the command run by a GUI and apply it to the command line, if for any other reason than just to know - as this will be a service to me in a number of other applications.

thanks in advance

---

### Post by pastalavista on 2009-02-24
right-click the menu item and add to desktop... right click desktop icon and select properties


edit: sorry.. never mind

---

### Post by howefield on 2009-02-24
> **darkenemy said:**
> Specifically, I am trying to figure out how to run a specific VirtualBox machine from a quick launch icon,..

The command would be

```
VBoxManage startvm name_of_vm
```

If you have spaces in the name of your vm, you would need to wrap the name with quotes.

---

### Post by snova on 2009-02-24
> **darkenemy said:**
> When I actually open VirtualBox through the command line, I then click a "start" button to start a virtual machine, but isn't it true that the button I click is somewhere translated to a command by the program (a process that the user doesn't see).

Not necessarily. It is possible that VirtualBox has another program somewhere that does that actual work, but that doesn't mean the button is bound to the program- just that it eventually runs that program.

In your case, however, VirtualBox takes a command line argument to start a particular VM.

```

$ VirtualBox --help
Sun xVM VirtualBox Graphical User Interface 2.0.6
(C) 2005-2008 Sun Microsystems, Inc.
All rights reserved.

Usage:
**  -startvm <vmname|UUID>     start a VM by specifying its UUID or name**
  -rmode sdl|image           select different render mode (default is sdl)

```

Try that.

---

### Post by darkenemy on 2009-02-24
Yup, the "virtualbox -startvm" command did the trick,

so is there no way to determine the command run by a gui?

thanks for the help

---

