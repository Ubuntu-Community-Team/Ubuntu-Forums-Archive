---
title: "HELP - Kontact problems - lost files"
date: 2006-06-02
forum: Desktop Environments
---

### Post by silvagroup on 2006-06-02
When I run Kontact my contacts list is all of a sudden empty (has been fine for over 2 years) lost all 450 contacts and I get this error when closing contacts > The resource '/home/carlos/.kde/share/apps/kabc/std.vcf' is locked by application ''. after clicking on OK I get > Unable to get access for saving the address book resource Then > The resource '/home/carlos/.kde/share/apps/kabc/std.vcf' is locked by application ''. and then> Unable to save to resource 'resource'. It is locked. Then finally everything closes.
What's happening and where are my contacts. :o ???

When I started form terminal and then closed Kontact here's what I got:
> kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
QLayout::addChildLayout: layout already has a parent
carlos@Silvagroup:~$ WeaverThreadLogger: thread (ID: 1) suspended.
WeaverThreadLogger: thread (ID: 2) suspended.
WeaverThreadLogger: thread (ID: 3) suspended.
WeaverThreadLogger: thread (ID: 4) suspended.
Weaver dtor: destroying inventory.
WeaverThreadLogger: thread (ID: 1) destroyed.
WeaverThreadLogger: thread (ID: 2) destroyed.
WeaverThreadLogger: thread (ID: 3) destroyed.
WeaverThreadLogger: thread (ID: 4) destroyed.
Weaver dtor: done

I posted on the Kubuntu forums with no success any one here have an answer or at least a place to start - HELP

---

### Post by silvagroup on 2006-06-02
Hurray :D problem resolved. :D 
WOW, this one seems to have stumped everyone. ](*,) 
If you have or have had this problem here is the solution:
1. go to your ~/.kde/share/apps/kabc/lock then remove all files (these are old lock files)
2. Then go to ~/.kde/share/apps/kabc/ click on the latest creation date not .vfc_# (these are backup files) click on it kaddressbook will open then select import all and that's it you know have your address book back  :-D 
Thanks to KDE forum and KDE bug forum for trail to solution. :KS :KS

---

