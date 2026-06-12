---
title: "EDIT Workspaces in Ubuntu 11.04"
date: 2011-04-29
forum: Desktop Environments
---

### Post by Alexsupertramp on 2011-04-29
Hi.
i would like to know if i can change the workspace switcher in ubuntu 11.04 to have only i horizontal row..without a second tier so that i can change my workspaces just my scroll action using compizconfig settings manager.

---

### Post by 3Miro on 2011-04-29
Just go ahead and use CCSM. I use 4 workspaces in a row and I switch between them with mouse-scroll. Works just fine with Unity.

---

### Post by SonicSteve on 2011-04-29
In case your having trouble the settings to change are in 

General settings, desktop size

then change vertical virtual size to 1 from the default 2

Then change horizontal size to the # of workspaces you want.

Waala!

---

### Post by Alexsupertramp on 2011-04-29
> **SonicSteve said:**
> In case your having trouble the settings to change are in 

General settings, desktop size

then change vertical virtual size to 1 from the default 2

Then change horizontal size to the # of workspaces you want.

Waala!

yeah i tried that and worked...thanks for the reply,but when i use CCSM the panel and the launcher display areas get hazy and the image breaks up into colors.
this gets fixed by logging out and then logging in again.
[http://ubuntuforums.org/showthread.php?t=1743604]("http://ubuntuforums.org/showthread.php?t=1743604")
this apart if you remember the simple CCSM there was an option to switch workspaces without any animation i.e. without ring switcher or cube or whatever [don't remember much].i just want the open windows to slide away instead of the whole workspace.
appreciate the help.:D

[[img]http://s3.postimage.org/1tu6c4j2c/Screenshot.jpg[/img]](http://postimage.org/image/1tu6c4j2c/)

---

### Post by Copper Bezel on 2011-04-29
It's not a matter of changing the transition, but how some specific types of windows are treated under it. 

The smooth slide that only affects "normal" windows is a behavior of the Compiz Desktop Wall. Under the Viewport Switching tab, the text box for non-sliding windows should look like 

```
type=Dock | type=Desktop | state=Sticky
```

---

### Post by Alexsupertramp on 2011-04-30
> **Copper Bezel said:**
> It's not a matter of changing the transition, but how some specific types of windows are treated under it. 

The smooth slide that only affects "normal" windows is a behavior of the Compiz Desktop Wall. Under the Viewport Switching tab, the text box for non-sliding windows should look like 

```
type=Dock | type=Desktop | state=Sticky
```

thanks for this amazing quick reply.gratitude.:KS

---

### Post by roboa1983 on 2011-05-04
I had a similar question, wanting to extend to 2x3 spaces. 
Installed CCSM and followed the steps from SonicSteve.
Works great!

---

