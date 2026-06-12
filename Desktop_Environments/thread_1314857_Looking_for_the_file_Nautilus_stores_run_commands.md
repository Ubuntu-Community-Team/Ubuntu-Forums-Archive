---
title: "Looking for the file Nautilus stores run commands"
date: 2009-11-04
forum: Desktop Environments
---

### Post by pjbgravely on 2009-11-04
I am trying to fix the feature/bug of Totem replacing existing window with new. I am looking for the file that Nautilus stores it's run commands for applications when a file is clicked on.

I thought that /usr/share/gconf/schemas/totem-handlers.schemas was it but it did nothing when changed.

I did find a work around but it will be tedious to implement and I would like to fix it at it's source.

Paul

---

### Post by PacSci on 2009-11-04
Actually, how Nautilus determines which commands to run for a file is a bit more complicated than that. When you double-click a file, its mimetype is determined, and then looked up in the 'defaults.list' file, which is either found in '~/.local/share/applications' or '/usr/share/applications'. The entry in 'defaults.list' for that mimetype refers to a '.desktop' file which is also found in one of those directories. The 'Exec' entry from that '.desktop' file is called with the given file.

The practical application of this is that if you are trying to fix this by adding an option to Totem's parameters, the easiest way to do it is to copy '/usr/share/applications/totem.desktop' to '~/.local/share/applications/totem.desktop' and change 'Exec=totem %U' to 'Exec=totem --whatever-option %U'. Based on your description of the problem, I would try the '--no-existing-session' option.

If this doesn't work, I have another idea, but it's somewhat more involved so I won't reveal it just yet.

---

### Post by pjbgravely on 2009-11-04
Thanks,

   I changed /usr/share/applications/totem.desktop to add the option which you guessed (--no-existing-session) and it worked system wide. I see that the user .desktop file might have been better but I can do that if it doesn't survive an update. 

   Thanks also for your incite on how nautilus works. 

Paul

---

