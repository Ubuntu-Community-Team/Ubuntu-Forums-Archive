---
title: "Window title bars disappeared"
date: 2011-04-20
forum: Desktop Environments
---

### Post by chickeng on 2011-04-20
I have just upgraded from 10.10 to 11.04

Using gnome I can no longer see the title bars of any windows or the minimise, restore and close buttons.

Example is shown here:
[http://i.imgur.com/rqrkr.png](http://i.imgur.com/rqrkr.png)


Can anybody help me with this?

Thanks,

---

### Post by karmila on 2011-04-20
Do you have compiz activated? If so, try:
*compiz --replace*
If don't, try:
*metacity --replace*

---

### Post by Copper Bezel on 2011-04-20
I'm thinking this is a problem between 10.10 and 11.04's implementations of Compiz. We've been seeing a lot of these, some more serious than others. 

To the OP, try switching to Metacity as your Window Manager ( metacity --replace ) and reinstalling Compiz from the Software Center or Synaptic. Notice that the Compiz settings manager is now called compizconfig-settings-manager, and there may be some other package name chnages.

---

