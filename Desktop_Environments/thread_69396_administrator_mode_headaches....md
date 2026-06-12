---
title: "administrator mode headaches..."
date: 2005-09-26
forum: Desktop Environments
---

### Post by cypher35 on 2005-09-26
I am having trouble getting "Administrator Mode" to work in kde's control center.

Whenever i select admin mode in "Network Settings" or any other subsection that requires admin mode, i am prompted for my pasword and then redirected to the blue "Internet & Network" parent section page instead of "Network Settings".

I know this problem has been reported before on other web forums, but i have yet to see someone some up with a solution that doesn't involve ***sudo kdesu kcontrol*** or some other duct tape solution.

---

### Post by cypher35 on 2005-09-26
Here's a quick follow up to my above problem...  i can get admin mode to work by going to my "Theme Manager", selecting a new theme, and going back to my old theme.  However, the font settings change without telling them to do so.  Dispite having everything set to Lucida Grande 10, when i enter Admin Mode, i see a big bloated Bitstream Vera Sans 12 typeface staring back at me.  It's strange that it shows Lucida Grande 10 when it's greyed out in non-admin mode, but it changes back to a different font for admin mode.

---

### Post by GoldBuggie on 2005-09-26
The admin mode in control center is a bit buggy. To enter the admin modes of control center start it using "kdesu kcontrol"(I can recommend setting up a kmenu item for this). You will start kcontrol as root. When you get in admin mode these are the settings that are valid. So change the fonts in here.

When you need to change settings that only apply to the user then start kcontrol as normal.

---

