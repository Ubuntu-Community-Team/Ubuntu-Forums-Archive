---
title: "I broke something (gdm?) controlling window appearance and themes"
date: 2009-01-02
forum: Desktop Environments
---

### Post by thinking2loud on 2009-01-02
I'm running 8.04.  I was trying to get some non-Ubuntu software to compile, so I think I messed up something associated with gtk.  

I have this problem in which one of the symptoms was that a bunch of software including eog forgot how to read .svg files.  I fixed that problem by upgrading librsvg to 2.22.3 (which is newer than what Synaptic gives you).  

The other problems are that window appearance is screwed up and themes/customization are not available.  There's weird scaling artifacts on some pictures (like the PNG Ubuntu on the top of this page).  And the title bar of windows is blue, instead of the usual orangey Human theme color.  When I try to go and reset the theme, the only one available is Custom, even though the files and everything for Human are in /usr/share/gdm/themes.  I have tried reinstalling gdm and everything else I could find associated with themes.

Any other good ideas?

---

### Post by VOLKOV9 on 2009-06-28
Similar story here.  I upgraded my gtk beyond the repos to get file-browser-applet to compile, and now I get blue windows and can't change theme (though I can still see the other themes... just clicking on them does nothing).  And yes, eog can't see .svg files, though I'll try your fix.

If you solved this (or if anyone else has any ideas), I'd be delighted to hear about it.

---

