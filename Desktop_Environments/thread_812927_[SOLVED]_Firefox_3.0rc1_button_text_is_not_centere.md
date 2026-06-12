---
title: "[SOLVED] Firefox 3.0rc1 button text is not centered on Google homepage"
date: 2008-05-30
forum: Desktop Environments
---

### Post by heatpumpcontrol on 2008-05-30
Hello, I have this issue that started after the upgrade to FF3.0 rc1 which is more of an annoyance than anything else. 

On the Google home page the search button text is off centered. I tried to install Firefox widgets to no avail. I don't know how the button text is on other sites because I don't have anything else to compare it. Does anyone else have this problem? Has anyone found a solution?

Thanks

[IMG]http://ubuntuforums.org/picture.php?albumid=211&pictureid=660[/IMG]

---

### Post by DJ_Peng on 2008-05-30
It looks to me that you have a font (or zoom level) that doesn't want to fit in the dimensions that Google has set for their buttons. I get that sometimes on various sites. I figure it's simply because I'm using a bigger font size than the site designer had in mind when they created the code for the page.

---

### Post by @_R_|\/|_@_G_E_|)_|)_0|\| on 2008-05-30
You know, I sorta had the same problem... Once, I was just going through Ubuntu forums and suddenly my zoom suddenly went out! It was really annoying. It might be one of your settings or one of your recent add-ons. I checked it out to see that minimum font had been applied! Somehow it had automatically turned itself on somehow:confused:

Anyhoo, disabling it I restarted Firefox and 'Shazzam!' The problem just seemed to go away!:)

---

### Post by heatpumpcontrol on 2008-05-30
Thanks guys, I'll try this out... I'll report back as to which one corrected the problem....

Edit: Well I've tried all kinds of things ie: FF settings and the O/S settings and neither has made a change. Any specific font settings that someone knows about?

Thanks

---

### Post by DJ_Peng on 2008-05-31
Two possibilities. Are you overriding the minimum font size for sites in Fx? (It's in the Advanced Fonts settings as Allow pages to choose their own fonts. The box should be checked IMO.) The second is your zoom level. Try hitting Ctr-0 (zero) to reset the zoom size, and also View > Zoom > Reset. That may be a bit of a long shot but it's worth trying if only to rule it out. I'm attaching a screen shot to show what my buttons on iGoogle look like. My font settings are:

[LIST]
[*]**Firefox:**
[LIST]
[*]Default font: DejaVu Sans 11
[*]Proportional: Sans Serif 11
[*]Serif: DejaVu Serif
[*]Sans-serif: DejaVu Sans
[*]Monospace: DejaVu Sans Mono 12
[*]Minimum font size: 11
[*]Allow override: TRUE
[/LIST]
[*]**OS (Ubuntu Hardy with the Mac4Lin Graphite 0.4 theme:**
[LIST]
[*]Application Font: DejaVu Sans ExtraLight 10
[*]Document Font: <same>
[*]Desktop Font: <same>
[/LIST]
[/LIST]
I hope that helps.

---

### Post by heatpumpcontrol on 2008-05-31
Yay! I figured it out. Yes I did Peng, I have altered my default fonts. I started playing around with each of them until I came across the culprit. The funny thing is I started with the lower options first "Fixed width fonts" and worked my way up and guess which one it was....? lol it was the top most option.."Application Font".

I don't know which one I had selected but I can tell you which one works great...."Bitsream Vera Sans Oblique". Everything is centered now. I was even having issues with some program settings that would pop up a separate window for its' settings. That's when I got frustrated and started messing around with all the fonts and that's also when I realized that it wasn't a FF setting but a system setting. 

Anyway I have it all working now. The pop up window and FF. :lolflag:

---

### Post by DJ_Peng on 2008-06-01
Glad to hear you got it working. I can never remember which font changes what in the system settings.:lolflag:
You should go in to the Thread Tools and mark it as Solved. That way people will know there's a solution in the thread in case they have the same issue.

---

### Post by heatpumpcontrol on 2008-06-01
> **DJ_Peng said:**
> Glad to hear you got it working. I can never remember which font changes what in the system settings.:lolflag:
You should go in to the Thread Tools and mark it as Solved. That way people will know there's a solution in the thread in case they have the same issue.

Yes, and thank you for your responses....

---

