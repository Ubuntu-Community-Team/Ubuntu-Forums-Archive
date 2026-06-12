---
title: "Changing # of workspaces"
date: 2011-07-27
forum: Desktop Environments
---

### Post by cwhittier on 2011-07-27
I am running ubuntu 9.04, and need to change the number of workspaces to 1 from the command line. I am using this command in a script:

gconftool --set -t int /apps/metacity/general/num_workspaces 1

I can confirm in gconf-editor that the value is changed, but I can still scroll over to the second workspace with the mouse wheel. Can someone tell me why this isn't working?

---

### Post by jerrrys on 2011-07-27
don't know about terminal, but if you right click on workspaces and go to properties.  the # of workspaces can be changed from there. and are you aware of this:

[https://lists.ubuntu.com/archives/ubuntu-announce/2010-September/000137.html](https://lists.ubuntu.com/archives/ubuntu-announce/2010-September/000137.html)

---

### Post by cwhittier on 2011-07-27
I know how to change it via the panel, but that is not an option here. I need to be able to adjust this via script.

I am also aware that 9.04 is no longer a supported release, but being able to get updates is also irrelevant here.

---

### Post by CatKiller on 2011-07-27
> **cwhittier said:**
> I can still scroll over to the second workspace with the mouse wheel.

Then you probably aren't using Metacity as your window manager.

---

### Post by cwhittier on 2011-07-27
Hmm, do you have any idea what it might be using instead of metacity? gnome-session has metacity listed as the window manager, and I haven't made any system changes since installation other then to turn off gnome-panel. 

Also, not sure if this helps, but I am running this setup both on a virtual machine, and on a dedicated piece of hardware with a 640x480 touch screen. On the VM, I cannot scroll over with the mouse wheel even when set to more than one workspace, on the touch screen I can, but these installations should be the same. Is it possible that it has something to do with the monitor?

---

### Post by CatKiller on 2011-07-27
Probably Compiz. 2009 sounds about right for when it started to be installed by default, and enabled if the hardware was capable. The host of the VM could well be capable too, but hardware detection in a virtual machine is tricky business.

---

### Post by wojox on 2011-07-27
```
gconftool-2 -s /apps/metacity/general/num_workspaces 1 --type int
```

Log out and in. I thought the mouse wheel and compiz worked together?

---

### Post by cwhittier on 2011-07-28
> **CatKiller said:**
> Probably Compiz. 2009 sounds about right for when it started to be installed by default, and enabled if the hardware was capable. The host of the VM could well be capable too, but hardware detection in a virtual machine is tricky business.

I don't believe compiz is already installed, though I am unsure how to check. typing "ccsm" into a terminal tells me the compizconfig-settings-manager is not installed... And I'm pretty sure my touch screen system has lower specs than the VM's virtual hardware, so I would find it odd that something might be enabled there and not in my VM.  

Also, to wojox:
I included the code I was using to change the metacity workspaces in my original post, so I already know how to do that. I considered the compiz theory as 99% of the threads I found on this issue had compiz to blame, however as I just mentioned above, I don't think this is installed, though I am open to ways to check and be sure.

---

### Post by CatKiller on 2011-07-28
I don't think CCSM's ever been installed by default. It's not very user-friendly. The hyphenation is peculiar; it's compizconfig-settings-manager.

You can see if Compiz is installed in Synaptic (or *aptitude show compiz* from the command line), or by running it with ```
compiz --replace
```

It's not a question of whether the VM has better hardware, it's a question of whether the detection routines know that the VM has better hardware :)

You can still change the number of workspaces with GConf/Compiz, it's just a different key. Compiz' GConf structure's changed since then, so I can't tell you exactly the name of the key, but I'm sure you'll find it.

---

### Post by cwhittier on 2011-07-28
Ladies and Gentlemen we have a winner!

I did find that compiz was installed. It was not the number of workspaces however, it was the Horizontal Virtual Size in compiz, which does more or less the same thing - it extends your desktop, giving you scrollable access to the other sections.

For anyone with the same issue, the code to change it for me, is:

gconftool --set -t int /apps/compiz/general/screen0/options/hsize 1

Thanks everyone for your help with this.

---

