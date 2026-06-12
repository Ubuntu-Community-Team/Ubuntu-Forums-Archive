---
title: "Slection of two os?"
date: 2011-01-14
forum: Desktop Environments
---

### Post by adeee on 2011-01-14
Dear fellows, Friends, and Sir's i have questions that is difficult to
explain because of my English but i try to make it easy and understandable..[IMG]http://www.linuxforums.org/forum/images/smilies/rolleyes.gif[/IMG]
 
so there it is.
 
operating system: Ubuntu(wubi)
hard 80 gb divide into 4 partition each 20gb.[IMG]http://www.linuxforums.org/forum/images/smilies/eek.gif[/IMG]
 
 [SIZE=2][COLOR=Sienna]1.[/COLOR][/SIZE]Can i use ubuntu as a primary os instead of windows xp?
 
 [SIZE=2][COLOR=Sienna]2.[/COLOR][/SIZE]i use ubuntu in wubi and really enjoys it. i install several softwares but there is
a problem.wubi have limited space. only 10gb i gave.and you now updates or other downloading
requires more space.[IMG]http://www.linuxforums.org/forum/images/smilies/icon_confused.gif[/IMG]
i install lvpm to increase space but i dont try to use it.
so instead of increasing space of wubi i decided to use ubuntu as a os
in which i use windows as a application. like wubi in windows.
 
so there is another question arises.
 
 [SIZE=2][COLOR=Sienna]3.[/COLOR][/SIZE] Can i use two operating system at time.?
means
no one operating system depend other one each have independent and dependent right.
How dependent and Independent? i tell you.
but firstly i tell you in this case i want to give 40 gb to window(two drives) and remaining to ubuntu.
 [COLOR=DarkOrchid]Independent cases:[/COLOR]
->in case of corrupting an window drive! no effect on ubuntu applied. and vise versa.
->normally boot. no booting problem occurred.
->if any virus threat appear in any os then other not effected.totally separate.
 
 [COLOR=Blue]Dependent cases:[/COLOR]
i can access my window drives in ubuntu.
not ubuntu in windows.because ntfs dont support ext3.
 
so suggest me your opinion. what you suggest case 1,2 or 3?
and your how can i apply your suggested case.?[IMG]http://www.linuxforums.org/forum/images/smilies/confused.gif[/IMG]
whats your recommendation?
what you prefer? 
what is suitable for me?
 
 
 [COLOR=Red]Remember[/COLOR]:i dont want lose my data in ubuntu.. in third case i just transfer ubuntu
from window to seprate with require space.

---

### Post by celldweller1591 on 2011-01-14
1) Primary OS in terms of boot preferences or Disk usage ? 
If u are asking about boot preferences, then its easy, you just need to edit the boot.ini file and you are good to go. But if you are asking about disk usage, then sry, cant help. 
2) Well you are limited of / space. You need to install Ubuntu on a separate partition. See details [here]("www.linoob.com/2009/04/landing-on-planet-ubuntu/"). You can then install windows inside Ubuntu using Virtual Box or KVM but that would be a virtual install not a dedicated one like Wubi does in case of Ubuntu. Actually Wubi's reverse isnt available. 
3) Yes & No. Yes with the help of virtualization and no because you can boot into 1 operating system at a time. 
To see What is virtual box and how u can use it to run 2 os at a time, see [this page]("www.linoob.com/2010/12/virtualbox-4-0-for-ubuntu-10-10/"), & for KVM, [this page]("www.linoob.com/2009/10/kvm-kernel-virtual-machine").

Windows viruses cant do anything in Ubuntu coz its different so no Virus problem at all.

---

