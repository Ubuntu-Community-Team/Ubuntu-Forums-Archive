---
title: "Corrupt fonts in 8.10"
date: 2008-12-03
forum: Desktop Environments
---

### Post by alienjon on 2008-12-03
I first tried upgrading to 8.10 from 8.04 and then just did a clean install of 8.10 but I'm having the same problem.  Basically the text in most of my programs (website text in firefox and typed text in kate, for example) is being displayed in a corrupt manner.  Basically it looks like the text was displayed in ink and then smudged so the words are unrecognizable.  If I highlight the text or scroll past the text and then back (forcing a redraw) the text will display until the window is redrawn (even if I simply scroll down)

Additionally, I've found that when I enable desktop effects, the menu items for several programs (notably kdevelop and the system tray item for knetworkmanager) simply won't display at all!  The underscore for the hotkey letters in menus will display but no text will be there.

Disabling desktop effects will turn those menu items from missing to the garbled text described above.

I think the only text not to display incorrectly are things directly associated with KDE 4 (system settings, the new 'main menu', yakuake, etc...) or (obviously) things that just don't use fonts (such as games)

I first noticed this after installing a bunch of packages that I don't think have anything to do with changing anything related to fonts on my system soon after installing the system (java, flash, firefox, kdevelop, etc...) (although I noticed it immediately after the time I had upgraded from 8.04.

I've tried changing display fonts from dejavu to something else, I've tried enabling and disabling antialiasing and forcing dpi.  I've tried installing mscorefonts and using one of those.  I've even tried completely removing the .kde and .kderc directory and file so that kde would regenerate them, but it still persists.

Any ideas how I could try fixing this?

---

### Post by alienjon on 2008-12-03
Ok, update on this.  If I disable the graphic driver the fonts display as they should.  I'm using nvidia version .96-9 (the latest, I believe).  I know that *-5 and earlier don't work with the 8.10 kernel, so I'm guessing this is an issue that nvidia needs to take care of.  Anyone have any potential info on this?

---

### Post by alienjon on 2008-12-03
Ok, almost completely solved, I think.  For some reason, the nvidia driver doesn't like to antialias fonts.  I just went into the 'Fonts' section of 'Apperance' in 'System Settings' and changed the excluded range to below the font sizes nvidia was using to display (I have mine set to 3px - 9px).  My only problem now is that some screens don't refresh themselves when they should (different from before, actually, now I notice in konsole (particularly yakuake) that previously typed lines/scrolled lines will remain and duplicate themselves on the screen)  In addition, I've also found that effects slow down my system MUCH more than compiz does (I'd rather use kwin, if possible, but I figured its worth noting here)

---

