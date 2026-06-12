---
title: "How to remove program"
date: 2009-05-14
forum: General Help
---

### Post by gingaz on 2009-05-14
Hello,

i had installation of NetBeans (6.0 i think) in Ubuntu 8.10 and after upgrade to 9.04 it became 6.5. Everything seemed OK until i tried to uninstall it.

I didn't find NetBeans in Synaptic - it showed that it's not on my PC, so i thought i'll overwrite it by installing new one and then could uninstall. Didn't help. 
After installation second icon of Netbeans appeared in Apps/Programming.. After uninstall the old one left.

I can't find NetBeans in filesystem anywhere.. Any ideas how to remove it manually (completely: from filesystem and menu)?

Thank you!

---

### Post by s.fox on 2009-05-14
Hi,

Is it not listed here? :
[B]
Applications ->  Add/Remove[/B]

Hope you find it!

-Ash R

---

### Post by Onizuka89 on 2009-05-14
did you try to find it by using the locate command?
like "locate netbeans" or something? if it's any file called netbeans on your HDD it should find it. but what you can do after that I don't know.

---

### Post by gingaz on 2009-05-14
Aaa, 'locate' helped. Found directory with netbeans install. Just ran uninstall.sh and it was fully removed.

Well, App->Add/Remove didn't show anything - just like Synaptic.

Just thinking, why i didn't use find function... :redface:

Thank you! :)

---

