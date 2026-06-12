---
title: "errors with simple-ccsm"
date: 2009-02-17
forum: Desktop Environments
---

### Post by hockman5 on 2009-02-17
I get the following errors when attempting to run simple-ccsm   
Traceback (most recent call last):
  File "/usr/bin/simple-ccsm", line 949, in <module>
    mainWin = MainWin(context, page)
  File "/usr/bin/simple-ccsm", line 867, in __init__
    self.Update()
  File "/usr/bin/simple-ccsm", line 873, in Update
    self.AnimationPage.Update()
  File "/usr/bin/simple-ccsm", line 514, in Update
    self.SetEnableAnimations()
  File "/usr/bin/simple-ccsm", line 492, in SetEnableAnimations
    plugin = self.Context.Plugins['animation']
KeyError: 'animation'

UBUNTU 8.04

---

