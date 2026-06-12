---
title: "idesk command line options"
date: 2007-07-28
forum: Desktop Environments
---

### Post by promet on 2007-07-28
Hello,

I've just started down the road to configuring idesk. I am having a problem though. I run Fluxbox and need to run Nautilus with the "--no-desktop" option to prevent my desktop from reverting to Gnome and basically screwing my whole world up.

I have tried to enter this option in the "Command" section of my Nautilus.lnk file, like so:

```

table Icon
  Caption: Nautilus
  Command[0]: /usr/bin/nautilus --no-desktop 
  Icon: /usr/share/icons/Vista/128x128/apps/gnome-folder.png
  Width: 28
  Height: 28
  X: 43
  Y: 87
end

```But idesk seems not to be able to parse the command. It returns with:

```

promet@tgx:~$  Idesk starting in :0.0
[idesk] Background's file not found.
[idesk] Background's source not found.
/bin/sh: /usr/bin/nautilus --no-desktop: not found

```I've tried encapsulating the command in both single and double quotes, but no dice. Has anyone been able to pass command line options to idesk or have any bright ideas? I'd appreciate any help. Otherwise I may be stuck with the famously unattractive "Gnome-Commander"   :( . Thanks.

Promet

---

### Post by rjmdomingo2003 on 2007-11-08
Try configuring your .ideskrc file to point at your background/wallpaper folder.

I actually use the same *nautilus --no-desktop* icon-command.:)

---

### Post by rjmdomingo2003 on 2007-11-08
Check this out: [http://idesk.sourceforge.net/wiki/index.php/Idesk-usage](http://idesk.sourceforge.net/wiki/index.php/Idesk-usage)

Hope this helps.

---

