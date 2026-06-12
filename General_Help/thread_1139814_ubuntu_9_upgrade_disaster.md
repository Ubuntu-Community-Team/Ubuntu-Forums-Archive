---
title: "ubuntu 9 upgrade disaster"
date: 2009-04-27
forum: General Help
---

### Post by iggynig on 2009-04-27
Hi all,

I am new to Ubuntu and have only been using it for a couple of months.

Last night i went to upgrade from version 8 to version 9 and my laptop crashed before the installation was complete.

I have managed to get it up and running now but the resolution is completly out and it doesn't let me change it to one that fits the laptop screen.

I am using a Elonex web book which only has a 10" screen and the resolution makes the display huge. I have tried adjusting the display preferences but none of the options make any difference.

Please help

Thanks

Iggynig

---

### Post by zvacet on 2009-04-27
Did you upgrade it completely or is something missing form Jaunty?Go to the system>admin>software sources and uncheck all third party repos.After that go to the terminal and type 

```
sudo apt-get update && sudo apt-get dist-upgrade
```

When you are sure that you have complete Jaunty installed then you can go and try to fix things if needed.

---

### Post by iggynig on 2009-04-27
> **zvacet said:**
> Did you upgrade it completely or is something missing form Jaunty?Go to the system>admin>software sources and uncheck all third party repos.After that go to the terminal and type 

```
sudo apt-get update && sudo apt-get dist-upgrade
```

When you are sure that you have complete Jaunty installed then you can go and try to fix things if needed.
Hi, cheers for the idea

unfortunately it didn't work, i went in to third party software but nothing was checked on the list. I then ran the code and this is the error i got

Processing triggers for doc-base ...
Processing 1 changed doc-base file(s)...
Registering documents with scrollkeeper...
Setting up libchipcard-tools (4.1.3-2ubuntu1) ...
Starting libchipcard daemon: invoke-rc.d: initscript libchipcard-tools, action "start" failed.
dpkg: error processing libchipcard-tools (--configure):
 subprocess post-installation script returned error exit status 1
Setting up acpid (1.0.6-9ubuntu4.9.04.2) ...
 * Stopping Hardware abstraction layer hald                              [ OK ] 
 * Loading ACPI modules...                                               [ OK ] 
 * Starting ACPI services...                                             [ OK ] 
 * Starting Hardware abstraction layer hald                              [ OK ] 

Setting up libfreetype6 (2.3.9-4ubuntu0.1) ...

Setting up libfreetype6-dev (2.3.9-4ubuntu0.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 libchipcard-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
iggynig@ubuntu:~$

---

### Post by zvacet on 2009-04-27
```
sudo dpkg --configure -a
```

---

### Post by Didius Falco on 2009-05-04
If the above doesn't do the trick, try this:

[http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html](http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html)

---

### Post by KJH on 2009-05-04
See my response here [http://ubuntuforums.org/showthread.php?p=7212041](http://ubuntuforums.org/showthread.php?p=7212041) - hope it works for you.

---

