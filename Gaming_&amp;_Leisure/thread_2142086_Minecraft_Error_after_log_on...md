---
title: "Minecraft Error after log on.."
date: 2013-05-04
forum: Gaming &amp; Leisure
---

### Post by ctabora on 2013-05-04
Hey I'm fairly new to linux but decided to try it on this old computer ive bben working on..and all i have to say is, I love it, so much freedom to the user, its amazing anyway ive installed minecraft using mc-nix and it installed perfectly no errors or anything but after log on it it starts up then crashes to the black sreen and ends with an error report.. Iv installed sun java 6 & 7 and the actual java runtime from oracle. does anyone have any ideas whats causing this?? my mc version is 1.5.2 and the os is ubuntu 12.04 generic...please and thank you in advance
                                                                           -Christian

---

### Post by OmgItsPixelated on 2013-05-08
Could you post the error report that you get? That would help to diagnose the problem.

---

### Post by Horbo on 2013-05-08
Really Sun Java?

MC doesn't like Oracle Java 7.  Install and run with Oracle Java 6.


[COLOR=#000000][FONT=Verdana]sudo add-apt-repository ppa:webupd8team/java
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]sudo apt-get update && sudo apt-get install oracle-java6-installer[/FONT][/COLOR]

---

### Post by nsync on 2013-05-10
wrong i think MC also supports java 7. i picked java7 instead of java6, but does it matter? i mean they are both java runtime and what could be the difference between the two? and for you ctabora i think you should update your ubuntu .. you might missed some opengl updates.. ur error is more likely to be described as also the windows version. you could also add more details so we could help you more with ur problem.

---

### Post by Horbo on 2013-05-11
> **nsync said:**
> wrong i think MC also supports java 7. 

You think?  But you also know I'm wrong?  Interesting.

I'm telling you (OP), that the black screen on startup is a classic result of using Oracle Java 7.  Install Oracle Java 6 and run with that instead.

---

### Post by nsync on 2013-05-11
> **Horbo said:**
> You think?  But you also know I'm wrong?  Interesting.

I'm telling you (OP), that the black screen on startup is a classic result of using Oracle Java 7.  Install Oracle Java 6 and run with that instead.

then how come i can still play minecraft using Java7?

---

