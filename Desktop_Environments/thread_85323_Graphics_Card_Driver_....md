---
title: "Graphics Card Driver ..."
date: 2005-11-02
forum: Desktop Environments
---

### Post by DrQuincy on 2005-11-02
What's the deal with graphics card drivers on Linux?

I have a Geforce 4 Ti4200, Abit OTES.  Is there anything I can download that will increase performance?

---

### Post by KingBahamut on 2005-11-02
sudo apt-get install nvidia-glx nvidia-settings 
sudo nvidia-glx-config enable 

Restart X 

Login

glxgears -info  in a terminal.

---

### Post by DrQuincy on 2005-11-02
Thanks :)

I can't try it yet as I'm at work: does it make much difference to the performance?

---

