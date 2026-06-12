---
title: "Adobe Air app window resolution 640x480 problem"
date: 2010-03-17
forum: Desktop Environments
---

### Post by cernosko on 2010-03-17
Hi, we have a problem with our flex app runnig on Ubuntu. On Windows and OSX everything is ok, but Ubuntu prevents Adobe Air 1.5.3 NativeWidnows being larger than 640x480. We have already tried every options in xorg, but did not help.
Has anyone encountered this? Any solutions? 

Check the simple class attached.

thank you

---

### Post by cernosko on 2010-03-23
solution so easy!! change this two lines of code:

//monitorWindow.stage.stageWidth = bounds.width;
//monitorWindow.stage.stageHeight = bounds.height;

monitorWindow.width = bounds.width;
monitorWindow.height = bounds.height;

---

