---
title: "Java UI fields stop taking keyboard input (feisty+jre6)"
date: 2007-06-15
forum: Desktop Environments
---

### Post by harbdog on 2007-06-15
I know I have seen a post on this before somewhere but couldn't find it in these forums

it seems almost random at times where the text fields in a java swing application no longer response to keyboard input, but can still be pasted into using middle click.  I don't believe i have seen the issue in Netbeans, but in any other application such as the one i'm developing.  Is there some bug open somewhere already with a quick fix, or some piece of code I can throw in to make it behave properly at all times.

the issue occurs with both beryl and metacity, and is only solved generally by restarting the application and crossing fingers to hope it doesn't happen again too soon.

---

### Post by vtripolitakis on 2007-06-16
Check this for a temporary solution

[http://ubuntuforums.org/showthread.php?t=421571&highlight=java+keyboard](http://ubuntuforums.org/showthread.php?t=421571&highlight=java+keyboard)

Unfortunately it is a known bug. I assume that it will be fixed in upcoming jre versions...
[http://www.netbeans.org/issues/show_bug.cgi?id=94316](http://www.netbeans.org/issues/show_bug.cgi?id=94316)

---

