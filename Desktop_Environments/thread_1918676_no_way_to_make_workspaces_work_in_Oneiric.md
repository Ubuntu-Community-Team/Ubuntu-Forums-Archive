---
title: "no way to make workspaces work in Oneiric"
date: 2012-02-01
forum: Desktop Environments
---

### Post by Gingalone on 2012-02-01
I read many forums, howtos etc. tried so many different settings with CCSM and nothing happened... I can't understand why in the Unity launch bar there is a workspaces icon if it's totally useless: in noway I can put a window in any other workspace and if I click on 'workspaces' in the launchbar I get my desktop on top-left quarter of my monitor and that's all.
Is my laptop sick or is it me? Or Unity?
PS: I am using Unity 2d

---

### Post by Frogs Hair on 2012-02-01
When  the workspace icon selected an over view of four small windows appear . Double click the space you want to  use to bring it to the forefront . Open the application/s  needed in that space . Select the workspace icon again and bring the next workspace to the forefront adding applications to that space  . 

You should find that selecting the icons of the open applications allows movement between spaces as well as using the overview . You should also be able to drag applications from one space to the other .

---

### Post by Gingalone on 2012-02-02
> **Frogs Hair said:**
> When  the workspace icon selected an over view of four small windows appear . Double click the space you want to  use to bring it to the forefront . Open the application/s  needed in that space . Select the workspace icon again and bring the next workspace to the forefront adding applications to that space  . 
I get just one small window (top-left) and the other 3 quarter of screen are black, if I click in that black space nothing happens.
> You should find that selecting the icons of the open applications allows movement between spaces as well as using the overview . You should also be able to drag applications from one space to the other .

No, I can't.
Moreover I noticed that in my home Ubuntu11.10-Unity2D PC clicking the top bar of a window with the right button I get a menu with also "Move this window to another workspace" while in my work laptop in that menu I have only Minimize-Maximize-Move-Resize-Always on Top-Close.
SO I think something is missing here...

---

### Post by Frogs Hair on 2012-02-02
You could check out this tread . [http://askubuntu.com/questions/66701/how-configure-workspaces-on-unity-2d](http://askubuntu.com/questions/66701/how-configure-workspaces-on-unity-2d)

---

### Post by Gingalone on 2012-02-02
OK, solved with askubuntu (thanks Frogs Hair!):
```
gconftool-2 -s /apps/metacity/general/num_workspaces --type int 4
```
obviously I had just a single workspace "on"

---

