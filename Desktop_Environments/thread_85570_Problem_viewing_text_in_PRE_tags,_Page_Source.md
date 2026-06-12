---
title: "Problem viewing text in PRE tags, Page Source"
date: 2005-11-03
forum: Desktop Environments
---

### Post by joshuapurcell on 2005-11-03
I'm having the weirdest problem with viewing some text in browsers. Here is when I'm unable to actually see the text on pages while browsing the web:

-anything in <pre> tags
-viewing the source of web pages in Firefox
-the search field at wiki.ubuntu.com

I can tell that there is text when I highlight the area... the screen shows that I've highlighted an area but the actual letters still do not show up. At first I thought this was a problem with my Opera browser, so I upgraded to the latest version (didn't solve the problem). Then I went back to my old Firefox browser and the same thing was happening... even after upgrading tonight to the newest 1.5 Release Candidate.

Something has to be messed up with the settings on my system other than the browser, but I'm not sure what it would be. Has anyone else had this problem?

Here is a screenshot of what my screen looks like if I pull up the source of this web page (or any other one) using Firefox. This is the exact same thing I get in any of the other scenarios listed above.

---

### Post by heimo on 2005-11-03
Try changing Monospace font (in FF1.5 this is in Edit->Preferences->Content->Fonts&Colors->Advanced
You may be missing some "core" fonts, but I'm not sure.

---

### Post by joshuapurcell on 2005-11-03
[QUOTE=heimo]Try changing Monospace font (in FF1.5 this is in Edit->Preferences->Content->Fonts&Colors->Advanced
You may be missing some "core" fonts, but I'm not sure.[/QUOTE]
Changing the Monospace font from 'Courier' to 'monospace' did fix it so that I'm able to view the page source and I believe <pre> tags are now working from the quick testing I've done, but the last thing that still isn't working is the wiki search field listed in my first post. I'm sure it's related to some font setting and I'll keep looking at it. I wonder what happened to my fonts...

Thanks for your help.

---

