---
title: "Synaptics touchpad settings location?"
date: 2008-11-18
forum: Desktop Environments
---

### Post by Nergar on 2008-11-18
Where can I find the current configuration of the synaptics touchpad in Intrepid? Xorg.conf is empty. 

I want to try out other distros but my touchpad never works as good as in Ubuntu so I want to copy this settings to other distros.

I'm using a Dell Inspiron 1525 (not the Ubuntu preloaded one). 

Also, out of curiosity, how does Ubuntu configures Xorg?

---

### Post by softtower on 2008-11-18
Something like this:
/usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi

---

### Post by damis648 on 2008-11-18
In intrepid xorg no longer configures the trackpad. I think the configuration files vary with model, mine is /etc/hal/fdi/policy/xps-touchpad.fdi and I have put in it the following:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.LeftEdge" type="string">120</merge>
   <merge key="input.x11_options.RightEdge" type="string">830</merge>
   <merge key="input.x11_options.TopEdge" type="string">120</merge>
   <merge key="input.x11_options.BottomEdge" type="string">650</merge>
   <merge key="input.x11_options.FingerLow" type="string">14</merge>
   <merge key="input.x11_options.FingerHigh" type="string">15</merge>
   <merge key="input.x11_options.MaxTapTime" type="string">180</merge>
   <merge key="input.x11_options.MaxTapMove" type="string">110</merge>
   <merge key="input.x11_options.ClickTime" type="string">0</merge>
   <merge key="input.x11_options.EmulateMidButtonTime" type="string">75</merge>
   <merge key="input.x11_options.VertScrollDelta" type="string">10</merge>
   <merge key="input.x11_options.HorizScrollDelta" type="string">0</merge>
   <merge key="input.x11_options.MinSpeed" type="string">0.45</merge>
   <merge key="input.x11_options.MaxSpeed" type="string">0.95</merge>
   <merge key="input.x11_options.AccelFactor" type="string">0.06</merge>
   <merge key="input.x11_options.EdgeMotionMinSpeed" type="string">200</merge>
   <merge key="input.x11_options.EdgeMotionMaxSpeed" type="string">200</merge>
   <merge key="input.x11_options.UpDownScrolling" type="string">1</merge>
   <merge key="input.x11_options.CircularScrolling" type="string">0</merge>
   <merge key="input.x11_options.SHMConfig" type="string">true</merge>
  </match>
 </device>
</deviceinfo>
```

(If you decide to modify yours, make sure you do a
```
sudo /etc/init.d/hal restart
```
and then a ctrl+alt+backpace)

---

### Post by Nergar on 2008-11-18
Hey Thanks a lot. I hope I can strip down those files and be able to use them in arch.

---

### Post by ee19921 on 2008-11-21
I need some help widening the scrolling area. I created a fdi file in /etc/hal/fdi/policy and restarted hal. Still I have the problem. Any ideas?

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.RightEdge" type="string">2530</merge>
  </match>
 </device>
</deviceinfo>

```

Thanks!

---

### Post by bobe84 on 2008-11-30
Hallo there,im also using 1525, i made my own config:

/usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi

```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="Synaptics TouchPad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
	<!-- Arbitrary options can be passed to the driver using 
	     the input.x11_options property since xorg-server-1.5. -->
	<!-- EXAMPLE:
	<merge key="input.x11_options.LeftEdge" type="string">120</merge>
	-->
      </match>
<match key="info.product" contains="AlpsPS/2 ALPS">
<merge key="input.x11_driver" type="string">synaptics</merge>
	<merge key="input.x11_options.SHMConfig" type="string">true</merge>
	<merge key="input.x11_options.LeftEdge" type="string">50</merge>
        <merge key="input.x11_options.RightEdge" type="string">900</merge>
        <merge key="input.x11_options.TopEdge" type="string">140</merge>
        <merge key="input.x11_options.BottomEdge" type="string">680</merge>
        <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
        <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
        <merge key="input.x11_options.ClickFinger3" type="string">2</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.VertEdgeScroll" type="string">1</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">0</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">0</merge>
        <merge key="input.x11_options.HorizScrollDelta" type="string">20</merge>
        <merge key="input.x11_options.VertScrollDelta" type="string">20</merge>
        <merge key="input.x11_options.PressureMotionMinZ" type="string">30</merge>
        <merge key="input.x11_options.PressureMotionMaxZ" type="string">160</merge>
        <merge key="input.x11_options.PressureMotionMinFactor" type="string">1</merge>
        <merge key="input.x11_options.PressureMotionMaxFactor" type="string">1</merge>
        <merge key="input.x11_options.FingerLow" type="string">18</merge>
        <merge key="input.x11_options.FingerHigh" type="string">23</merge>
        <merge key="input.x11_options.FingerPress" type="string">256</merge>
        <merge key="input.x11_options.PalmDetect" type="string">1</merge>
        <merge key="input.x11_options.PalmMinWidth" type="string">10</merge>
        <merge key="input.x11_options.PalmMinZ" type="string">200</merge>
        <merge key="input.x11_options.MinSpeed" type="string">1</merge>
        <merge key="input.x11_options.MaxSpeed" type="string">1.5</merge>
        <merge key="input.x11_options.AccelFactor" type="string">0.10</merge>
        <merge key="input.x11_options.MaxTapMove" type="string">110</merge>
        <merge key="input.x11_options.MaxTapTime" type="string">366</merge>
        <merge key="input.x11_options.MaxDoubleTapTime" type="string">180</merge>
        <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">2</merge>
        <merge key="input.x11_options.TapButton3" type="string">3</merge>
        <merge key="input.x11_options.RTCornerButton" type="string">2</merge>
        <merge key="input.x11_options.RBCornerButton" type="string">3</merge>
        <merge key="input.x11_options.LTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LBCornerButton" type="string">0</merge>
    </match>
    </match>
  </device>
</deviceinfo>


```

