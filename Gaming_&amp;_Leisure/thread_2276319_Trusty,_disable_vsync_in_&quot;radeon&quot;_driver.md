---
title: "Trusty, disable vsync in &quot;radeon&quot; driver?"
date: 2015-05-01
forum: Gaming &amp; Leisure
---

### Post by Edward_Marsen on 2015-05-01
Hi everyone,

On amd64 Ubuntu 14.04.2 LTS, what is the **simplest **way to disable all kinds of vsync and disable all kinds of fps caps/limits in the "radeon" driver? I'm trying to play Quake Live through Wine and "vblank_mode=0" lets me have higher than 60 fps in windowed mode, but still stays capped at 60 in fullscreen mode. And yes, I am sure that all kinds of vsync are turned off in the game itself.

This is on a late 2008 Lenovo 17 inch laptop with
2 GHz T5800 Intel Core 2 Duo
4 GB system RAM
Discrete graphics: ATI Mobility Radeon HD 3650 (512 MB), with a (in case this matters) VGA IN/OUT connector (and accompanying IN/OUT switch)
Built-in 17 inch 1440x900 display

Please help.


Attached is a window capture of when I click on "About This Computer"

[ATTACH=CONFIG]261700[/ATTACH]

---

### Post by Edward_Marsen on 2015-06-02
Pretty please help :) :) :)

---

### Post by R33D3M33R on 2015-06-03
Did you try this: [https://wiki.archlinux.org/index.php/ATI#Turn_vsync_off](https://wiki.archlinux.org/index.php/ATI#Turn_vsync_off)

---

### Post by Edward_Marsen on 2015-06-09
Thanks R33D33M33R :)

Can you or someone please help me out with carrying out the instructions on the page you linked?
Do you think this method is applicable to Ubuntu even though it's on archlinux.org?
Do you think this method will work for fullscreen mode in addition to windowed mode?
If so,
What program/application should I use to "create ~/.drirc" ? Would gedit work?
What kind of text file should I compose it as?
What file type and file extension should I save it as?
What does the "~" symbol mean?
In what folder should I end up leaving the created file in?

Cheers :)

---

### Post by deadflowr on 2015-06-10
> Do you think this method is applicable to Ubuntu even though it's on archlinux.org?
Yes
> Do you think this method will work for fullscreen mode in addition to windowed mode?
It Should
> If so,What program/application should I use to "create ~/.drirc" ? Would gedit work?
Gedit is totally fine, it's only a simple text file anyway.
> What kind of text file should I compose it as?
Simply copy and paste it from the Arch page.
> What file type and file extension should I save it as?
No extension necessary, this isn't Windows...
> What does the "~" symbol mean?
the ~ symbol means /home, so ~/.drirc simply shortens /home/user/.drirc
> In what folder should I end up leaving the created file in?
Home. 
Put in the same place that your folders such as Pictures Videos and Documents is located.
Otherwise known as the top level of your home folder.
If that makes sense.
Just remember to put a dot at the front of drirc.
The dot makes the file hidden and the system is designed to look for that file as a hidden file.
Also, if that makes sense.

---

