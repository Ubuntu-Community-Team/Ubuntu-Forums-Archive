---
title: "Recovering from trying to change default file manager with Psychocats script"
date: 2009-05-06
forum: General Help
---

### Post by Penguin Guy on 2009-05-06
In general your tutorials are very good; but one that I didn't like much was the one about [COLOR=Blue][changing default file browsers]("http://www.psychocats.net/ubuntu/nonautilusplease")[/COLOR]. After I installed and later uninstalled the KDE desktop it left my default file browser as dolphin; I saw your script and tried to sue it to restore nautilus and despite it telling me that it had been successful - it didn't work.

I would advise three changes:

[LIST=1]
[*]Consider what happens if the script does **not** work.
[*]On your blog make it more clear that this fix **only** works if your script was used to change it in the first place.
[*]Go easy on the newlines :P.
[/LIST]

I would happily implement these changes and post them back here if you could tell me what each of the files actually contain (so the end user actually knows what the program is restoring (and because I want to know)).

My output (yeah; confusing):
```
~/Desktop$ ./restorenautilus.sh 

You're missing a Computer .desktop backup file--nothing to restore


You're missing a Nautilus .desktop backup file--nothing to restore


You're missing a folder handler .desktop backup file--nothing to restore


You're missing a Home .desktop backup file--nothing to restore


You're missing a Network backup file--nothing to restore. If you had Thunar as your previous default file manager, this is normal.


Nautilus should now be your new default file manager in Gnome again


```

---

### Post by aysiu on 2009-05-06
Did you read the disclaimer on that page? > This tutorial has not been updated since Ubuntu 6.06, and it will most likely never be updated here again. If you would like to copy this tutorial to the community site and update it, please feel free to do so. You have my blessing in advance.

Both the scripts on this page and the files they download are transparent&#8212;you can see everything each script is going to do (they're just text files). They are presented as-is, though. If you are unsure of what a command in the script does or need to verify (for your own peace of mind) the content of the files downloaded by the scripts, please consult members of the Ubuntu Forums.  I'm sure there are lots of folks who can help you hear to try to recover from this.

*restorenautilus.sh* is just a text file. Its contents are completely transparent, so you can see what it's trying to do. I'll post them here for easy reference: ```
#!/bin/bash
if [ -f /usr/share/applications/nautilus-computer.desktop.backup ]; then
  echo -e "\nRestoring Computer .desktop file\n"
  sudo cp /usr/share/applications/nautilus-computer.desktop.backup /usr/share/applications/nautilus-computer.desktop
else
  echo -e "\nYou're missing a Computer .desktop backup file--nothing to restore\n"
fi
if [ -f /usr/share/applications/nautilus.desktop.backup ]; then
  echo -e "\nRestoring Nautilus .desktop file\n"
  sudo cp /usr/share/applications/nautilus.desktop.backup /usr/share/applications/nautilus.desktop
else
  echo -e "\nYou're missing a Nautilus .desktop backup file--nothing to restore\n"
fi
if [ -f /usr/share/applications/nautilus-folder-handler.desktop.backup ]; then
  echo -e "\nRestoring folder handler .desktop file\n"
  sudo cp /usr/share/applications/nautilus-folder-handler.desktop.backup /usr/share/applications/nautilus-folder-handler.desktop
else
  echo -e "\nYou're missing a folder handler .desktop backup file--nothing to restore\n"
fi
if [ -f /usr/share/applications/nautilus-home.desktop.backup ]; then
  echo -e "\nRestoring Home .desktop file\n"
  sudo cp /usr/share/applications/nautilus-home.desktop.backup /usr/share/applications/nautilus-home.desktop
else
  echo -e "\nYou're missing a Home .desktop backup file--nothing to restore\n"
fi
if [ -f /usr/share/applications/network-scheme.desktop.backup ]; then
  echo -e "\nRestoring Network .desktop file\n"
  sudo cp /usr/share/applications/network-scheme.desktop.backup /usr/share/applications/network-scheme.desktop
else
  echo -e "\nYou're missing a Network backup file--nothing to restore. If you had Thunar as your previous default file manager, this is normal.\n"
fi
echo '
Nautilus should now be your new default file manager in Gnome again
'
``` I thought it was quite obvious that the restoration script would work only if you used one of the other scripts to remove Nautilus as the default in the first place. I'll put another disclaimer in, though, just in case.

---

