---
title: "Unaable to Open External HD's and Use Azureus"
date: 2008-03-05
forum: Desktop Environments
---

### Post by mav5150 on 2008-03-05
Hey Everyone, so I'm not a complete noob when it comes to Linux (I've played around with Linux on an old laptop for about a year, but just decided to get full core into Linux on my desktop) but I'm having some problems and can't seem to find a solution for them. The first problem I'm having is with Azureus, when I launch Azureus the splash screen comes up and then the installation screens opens for selecting a languages then Azureus just closes it's self. I tried opening it up in a terminal window to see what's going on and this is what happened : 
```
mavrik@mavrik-desktop:~$ azureus
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  Internal Error (53484152454432554E54494D450E4350500214), pid=4037, tid=3084430224
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0_03-b05 mixed mode, sharing)
# An error report file with more information is saved as hs_err_pid4037.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)

```

And I don't know how to fix this issue. It's obvious it has something to do with Java, and I know I have it installed because I just installed Netbeans and the installer was able to find a proper JDK on my system, plus when I go into Synaptic all of the sun-java6 packages have been installed. Any help here would be great. 

My other problem comes from my external Hard Drives. I have three externals, that are all filled with movies, cartoons, music, etc and after installing Ubuntu on my Desktop, the system recognizes them as USB drives but when I try to open them I get the "Unable to Mount the Volume 'X' ". I've looked around and most people have said that I should Force Mount the drives, but I'm scared I'll loose all my data if I do. So, again any help in this area would be great as well. 

Thanks.

---

### Post by mav5150 on 2008-03-12
Ok nevermind, I was able to fix the problems myself. Turned out when I was trying to force mount the drives I forgot to make a directory first for them to get forced mounted too. And with Azureus I just decided to use Ktorrent instead and it works perfectly fine.

---

