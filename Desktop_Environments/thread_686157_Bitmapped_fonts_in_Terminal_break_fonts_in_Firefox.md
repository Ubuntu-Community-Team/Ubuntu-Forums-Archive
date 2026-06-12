---
title: "Bitmapped fonts in Terminal break fonts in Firefox"
date: 2008-02-02
forum: Desktop Environments
---

### Post by BattlePanic on 2008-02-02
I want to use a nice and crisp bitmapped font in gnome-terminal so I copied the bitmapped fonts that I'd like to use into my ~/.fonts directory but they weren't showing up in gnome-terminal's list of available fonts

It turns out that bitmapped fonts are not enabled by default in Ubuntu 7.10 Gutsy Gibbon.

Running the following in terminal:

```
sudo dpkg-reconfigure fontconfig-config
```

gave me a series of dialogs, one of which asked if I'd like to enable bitmapped fonts by default.  This did the trick and after restarting my X11 session, the bitmapped font I had installed, (along with some others that seem to have already been installed) were now showing up in the gnome-terminal's list of available fonts.

Unfortunately, this seems to have caused some side-effects in other programs.  Most noticeably, Firefox no longer displays certain fonts as it used to.  By enabling bitmapped fonts, I seem to have enabled a 'Times', 'Courier', and 'Helvetica' font among others that were previously unlisted.  I'm not even really sure where these particular fonts are stored on my system but Firefox seems to now render these bitmapped fonts for certain webpages and and input fields as opposed to whatever it has previously using.  The end result looks pretty bad, in my opinion.

I'm really only interested in using bitmapped fonts in the terminal and leaving everything else as it was.  Is there a better way to go about this without it breaking the fonts I'm currently using in other programs?

---

### Post by BattlePanic on 2008-02-03
I wanted to add a little followup for whomever may come across this.  I've managed to fix some of the font issues in Firefox by editing the font preferences.  It appears that the default font settings in Firefox change depending on whether or not bitmapped fonts have been enabled.

Default choices for the fonts used Firefox can be found under Edit -> Preferences -> Content -> Fonts & Colors -> Advanced.

Here is a comparison of what the preferences dialog shows with and without bitmapped fonts enabled

Firefox Font preferences (bitmapped fonts disabled):
----------------------------------------------------------
Fonts for: Western
Proportional: Serif	Size: 16
Serif: serif
Sans-serif: sans-serif
Monospace: monospace	Size: 12

Firefox Font preferences (bitmapped fonts enabled)
----------------------------------------------------------
Fonts for: Western	Size: 16
Proportional: Serif
Serif: Times
Sans-serif: Helvetica
Monospace: Courier	Size: 12

Times, Helvetica, and Courier fonts are bitmapped fonts and this is why so many pages were rendering with harsh and jagged fonts.  Adjusting the preferences back to the original defaults corrects the problem, for the most part.   Unfortunately, if a web page explicitly requests a font that exists on my system, Firefox will use it regardless of whether it is bitmapped or not.  So, in my case, if it asks for Helvetica, Firefox will use the bitmapped Helvetica that is on my system.

Right now, my only interest in bitmapped fonts is for use in a terminal emulator.  I'm happy to let all other applications ignore my system's bitmapped fonts entirely.  I think this would mean that I need bitmapped fonts enabled as a per-application setting rather than a systemwide setting.  I'm not sure if this is possible but if anyone knows how, please let me know.

---

