---
title: "Touchpad problems when kde not running"
date: 2009-09-22
forum: Desktop Environments
---

### Post by rosspoko on 2009-09-22
Hi

I have a HP tx1220 laptop with Kubuntu Jaunty.  Recently, I decided to install LXDE in addition to KDE so that I could go back and forth between memory-hogging eye-candy and just the necessities whenever I got tired of one or the other.  I got in the habit of running KDE when my computer is docked, using an external mouse and keyboard, and running LXDE when the computer was unplugged using the built in touchpad and keyboard.

While using the touchpad (in LXDE), I discovered that while all of its functionality still worked, it performed quite badly.  whenever I would attempt to move the cursor, it would take a half second or so to respond, but then once moving would be completely responsive.  Also, it was near impossible to use tap-to-click, and even using the actual left-click button was rather unresponsive, often taking several tries to click anything.  

After looking into the problem, I am fairly sure that it only occurs while I am running LXDE and while I am still at the kdm login screen.  Once I go into KDE it seems to be fine.  

While looking for answers, I have found that there are no settings for my touchpad, or any input device for that matter, in my xorg.conf file. In an attempt to fix this I modified my /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi file so that it looks like this: ```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <!-- Arbitrary options can be passed to the driver using
             the input.x11_options property since xorg-server-1.5. -->
        <!-- EXAMPLE:
        <merge key="input.x11_options.LeftEdge" type="string">120</merge>
        -->
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.SHMConfig" type="string">On</merge>
        <merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">90</m$
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</mer$
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</me$
        <merge key="input.x11_options.TapButton1" type="string">1</merge>
    </match>
  </device>
</deviceinfo>

```

I might have no idea what I'm talking about, but if I had to guess what the problem is, I would guess that KDE is talking to the touchpad through HAL, using the configuration that I just posted.  Everything else, however, is not using HAL to talk to the touchpad and is just using a default driver built into X or the kernel.  Again though, I barely even know what HAL does so I could definitely be wrong about that. 

Thanks for any help

EDIT: I have just noticed that the text I copied for that file has some lines truncated, but you get the idea.

---

### Post by rosspoko on 2009-09-30
After upgrading to Karmic, the problem seems to be fixed.  I still do not know what the issue was to begin with though

---

