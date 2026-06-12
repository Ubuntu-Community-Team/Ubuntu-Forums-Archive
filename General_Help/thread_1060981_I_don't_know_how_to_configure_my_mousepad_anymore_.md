---
title: "I don't know how to configure my mousepad anymore in 8.10"
date: 2009-02-05
forum: General Help
---

### Post by jonlemur on 2009-02-05
I just upgraded to 8.10 last night, and I can't figure out exactly how to configure my mousepad like I used to be able to in the xorg.conf file.  I did something to another laptop a couple of weeks ago with a HAL file (or something like that), but I can't find the howto that I used for that.  Basically what I want to do is mimic what I had in xorg.conf with ```
Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
Option "SHMConfig" "true"
Option "RightEdge" "5900"
Option "VertEdgeScroll" "true"
EndSection 
```
The most important part for me now is the RightEdge 5900 part to fix the scrolling area.  How can I do that?

Thanks

---

### Post by Vadi on 2009-02-05
Adding this to xorg.conf doesn't work anymore?

You can also use [GSynaptics]("http://gsynaptics.sourceforge.jp/") for configuring it. Click [here]("apt:gsynaptics") to install.

---

### Post by pnutzh4x0r on 2009-02-05
Once you enable SHMConfig, you can access the synaptics configuration using gsynaptics.  More information about how to do this can be found here:

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

For the particular setting, RightEdge, you will have to write a hal policy XML file as shown in:

[http://ubuntuforums.org/showthread.php?t=965046](http://ubuntuforums.org/showthread.php?t=965046)

Basically you want to create a file /etc/hal/fdi/policy/synaptics.fdi and put in something like:

```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>
   <merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>
   <merge key="input.x11_options.SHMConfig" type="string">true</merge>
   <merge key="input.x11_options.VertEdgeScroll" type="string">false</merge>
   <merge key="input.x11_options.HorizEdgeScroll" type="string">false</merge>
   <merge key="input.x11_options.TapButton1" type="string">1</merge>
   <merge key="input.x11_options.TapButton2" type="string">3</merge>
   <merge key="input.x11_options.TapButton3" type="string">2</merge>
   <merge key="input.x11_options.RightEdge" type="string">5900</merge>
  </match>
 </device>
</deviceinfo>

```

A more complete example of a synaptics policy file can be found in:
 
/usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi

Note, you don't to enable the SHMConfig separately from the driver settings.  The example above with both enable the SHMConfig AND set your RightEdge setting.  Once you create the policy file, you will need to reboot for the settings to take effect.

---

### Post by jonlemur on 2009-02-07
Thanks that did it.  I tried putting that stuff in xorg.conf, but it didn't work in there.  I had to add the synaptics.fdi file.

---

