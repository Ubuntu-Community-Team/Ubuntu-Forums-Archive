---
title: "How to configure double-clicking window icon/button to close window"
date: 2011-11-30
forum: Desktop Environments
---

### Post by Cupcake123 on 2011-11-30
Hi,

I downloaded Lubuntu 11.10. I have previously used Xubuntu, and one feature I liked there was an option to close windows when the window's menu button/icon is double-clicked. (Usually that button is at the top left of the window.) With that option enabled, a separate window close button is not needed.

It's not possible to enable that from the Lubuntu preferences. However you can apparently achieve it by editing the Openbox configuration file. I read this info at [http://melp.nl/2011/01/10-must-have-key-and-mouse-binding-configs-in-openbox/](http://melp.nl/2011/01/10-must-have-key-and-mouse-binding-configs-in-openbox/)

You add the text below to ~/.config/openbox/rc.xml

<context name="Icon">
  <mousebind action="DoubleClick" button="Left">
    <action name="Focus"/>
    <action name="Close"/>
  </mousebind>
  <!-- ... -->
</context>

---

