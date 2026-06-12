---
title: "Key Bindings Not Working"
date: 2012-10-26
forum: Desktop Environments
---

### Post by OnlyDeanCanLayEggs on 2012-10-26
I've been trying to set up a few custom keybindings to launch my most-used applications.  I run Lubuntu, and therefore and trying to do it by editing the OpenBox configuration file.  So, I nagivate to /home/user/.config/openbox and then open the rc.xml file with Leafpad.  I have tried both of these additions within the  "keybind" tag, and neither has worked: 

```

<keybind key="W-b"><action name="Execute"><command>firefox</command>

</action></keybind>
   <keybind key="W-w">
      <action name="Execute">
            <startupnotify>
                  <enabled>true</enabled>
                  <name>Web Browser</name>
           </startupnotify>
    <command>x-www-browser</command>

```Can anyone clue me in as to what is wrong? Is there another program that may be interfering?  I should note that all pre-set keybindings in the rc.xml file do work correctly.

---

