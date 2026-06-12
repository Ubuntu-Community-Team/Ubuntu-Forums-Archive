---
title: "compiz config:  convert from gconf -&gt; gsettings?"
date: 2014-10-24
forum: Desktop Environments
---

### Post by jwcalla on 2014-10-24
Hi,

I'm hoping somebody has some ideas for this one.

I just upgraded from 12.04.5 to 14.04.1 and in the process lost all of my compiz settings.  I have all the directories backed up (~/.compiz*, ~/.gconf/apps/compiz*, ~/.config/compiz*) and it doesn't look like there were really any changes made in those files during the upgrade.

If I understand correctly, they've moved from using the gconf file structure backend to using gsettings.  Is there a way to "import" my previous gconf-style settings into the new mechanism?

I did try running "[COLOR=#333333][FONT=monospace]gsettings-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]data-convert --file=[/FONT][/COLOR][COLOR=#333333][FONT=monospace]/usr/lib/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]compiz/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]migration/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]compiz-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]profile-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]active-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]unity.convert[/FONT][/COLOR]" manually but that didn't seem to accomplish anything.

Thanks,
John

---

