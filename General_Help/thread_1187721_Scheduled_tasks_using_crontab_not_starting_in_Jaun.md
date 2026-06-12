---
title: "Scheduled tasks using crontab not starting in Jaunty"
date: 2009-06-14
forum: General Help
---

### Post by vsen123 on 2009-06-14
Hi,
I scheduled azureus to start at 2:15 A.M. using Gnome Schedule.The task ran when manually executed but wouldn't start at the scheduled time.
I tried to schedule it using
                       
    ```
crontab -e
```

and added the following:

    ```
15 2 * * * DISPLAY=:0 vuze &
```

Note:I've setup vuze so that instead of the full path it will run on entering 'vuze' at the terminal.

Nothing works.Is cron broken in Jaunty?I have Ubuntu 9.04 with all updates installed.Athlon 64 2800+,1GB RAM,ASUS K8S-MX MB.

---

### Post by cmnorton on 2009-06-15
Suggest you try something very vanilla like an echo command running every minute. Just don't forget to take the entry out when you're done testing.

---

### Post by renkinjutsu on 2009-06-15
when using crontab, you'll have to use the full path to the executable

```
whereis vuze
``` in the terminal to find out where it is..
also the way i've seen it done with GUI apps is to use
```
export DISPLAY=:0 & /usr/bin/vuze
```

cron works perfectly fine in jaunty

---

### Post by jasonjob on 2009-08-23
Okay, I've just spent several hours trawling the net for a solution to this exact same problem (launching Azureus Vuze via cron at a certain time), and despite finding several different supposed solutions, I still can't do it...

cron works.  I know this, I can have it sending a hello message to me every minute.  Easy :)

The issue seems to be launching a java app from cron.  I cannot work out how to do it.  Here's what cron sends to me:

file:/usr/share/java/Azureus2.jar ; file:/usr/share/java/swt-gtk-3.4.jar ; file:
/home/jason/
java.lang.reflect.InvocationTargetException
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.
java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAcces
sorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at org.gudy.azureus2.ui.common.Main.directLaunch(Main.java:229)
    at org.gudy.azureus2.ui.common.Main.main(Main.java:132)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.
java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAcces
sorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:37)
    at java.lang.Thread.run(Thread.java:636)
Caused by: org.eclipse.swt.SWTError: No more handles [gtk_init_check() failed]
    at org.eclipse.swt.SWT.error(SWT.java:3803)
    at org.eclipse.swt.widgets.Display.createDisplay(Display.java:855)
    at org.eclipse.swt.widgets.Display.create(Display.java:843)
    at org.eclipse.swt.graphics.Device.<init>(Device.java:154)
    at org.eclipse.swt.widgets.Display.<init>(Display.java:471)
    at org.eclipse.swt.widgets.Display.<init>(Display.java:462)
    at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:9
0)
    at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThrea
d.java:67)
    at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.ja
va:110)
    at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:84)
    at org.gudy.azureus2.ui.swt.Main.main(Main.java:216)
    ... 12 more
Start fails:
com.aelitis.azureus.core.AzureusCoreException: Azureus core already instantiated
    at com.aelitis.azureus.core.impl.AzureusCoreImpl.create(AzureusCoreImpl.
java:99)
    at com.aelitis.azureus.core.AzureusCoreFactory.create(AzureusCoreFactory
.java:46)
    at org.gudy.azureus2.ui.common.Main.main(Main.java:160)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.
java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAcces
sorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:37)
    at java.lang.Thread.run(Thread.java:636)

The problem, so far as I can understand it, is that cron does not pass my user environment to java.  Following on from that, I have no idea how to pass such information.  The most common advice I can find is to use a shell script from cron, and have THAT launch Vuze.  No good.  Directed cron to the shell script that launches Vuze to start with, same old error.  Directed cron to a different script from the net:

#!/bin/sh
export PATH=$PATH:/opt/java/jre/bin
/usr/bin/azureus

and again, same thing.

All I can think of is that the people giving helpful advice don't actually use Vuze, and so are going on general principles, not actual experience (any number of them keep asking why the person asking for help is using Vuze, xyz app is soooo much better...).

So, can anyone, preferably someone who uses Vuze, tell me how to get cron to start it at 1 a.m. each morning?  (okay, the 1 a.m. bit each day I can do, it's the rest that's bothering me :)  I am not exactly a computer newbie, but I don't know a damned thing about java, and don't want to, either - I just want it to work.  Why Vuze?  Because it is what I used on my XP box (cue gasps - ex-Windows person), and I want to use what I am both familiar and happy with.  Yes, I am asking for someone to just dump a complete solution in my lap with no need for me to think.

Thanks.

---

