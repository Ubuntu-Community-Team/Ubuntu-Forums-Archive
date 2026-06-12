---
title: "Interesting OpenOffice numbering problem"
date: 2009-01-06
forum: General Help
---

### Post by all13d on 2009-01-06
This is a bit of a problem for me.

If I go into OpenOffice Writer, and try to create an outline list, once the number gets past III, the text is large enough to push the end point past the tab marker.  The attachment results.

Is there any way to fix this?  I'm surprised my googling didn't turn up anything; apparently not many others use outline lists.

P.S.: I'm running Openoffice v3, but the same problem happened in 2.4 on Hardy.  It's just getting pretty annoying these days.

---

### Post by chaplanger on 2009-01-06
Your spacing problem occurs because Openoffice places the text following the outline numbering too close to the period -- thus causing the text to move to the next tab stop.  The best way to adjust for what you want is to create a template outline with the tabs set to where you want them.

Begin a new document.  Begin your outline with sub points (you will have to put in some type of text in order to keep the outline subpoints).  Once you have this started go to format / Bullets and Numbering and choose the position tab.  Change the settings until you get the spacing you desire at each level of the outline.  Then save the document and use it as your outline template.

Openoffice 'help' can tell you how to save the document as a template if that is what you would prefer to do. 

Best of luck.

---

### Post by all13d on 2009-01-07
I know this is a simple solution, but is there any *real* way to bring it to the attention of the OpenOffice devs?  For someone who uses outlines a lot, this bug is a killer.

This is the default style, btw.  I haven't mucked with it.

---

### Post by chaplanger on 2009-01-12
You can go to Openoffice.org and forums if you like -- it seems many have mentioned this in the past (it supposedly began with Open Office 3.0).  If you begin a thread -- leave your example of what the situation looks like.  Also it would be good to emphasize that this occurs in the initial created document BEFORE it is saved into any format (Some seem to want to claim that it only happens when saved to .doc -- MS style).  As you probably already know -- this is a problem even before saving the document.

I agree with you that it is definitley is a problem that should be addressed by Openoffice though.

---

