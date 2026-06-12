---
title: "Window greyed out for not responding"
date: 2014-03-26
forum: Desktop Environments
---

### Post by philchambers on 2014-03-26
I presume this is a Unity issue.  I have written a program using Qt and at some stage it takes a long time collecting the properties of lots of files over NFS.  During this time the window greys out.

Presumably Unity is sending a signal to the program and not getting a response.  I would be happy to get the program to respond if I knew what to to respond to.

Can anyone tell me what Unity does that makes it grey out the window?

---

### Post by grahammechanical on 2014-03-26
When an application window greys out like that it is because the application is busy. The greying out is Unity's way of showing the user that the OS has not frozen but the application is busy. It is instead of an hour glass or a rotating set of dots or a swirl.

When I set two large Libreoffice Writer documents to save one after the other then both windows grey out like that but the user interface is still active.

Regards.

---

### Post by philchambers on 2014-03-26
I'm not sure about your explanation.  I don't see how Unity can tell that the process is busy (other than checking its CPU usage).  As an experiment I inserted a sleep(20) in my program and that caused the window to grey out.  the CPU usage is zero while sleeping, so it can't be that and the program was clearly not busy in any real sense.

Surely, Unity must be 'probing' the program in  some way to see if it gets a response.

---

### Post by Frogs Hair on 2014-03-26
Try starting the application from he terminal if you haven;t already and if you have check for errors in the output . If it is opening and  becomes un-responsive later  it could be difficult to trouble-shoot because it's your own program. You might get more  helpful input in the programming sub forum.

---

### Post by philchambers on 2014-03-27
Thanks for the suggestions. When you run a program under Qt (while developing it), you get the teminal output displayed, so I know that no errors are being reported.

I have taken several of the Qt examples and placed 'sleep(20)' in them and after several seconds into the sleep, the windows grey out.  So, this a feature of running a program under Unity and I want to understand how Unity detects the 'busy' state so I can work around it.

In my own program I have a progress bar to show that the program is doing something useful, so I don't want the window to grey out.  How can my program respond to Unity so that it does not grey out my window?

---

### Post by Frogs Hair on 2014-03-27
The only thing that comes to mind is memory. Though the program may be small and simple it may require a lot of memory. Running the following command while the program is running/grayed out will display information about the top processes and if the program is using significant resources. ```
top
```

---

