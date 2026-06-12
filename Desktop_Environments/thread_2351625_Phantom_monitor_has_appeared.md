---
title: "Phantom monitor has appeared"
date: 2017-02-05
forum: Desktop Environments
---

### Post by don-j-cooper on 2017-02-05
My PC runs 12.04 and the proprietary AMD driver. Been working happily without any changes bar Ubuntu updates for years with a very occasional glitch that sometimes it would boot up in the wrong resolution. A reboot always fixed that until last week when it stayed stuck. System settings->Screen Display offered me no better resolution until I noticed the 'Mirror displays' box was ticked, removing that allowed me to to reset to the 1920x1080 native to my monitor but it didn't delete the 'Unknown' monitor that had appeared alongside it. Although the machine now basically works there's still some odd behaviour - the login screen is in a lower resolution, preview windows when switching workspace are doubled up and squashed and the like. Nothing critical but I did some digging and ended up looking at monitors.xml, pasted below. A second configuration section has appeared that includes a fictitious CRT display with the lower 1400x1050 resolution I'd been getting. Deleting the new config and reverting to what presumably was the original seemed an obvious move but doesn't work, do that and at next boot it's decided that I've now got mirrored display once more and I'm stuck in low res until I remove it. Any way to get rid of this imaginary display?

```
<monitors version="1">
  <configuration>
      <clone>no</clone>
      <output name="DFP1">
      </output>
      <output name="DFP2">
          <vendor>ACR</vendor>
          <product>0x03fa</product>
          <serial>0x43404590</serial>
          <width>1920</width>
          <height>1080</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>yes</primary>
      </output>
      <output name="DFP3">
      </output>
      <output name="DFP4">
      </output>
      <output name="CRT1">
      </output>
      <output name="CRT2">
      </output>
  </configuration>
  <configuration>
      <clone>no</clone>
      <output name="DFP1">
      </output>
      <output name="DFP2">
          <vendor>ACR</vendor>
          <product>0x03fa</product>
          <serial>0x43404590</serial>
          <width>1920</width>
          <height>1080</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>yes</primary>
      </output>
      <output name="DFP3">
      </output>
      <output name="DFP4">
      </output>
      <output name="CRT1">
          <vendor>???</vendor>
          <product>0x0000</product>
          <serial>0x00000000</serial>
          <width>1400</width>
          <height>1050</height>
          <rate>60</rate>
          <x>1920</x>
          <y>30</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
      <output name="CRT2">
      </output>
  </configuration>
</monitors>
```

---