After you save file do system reboot :), cheers and put feedback was this useful :)

---

### Post by Pazin~ on 2008-12-05
> **bobe84 said:**
> Hallo there,im also using 1525, i made my own config:

/usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi

```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="Synaptics TouchPad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
	<!-- Arbitrary options can be passed to the driver using 
	     the input.x11_options property since xorg-server-1.5. -->
	<!-- EXAMPLE:
	<merge key="input.x11_options.LeftEdge" type="string">120</merge>
	-->
      </match>
<match key="info.product" contains="AlpsPS/2 ALPS">
<merge key="input.x11_driver" type="string">synaptics</merge>
	<merge key="input.x11_options.SHMConfig" type="string">true</merge>
	<merge key="input.x11_options.LeftEdge" type="string">50</merge>
        <merge key="input.x11_options.RightEdge" type="string">900</merge>
        <merge key="input.x11_options.TopEdge" type="string">140</merge>
        <merge key="input.x11_options.BottomEdge" type="string">680</merge>
        <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
        <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
        <merge key="input.x11_options.ClickFinger3" type="string">2</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.VertEdgeScroll" type="string">1</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">0</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">0</merge>
        <merge key="input.x11_options.HorizScrollDelta" type="string">20</merge>
        <merge key="input.x11_options.VertScrollDelta" type="string">20</merge>
        <merge key="input.x11_options.PressureMotionMinZ" type="string">30</merge>
        <merge key="input.x11_options.PressureMotionMaxZ" type="string">160</merge>
        <merge key="input.x11_options.PressureMotionMinFactor" type="string">1</merge>
        <merge key="input.x11_options.PressureMotionMaxFactor" type="string">1</merge>
        <merge key="input.x11_options.FingerLow" type="string">18</merge>
        <merge key="input.x11_options.FingerHigh" type="string">23</merge>
        <merge key="input.x11_options.FingerPress" type="string">256</merge>
        <merge key="input.x11_options.PalmDetect" type="string">1</merge>
        <merge key="input.x11_options.PalmMinWidth" type="string">10</merge>
        <merge key="input.x11_options.PalmMinZ" type="string">200</merge>
        <merge key="input.x11_options.MinSpeed" type="string">1</merge>
        <merge key="input.x11_options.MaxSpeed" type="string">1.5</merge>
        <merge key="input.x11_options.AccelFactor" type="string">0.10</merge>
        <merge key="input.x11_options.MaxTapMove" type="string">110</merge>
        <merge key="input.x11_options.MaxTapTime" type="string">366</merge>
        <merge key="input.x11_options.MaxDoubleTapTime" type="string">180</merge>
        <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">2</merge>
        <merge key="input.x11_options.TapButton3" type="string">3</merge>
        <merge key="input.x11_options.RTCornerButton" type="string">2</merge>
        <merge key="input.x11_options.RBCornerButton" type="string">3</merge>
        <merge key="input.x11_options.LTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LBCornerButton" type="string">0</merge>
    </match>
    </match>
  </device>
</deviceinfo>


```

After you save file do system reboot :), cheers and put feedback was this useful :)


Amazing!! Thank you very much! :D

---

### Post by AmyRose on 2009-01-04
> **bobe84 said:**
> Hallo there,im also using 1525, i made my own config:
Thanks a lot! My touchpad works a lot better now.

---

### Post by asl.pavel on 2009-01-11
actually better create new file /etc/hal/fid/policy/10-x11-input.fdi cuz if u edith /usr/share/hal ... it would be updated after u reinstall dirver !

---

