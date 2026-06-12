---
title: "Drivers for TouchPad in M5030"
date: 2010-11-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Dha...1 on 2010-11-30
I've tried gpointingdevice and gsynaptics. But none of them are able to make scrolling function work.
So I guess, scrolling is not supported by my laptop. Is that so?
And, I want to turn off the TouchPad while using external mouse. How to do that?

---

### Post by theremper on 2011-03-18
to disable touch pad put xinput --set-prop "PS/2 Generic Mouse" "Device Enabled" 0
in the terminal

to enable touch pad put xinput --set-prop "PS/2 Generic Mouse" "Device Enabled" 1
in the terminal

now how to get it to reconginze the touch pad

---

