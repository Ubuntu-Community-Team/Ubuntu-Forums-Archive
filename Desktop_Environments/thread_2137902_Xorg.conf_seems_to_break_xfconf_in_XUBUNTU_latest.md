---
title: "Xorg.conf seems to break xfconf in XUBUNTU latest"
date: 2013-04-22
forum: Desktop Environments
---

### Post by gkatsanos on 2013-04-22
I had this problem two times; when I fiddle with Nvidia-settings and save to xorg.conf or edit manually the xorg.conf and have syntaxes, there seems to be a change inside [COLOR=#000000].config/xfce4 , specifically in [/COLOR][COLOR=#000000]~/xfce4-back/xfconf/xfce-perchannel-xml/displays.xml . I also filed a bug in the bugzilla XFCE: [/COLOR][https://bugzilla.xfce.org/show_bug.cgi?id=10023](https://bugzilla.xfce.org/show_bug.cgi?id=10023)

Basically deleting all xfconf stuff fixes the problem; but ends up losing alll shortcuts,icons,styles,panels.. 

I am able to save my shortcuts but not my panels.. It seems displays.xml is linked to them. I paste displays.xml below , in case you see some error/syntax error?

```
<?xml version="1.0" encoding="UTF-8"?>


<channel name="displays" version="1.0">
  <property name="Default" type="empty">
    <property name="LVDS-0" type="string" value="Laptop">
      <property name="Active" type="bool" value="true"/>
      <property name="Resolution" type="string" value="1366x768"/>
      <property name="RefreshRate" type="double" value="59.940060"/>
      <property name="Rotation" type="int" value="0"/>
      <property name="Reflection" type="string" value="0"/>
      <property name="Primary" type="bool" value="false"/>
      <property name="Position" type="empty">
        <property name="X" type="int" value="0"/>
        <property name="Y" type="int" value="0"/>
      </property>
    </property>
    <property name="HDMI-0" type="string" value="SONY">
      <property name="Active" type="bool" value="true"/>
      <property name="Resolution" type="string" value="1920x1080"/>
      <property name="RefreshRate" type="double" value="60.000000"/>
      <property name="Rotation" type="int" value="0"/>
      <property name="Reflection" type="string" value="0"/>
      <property name="Primary" type="bool" value="false"/>
      <property name="Position" type="empty">
        <property name="X" type="int" value="1366"/>
        <property name="Y" type="int" value="0"/>
      </property>
    </property>
  </property>
</channel>

```

---

