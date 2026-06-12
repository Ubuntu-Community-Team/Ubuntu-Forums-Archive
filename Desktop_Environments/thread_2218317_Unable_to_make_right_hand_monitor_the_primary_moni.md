---
title: "Unable to make right hand monitor the primary monitor after reboot"
date: 2014-04-20
forum: Desktop Environments
---

### Post by earthwormgym on 2014-04-20
I am using ubuntu 14.04. I am able to make my right hand monitor the primary using the "Screen Display" system setting tool but after reboot this monitor is forced to be on the left of the configuration.

I have tried various things with the xorg.conf but this does not seem to be what is making this configuration, the xorg.conf seems to be ignored. It seems to be the ~/.config/monitor.xml that dictates this, which I have pasted below

```
<monitors version="1">
  <configuration>
      <clone>no</clone>
      <output name="DVI-I-0">
      </output>
      <output name="VGA-0">
      </output>
      <output name="DVI-I-1">
          <vendor>VSC</vendor>
          <product>0x0f1c</product>
          <serial>0x01010101</serial>
          <width>1280</width>
          <height>1024</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
      <output name="HDMI-0">
          <vendor>IVM</vendor>
          <product>0x6107</product>
          <serial>0x01010101</serial>
          <width>1920</width>
          <height>1080</height>
          <rate>60</rate>
          <x>1280</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>yes</primary>
      </output>
      <output name="DVI-I-2">
      </output>
  </configuration>
</monitors>
```

This configuration reads correctly in that HDMI-0, which is the monitor on the right, is +1280 in the x direction so is on the right and is set as primary. However after reboot the effect is as if this monitor is at 0,0 and the other has a possitive x offset.

Has any one else got this issue? Should I raise this as a bug?

Thanks

---

