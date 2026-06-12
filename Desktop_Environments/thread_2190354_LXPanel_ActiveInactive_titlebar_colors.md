---
title: "LXPanel Active/Inactive titlebar colors"
date: 2013-11-27
forum: Desktop Environments
---

### Post by Elastic_Potential on 2013-11-27
Hey everyone,

The LXDE forum isn't working for whatever reason, so I was wondering if someone here knew how to edit these colors.  These variables aren't available in the LXPanel settings.  Anyone know?

---

### Post by Rex Bouwense on 2013-11-27
Are you talking about the color of the fonts?  If so you should be able to change the color under Panel Preferences->Appearance.  You can also change the background there as well.

---

### Post by Elastic_Potential on 2013-12-01
> **Rex Bouwense said:**
> Are you talking about the color of the fonts?  If so you should be able to change the color under Panel Preferences->Appearance.  You can also change the background there as well.

Thanks for the reply.  While the ability to change font and overall panel design is available in that Appearance dialog box, options to change the background color of the buttons themselves aren't there.  I assume this would be a value in the GTK theme, but I simply can't find which value it would be.

---

### Post by Dennis N on 2013-12-02
The background color of the window buttons is controlled in the theme config files in some cases - for example, using Xubuntu's Greybird theme, selected background color sets it. I believe this was also true with the Lubuntu default theme. This may not be true with other themes.

See **/usr/share/themes**, then your particular theme in there.

---

### Post by Elastic_Potential on 2013-12-11
> **Dennis N said:**
> The background color of the window buttons is controlled in the theme config files in some cases - for example, using Xubuntu's Greybird theme, selected background color sets it. I believe this was also true with the Lubuntu default theme. This may not be true with other themes.

See **/usr/share/themes**, then your particular theme in there.

I had assumed as much, but despite combing through the gtkrc file a couple times, I can't find any corresponding value.  I'll post the results once I find them.

---

### Post by Elastic_Potential on 2013-12-18
Well, I think the solution might be in lxpanel.  Mayhaps I'll tamper with the source code sometime if that's possible.  However, as was said, it looks like there's no way to change these colors without setting the window background to something different.

Solved, I s'pose.

[ATTACH=CONFIG]248702[/ATTACH]

---

