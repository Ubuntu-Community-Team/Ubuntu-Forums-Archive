---
title: "Configuring Unity in 12.04- two questions"
date: 2012-09-10
forum: Desktop Environments
---

### Post by George Heine on 2012-09-10
Hello -

As the title indicates, have recently upgraded to 12.04 LTS on a Toshiba laptop.  Decided it's time to give Unity a try.  Two configuration questions:

1) On startup I would like a single terminal window to appear.   (Without having to type Ctl-Alt-T, or any other action).

2) Whenever I insert a USB device, system automounts it and displays a "file viewer window" (i.e., a window with icons for each top-level entry on the media filesystem).
Automounting is fine, but I don't need that window.  How can it be disabled? 

On 10.04,  the following may have done the trick (or did it just disable automounting?), but it seems to have no effect on the current system. 

```
gconftool --set /apps/nautilus/preferences/media_automount_open --type bool "false" 
```
Thanks -hopefully these are simple questions.

---

### Post by ranger1021994 on 2012-09-10
1) Go to Startup Applications > Add > Give name and in command type 
  "gnome-terminal" and click Add


2) Go to System Settings > Details > Removable media > Tick never prompt

Hope it helps

---

### Post by cortman on 2012-09-10
> **George Heine said:**
> Hello -

As the title indicates, have recently upgraded to 12.04 LTS on a Toshiba laptop.  Decided it's time to give Unity a try.  Two configuration questions:

1) On startup I would like a single terminal window to appear.   (Without having to type Ctl-Alt-T, or any other action).

2) Whenever I insert a USB device, system automounts it and displays a "file viewer window" (i.e., a window with icons for each top-level entry on the media filesystem).
Automounting is fine, but I don't need that window.  How can it be disabled? 

On 10.04,  the following may have done the trick (or did it just disable automounting?), but it seems to have no effect on the current system. 

```
gconftool --set /apps/nautilus/preferences/media_automount_open --type bool "false" 
```
Thanks -hopefully these are simple questions.

You can add startup applications by clicking the gear icon in the far right of the panel, and selecting "Startup Applications".

To disable nautilus opening automatically, go to
dconf-editor> org> gnome> desktop> media-handling> and uncheck automount_open.

---

### Post by George Heine on 2012-09-10
Thanks to both for the quick answers.   Have marked this thread as Solved.

One quick note on Cortman's solution of using dconf-editor to disable a nautilus window on automount.  To get access to dconf-editor, it was necessary to run

```
sudo apt-get install dconf-tools
```That's "dconf-tools" and NOT "dconf".  Neither of these packages is installed by default
(at least they weren't on my system).

---

### Post by cortman on 2012-09-10
> **George Heine said:**
> Thanks to both for the quick answers.   Have marked this thread as Solved.

One quick note on Cortman's solution of using dconf-editor to disable a nautilus window on automount.  To get access to dconf-editor, it was necessary to run

```
sudo apt-get install dconf-tools
```That's "dconf-tools" and NOT "dconf".  Neither of these packages is installed by default
(at least they weren't on my system).

This is true. Sorry for not specifying.

---

