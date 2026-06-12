---
title: "Workspaces switcher - Gutsy"
date: 2007-10-24
forum: Desktop Effects &amp; Customization
---

### Post by onuca on 2007-10-24
I have recently upgraded to Gutsy and I am delighted with Compiz Fusion, however...
The worksapce switcher on Gnome panel does not work together with compiz desktops - ok I have same amount of workspaces on compiz and gnome workspace switchers but if I use the one on Gnome panel all windows just dissapear! It does not switch the desktops at all!!! Any ideas???

---

### Post by 505 on 2007-10-24
Another reason why [the bug]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/153322") I filled should be solved. It's a mess now.

To fix it, first unload compiz (command 'metacity --replace'), then set the number of desktops to 1 in the switcher, now load compiz (command 'compiz --replace'). Now the switcher should switch with a nice animation.

---

### Post by onuca on 2007-10-29
Thanks! I am just about to give it a try!

---

### Post by new2*buntu on 2007-10-29
I have the same problem (except with Beryl in Linux Mint Celena) and your fix didn't fix it. When I switch workspaces with the workspace switcher my windows all burn down.

---

### Post by PCZahra on 2007-10-30
ditto new2*buntu

---

### Post by Forlong on 2007-10-30
It's probably due to wrong configuration.

Do _not_ increase the number of desktops. Compiz (and Beryl) uses viewports.
So if you want to use four workspaces, only increase the "Horizontal Virtual Size".

---

### Post by aswinms on 2007-11-02
They work perfectly when the Desktop Effects are disabled, as soon as you enable the option.. Workspaces are very flaky, sometimes they work and sometimes they don't.. Anybody has a better solution than to disable the Desktop Effects?

---

### Post by burzum on 2007-11-09
I have the same problem but no solution. :(

---

### Post by deadahead on 2007-11-27
I am very new to ubuntu gutsy and have a problem where when I try and switch to my next workspace I just get the background with no applications to choose from. Any ideas?

---

### Post by Enginirical on 2007-11-29
Hey I have just been having the same issues, but fixed it using this thread so I don't understand why you are having issues.

If I clicked on viewport/desktop selection the menu&#347; would disappear. Furthermore all the windows tabs were annoyingly on all desktops regardless of where I opened them. 

As someone mentioned earlier there is a difference between desktops and viewports, as far as I understand, (Im a noob too) the result is the same but one is done through gnome-metacity and one is done through compiz fusion. 

To fix your problem open up compiz theme manager (system>administration>appearence-->visual effects>preferences) 

select General options then desktop size. Then reduce number of desktops to 1 and vertical virtual size to 1. 

The Virtual horizontal size is the number compiz viewports, If you select you desired number of viewport (desktops) here i.e. 4 for a cube then it will work as you expect it too without menus disappearing.

I hope this helps...good luck!

---

