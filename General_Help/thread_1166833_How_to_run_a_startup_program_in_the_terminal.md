---
title: "How to run a startup program in the terminal"
date: 2009-05-22
forum: General Help
---

### Post by Julian David Pitt on 2009-05-22
I run the folding at home client on an old IBM T23 laptop and am having some issues with it. I have set the program to run in the startup under System-Preferences-Startup-Applications, with the command /home/julian/Folding/.fah6. Is is listed in System Monitor as running but I would like to see it running in a terminal so that I can see how far it has got and also read any error messages. Could somebody please tell me how to do this, thanks a lot.

---

### Post by Idefix82 on 2009-05-22
Instead of running the command itself on start up, you could have a terminal run on start up which would execute the command. The start up command would have to be
```
gnome-terminal -x /home/julian/Folding/.fah6
```

---

### Post by Julian David Pitt on 2009-05-22
> gnome-terminal -x /home/julian/Folding/.fah6
Excellent and thanks a lot I will give that a try when I get home.

---

### Post by Julian David Pitt on 2009-05-24
thanks a lot it worked very well, but one more question, how do I get the terminal to start minimised?

---

### Post by Idefix82 on 2009-05-24
You are welcome. Not sure about the second question, I will look into it. Maybe it's one of the parameters that can be passed to the window manager.

---

