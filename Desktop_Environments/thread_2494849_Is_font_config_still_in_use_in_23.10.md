---
title: "Is font config still in use in 23.10?"
date: 2024-01-29
forum: Desktop Environments
---

### Post by toft6633 on 2024-01-29
Hello,

I am on Ubuntu 23.10. As the title says, do I wonder if font config is used in 23.10. I tested with disabling antialiasing, and when I run "fc-match --verbose Sans" it says antialiasing is disabled. However Firefox and Chromium are still antialiased. I even renamed the directory "/etc/fonts/conf.d" without noticing any differences.

What I really want is to disable subpixel-rendering, and I have done so both in Gnome twekas and in font config. However when neither Firefox or Chromium seem to honor font config settings, I don't know it is disabled.

A clarification would be appareciated.

Fred

---

### Post by Holger_Gehrke on 2024-01-29
Are you using the snap versions of these browsers ? snaps are a system within the system and each comes with their own configuration for everything and I wouldn't be surprised at all if that included a font config.

If 'snap list' on the command line shows the programs in question then you're probably using the snap versions.

Holger

---

### Post by toft6633 on 2024-01-29
Thanks,

'snap list' shows both Firefox and Chromium. 

Fred

---

### Post by Holger_Gehrke on 2024-01-29
Then you have two options:

[LIST=1]
[*]use something else for testing (snaps are compressed read-only file system images and the programs in a snap can not even see - much less read - anything that is part of the normal system except for your home directory and a few other selected places) 
[*]remove the snap(s) and install the browsers from a PPA. Instructions for that can be found here in the forum, it's not quite trivial since you need to set some priorities so the next update doesn't bring back the snap instead of updating the normal package. 
[/LIST]
 
Holger

---

### Post by toft6633 on 2024-01-30
Thanks,
I am not sure I like the snap thing... Fonts are essential in Linux and I want to control it. I am testing OpenSuse Leap with Plasma. Maybe I stay with it.

Fred

---

