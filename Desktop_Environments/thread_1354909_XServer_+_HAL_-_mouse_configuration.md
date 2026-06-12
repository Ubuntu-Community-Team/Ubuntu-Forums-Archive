---
title: "XServer + HAL - mouse configuration"
date: 2009-12-14
forum: Desktop Environments
---

### Post by Jethro_uk on 2009-12-14
regular followers of my strife with Ubuntu will know that I have encountered a bizarre issue with mouse focus ...

anyway, I am not a Linux guru, and have been struggling to find information on how the XServer handles mice. I have read that it now lets the HAL do the work. My question is how does this interact, and how can it be modified. What can I put in xorg.conf to modify or control mouse behaviour. How does HAL work, and can I modify how HAL deals with mice.

I am starting to think my problems are connected to the fact that the xorg.conf has only ever been built up by the install and upgrade programs, and they have left something as default, which is causing keyboard and/or mouse problems.

thanks guys

---

### Post by bryonak on 2009-12-14
xorg.conf is now only (mainly) used for video configuration.
The new configuration files for other (particularly input) devices are in /etc/hal/fdi/policy/
The files in this folder are called x.fdi, where x is a freely chosable descriptive name, and are formatted in XML. The settings options names are about the same you would use in xorg.conf.

For example, here's the /etc/hal/fdi/policy/appletouch.fdi for my laptops touchpad:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">

      <match key="info.product" contains="appletouch">
        <merge key="appledevice" type="bool">true</merge>
      </match>
      <match key="info.product" contains="bcm5974">
        <merge key="appledevice" type="bool">true</merge>
      </match>

      <match key="appledevice" bool="true">
	<merge key="input.x11_driver" type="string">synaptics</merge>
	<merge key="input.x11_options.SHMConfig" type="string">false</merge>
	<merge key="input.x11_options.LeftEdge" type="string">0</merge>
	<merge key="input.x11_options.RightEdge" type="string">1150</merge>
	<merge key="input.x11_options.TopEdge" type="string">0</merge>
	<merge key="input.x11_options.BottomEdge" type="string">800</merge>
	<merge key="input.x11_options.ClickFinger1" type="string">1</merge>
	<merge key="input.x11_options.ClickFinger2" type="string">3</merge>
	<merge key="input.x11_options.ClickFinger3" type="string">2</merge>
	<merge key="input.x11_options.FingerLow" type="string">15</merge>
	<merge key="input.x11_options.FingerHigh" type="string">25</merge>
	<merge key="input.x11_options.MaxTapTime" type="string">100</merge>
	<merge key="input.x11_options.MaxTapMove" type="string">10</merge>
	<merge key="input.x11_options.MaxDoubleTapTime" type="string">220</merge>
	<merge key="input.x11_options.MaxTripleTapTime" type="string">220</merge>
	<merge key="input.x11_options.LockedDrags" type="string">off</merge>
	<merge key="input.x11_options.MinSpeed" type="string">0.5</merge>
	<merge key="input.x11_options.MaxSpeed" type="string">2.5</merge>
	<merge key="input.x11_options.AccelFactor" type="string">0.15</merge>
	<merge key="input.x11_options.VertEdgeScroll" type="string">true</merge>
	<merge key="input.x11_options.HorizEdgeScroll" type="string">false</merge>
	<merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>
	<merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>
	<merge key="input.x11_options.VertScrollDelta" type="string">10</merge>
	<merge key="input.x11_options.HorizScrollDelta" type="string">15</merge>
	<merge key="input.x11_options.RTCornerButton" type="string">0</merge>
	<merge key="input.x11_options.RBCornerButton" type="string">0</merge>
	<merge key="input.x11_options.LBCornerButton" type="string">0</merge>
	<merge key="input.x11_options.LTCornerButton" type="string">0</merge>
	<merge key="input.x11_options.TapButton1" type="string">1</merge>
	<merge key="input.x11_options.TapButton2" type="string">3</merge>
	<merge key="input.x11_options.TapButton3" type="string">2</merge>
	<merge key="input.x11_options.PalmDetect" type="string">true</merge>
	<merge key="input.x11_options.PalmMinWidth" type="string">10</merge>
	<merge key="input.x11_options.PalmMinZ" type="string">200</merge>

	<merge key="input.x11_options.ClickTime" type="string">80</merge>
	<merge key="input.x11_options.FastTaps" type="string">false</merge>
	<merge key="input.x11_options.EdgeMotionMinZ" type="string">30</merge>
	<merge key="input.x11_options.EdgeMotionMaxZ" type="string">160</merge>
	<merge key="input.x11_options.EdgeMotionMinSpeed" type="string">1</merge>
	<merge key="input.x11_options.EdgeMotionMaxSpeed" type="string">40</merge>
	<merge key="input.x11_options.EdgeMotionUseAlways" type="string">off</merge>
	<merge key="input.x11_options.PressureMotionMinZ" type="string">10</merge>
	<merge key="input.x11_options.PressureMotionMaxZ" type="string">160</merge>
	<merge key="input.x11_options.PressureMotionMinFactor" type="string">1</merge>
	<merge key="input.x11_options.PressureMotionMaxFactor" type="string">1</merge>
	<merge key="input.x11_options.UpDownScrolling" type="string">true</merge>
	<merge key="input.x11_options.LeftRightScrolling" type="string">true</merge>
	<merge key="input.x11_options.UpDownRepeat" type="string">true</merge>
	<merge key="input.x11_options.LeftRightRepeat" type="string">false</merge>
	<merge key="input.x11_options.ScrollButtonRepeat" type="string">100</merge>
	<merge key="input.x11_options.EmulateMidButtonTime" type="string">75</merge>
	<merge key="input.x11_options.TouchpadOff" type="string">0</merge>
	<merge key="input.x11_options.GuestMouseOff" type="string">false</merge>
	<merge key="input.x11_options.CircularScrolling" type="string">off</merge>
	<merge key="input.x11_options.CircScrollDelta" type="string">0.1</merge>
	<merge key="input.x11_options.CircScrollTrigger" type="string">0</merge>
	<merge key="input.x11_options.CircularPad" type="string">false</merge>
	<merge key="input.x11_options.CoastingSpeed" type="string">0</merge>
	<merge key="input.x11_options.SingleTapTimeout" type="string">150</merge>
	<merge key="input.x11_options.TwoFingerButton1" type="string">2</merge>
	<merge key="input.x11_options.FingerPress" type="string">20</merge>
	<merge key="input.x11_options.TrackstickSpeed" type="string">0.0</merge>
      </match>
    </match>
  </device>
</deviceinfo>


```


As for mice... either wait for someone with more experience on this topic or try the search :)

---

### Post by Jethro_uk on 2009-12-15
brilliant, that's a start.

Unfortunately, my experience of searching for help with Ubuntu/Linux is variable ... and when it comes to the more obscure stuff (like this), I feel very alone ...

---

