---
title: "Help Debian Menu in Gnome"
date: 2007-05-27
forum: Desktop Environments
---

### Post by Trippen Out on 2007-05-27
okay so im trying to enable the debain menu under the applications drop down.. i have looked around at differnt guides .. i have installed the 2 packages that are said to be needed for this.. the menu .. and menu xdg or something like that... still it does not show up... under the menu editor it is no possible to put a checkmark on the debain menu but it will not stay there..everytime i open it back up its unchecked.. please how can i fix this.. is something overriding my settings... im at a loss here


using the 32bit fawn

---

### Post by spin2cool on 2007-05-27
The automatix installer comes with an option to enable the debian menu.  [http://getautomatix.com/](http://getautomatix.com/)

---

### Post by RedSquirrel on 2007-05-27
> **Trippen Out said:**
> okay so im trying to enable the debain menu under the applications drop down.. i have looked around at differnt guides .. i have installed the 2 packages that are said to be needed for this.. the menu .. and menu xdg or something like that... still it does not show up... under the menu editor it is no possible to put a checkmark on the debain menu but it will not stay there..everytime i open it back up its unchecked.. please how can i fix this.. is something overriding my settings... im at a loss here


using the 32bit fawn

Try running (in a terminal):

```
sudo update-menus
```

---

### Post by Trippen Out on 2007-05-27
it didnt work automatix either.. thanks tho.. but the sudo update-menus worked like a charm that was the command i was looking for.. thanks..

---

