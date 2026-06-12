---
title: "HELP: increase font size in online Help for OpenOffice"
date: 2006-02-19
forum: Desktop Environments
---

### Post by najevi on 2006-02-19
GNOME Desktop **2.12.1** (Ubuntu-Breezy 5.10)
 Screen Res = **1280**x**1024** (I want to keep this resolution)
OO.o help package = **openoffice.org2-help-en-us**


Using  the Font Preferences applet (**System **-> **Preferences** ->** Font**) I can tweak font sizes up from 10pt to 12pt across the 4 available fields (Application, Desktop, Window title, Terminal).

Tweaking the Application font size *does* affect text in the left hand navigation window of OO.o online Help (i.e. Bookmarks, Contents, Index, Find) but it *does not* increase the font size of the Help text that is in the main body window to the right.

[B]Do you know a solution for increasing the font size?

[/B][SIZE=2]***_Temporary Workaround_***:
[/SIZE][FONT=Verdana][SIZE=2]I found these lines to tweak. [/SIZE][/FONT][FONT=Courier New][FONT=Verdana][SIZE=2]*Your language may be different than *[B]en
[/B][/SIZE][/FONT][/FONT][SIZE=2][COLOR=Blue]sudo gedit[/COLOR][/SIZE][FONT=Courier New][FONT=Courier New][COLOR=Blue] /usr/lib/openoffice2/help/**en**/default.css[/COLOR][/FONT][/FONT]
[html]h1, h2, h3, h4, h5, h6
    { margin-bottom: 5pt; }

p, td
    { font-size: 10pt; margin-top: 2px; margin-bottom: 2px;}

h1
    { font-size: 18pt; border-bottom: 1px solid black; padding-bottom: 6px; margin-bottom: 6px;}

h2
    { font-size: 14pt; }

h3
    { font-size: 12pt; }

h4, h5, h6
    { font-size: 10pt; }
[/html] 
After closing and relaunching the OO.o tool of interest this certainly has the desired effect. *The trouble with this hack is that it affects all users.* I'd prefer this to be custom to my user login. Another user who prefers an 800x600 desktop resolution is going to be in for a [SIZE=5]big shock[/SIZE] when they open online help from within an OpenOffice.org app!

**Is there a more elegant (GUI based) method of adjusting this on a per-user basis?**

---

