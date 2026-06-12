---
title: "Touchpad scroll keeps switching desktop"
date: 2012-08-23
forum: Desktop Environments
---

### Post by Mellifluous on 2012-08-23
I've decided to give Linux another try with Lubuntu. One thing that's driving me nuts is the touchpad scroll on my laptop keeps switching my desktop. Is there any way to prevent this? I saw another post that said going into some file and deleting lines with 'desktopprevious' and desktopnext' but those lines weren't in the file.

Also how can I disable touch to click on the touchpad? I can't see an option for it in the preferences.

---

### Post by marinara on 2012-08-24
Before restarting openbox with this command: openbox --reconfigure 
Edit ~/.config/openbox/lubuntu-rc.xml and remove these lines:
{{{
      <mousebind button="Up" action="Click">
        <action name="GoToDesktop">
          <to>previous</to>
        </action>
      </mousebind>
      <mousebind button="Down" action="Click">
        <action name="GoToDesktop">
          <to>next</to>
        </action>
      </mousebind>
}}}                  

thanks for asking, will be added to the wiki

---

### Post by kalehrl on 2012-08-24
> One thing that's driving me nuts is the touchpad scroll on my laptop  keeps switching my desktop. Is there any way to prevent this?
You could just go to Openbox Configuration Manager, Desktop tab and put 1 in 'Number of Desktops' field. This will save you from manually editing lubuntu-rc.xml.
> Also how can I disable touch to click on the touchpad?
This is available in the wiki.

---

### Post by Mellifluous on 2012-08-24
> **kalehrl said:**
> You could just go to Openbox Configuration Manager, Desktop tab and put 1 in 'Number of Desktops' field. This will save you from manually editing lubuntu-rc.xml.

Thanks! That was very simple.

---

