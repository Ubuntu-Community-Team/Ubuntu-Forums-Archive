---
title: "gnome-background-properties"
date: 2005-02-13
forum: Desktop Environments
---

### Post by uncle on 2005-02-13
Hi, 

I'm a really linux-njubi so be kind :)

I'm currently just trying to learn ubuntu. When I try to change the background image i get a fatal error and the gnome-background-properties wont even start. 

My error message is in swedish so I'm not sure it will help you but here it is:
"Programmet "gnome-background-properties" har oväntat avslutas."

I also get an error message then I try to change resolution something about that X-servern dosent support the XRandR-addon.

My error message is in swedish so I'm not sure it will help you but here it is:
"X-servern stöder inte XRandR-tillägget. Ändringar av displaystorleken under körning är inte möjligt."

Any one that can help me?

---

### Post by piedamaro on 2005-02-13
To get error in English, open a terminal and type:
LANG="C" gnome-background-properties

---

### Post by uncle on 2005-02-13
[QUOTE=piedamaro]To get error in English, open a terminal and type:
LANG="C" gnome-background-properties[/QUOTE]
 Ah, tnx. 

The error message is:
The Application "gnome-background-properties" has quit unexpectedly.

---

### Post by piedamaro on 2005-02-13
[QUOTE=uncle]Ah, tnx. 

The error message is:
The Application "gnome-background-properties" has quit unexpectedly.[/QUOTE]
 You should file a bug, but you need a backtrace for it. Look here: [http://www.ubuntulinux.org/support/documentation/howto/bugreporting](http://www.ubuntulinux.org/support/documentation/howto/bugreporting)

---

### Post by uncle on 2005-02-21
[QUOTE=piedamaro]You should file a bug, but you need a backtrace for it. Look here: [http://www.ubuntulinux.org/support/documentation/howto/bugreporting](http://www.ubuntulinux.org/support/documentation/howto/bugreporting)[/QUOTE]
 Hi, again. I found what causing this problem. It's when I try to install my ATI - graphic drivers. I used this Howto: [http://www.ubuntulinux.org/wiki/BinaryDriverHowto/view?searchterm=ati%20drivers](http://www.ubuntulinux.org/wiki/BinaryDriverHowto/view?searchterm=ati%20drivers)

Anyone got a clue?

---

