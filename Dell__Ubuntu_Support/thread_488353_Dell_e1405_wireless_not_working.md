---
title: "Dell e1405 wireless not working"
date: 2007-06-30
forum: Dell  Ubuntu Support
---

### Post by ScorchKnights on 2007-06-30
I am sort of new at using Linux so here goes.
I have installed the newest ndiswrapper and the correct driver for my laptop. However, it seems that even though it says w29n51.inf is installed, my wireless still does not work. It is not giving me a wireless interface. 
Thanks ^_^

---

### Post by tolremeno on 2007-06-30
I have that computer, too. I've read numerous people getting wireless to work on it using ndiswrapper, but it didn't work for me.

I found [this page]("http://ubuntuforums.org/showthread.php?t=405990") to be useful. You can try the first method (ndiswrapper made easy, I think), but I had better luck with the second method. 

If you do get it to work the second way, you'll want to 
```
sudo gedit /etc/modules
```
and add bcm43xx to the end of the list (and take ndiswrapper off if it didn't work for you).

---

### Post by ScorchKnights on 2007-07-02
It works now, it turns out I had installed the wrong driver.
Thanks

---

