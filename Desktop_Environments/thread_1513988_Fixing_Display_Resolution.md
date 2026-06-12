---
title: "Fixing Display Resolution"
date: 2010-06-20
forum: Desktop Environments
---

### Post by dkutagulla on 2010-06-20
If display is garbled due to incorrect resolution setting, and substituting Xorg.conf in /etc/X11 does not fix the issue, The display resolution can be fixed by changing the Resolution attribute of property tag in:

/home/<USERNAME>/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml

For example my laptop LCD did not suppor  1364x768resolution, By selecting this resolution, I garbled my display. I changed the unsupported resolution to a supported value in the above file.
(see below) 
I changed:
<property name="Resolution" type="string" value="1364x768"/>
to:
<property name="Resolution" type="string" value="1024x768"/>

This fixed the issue.

Looks like above file stores user's display customizations. can somebody confirm this?

Nonethe less hope this post helps users out there who r fixing their displays...

Divyanand

---

