---
title: "OpenOffice Graphic Glitches"
date: 2006-06-01
forum: Desktop Environments
---

### Post by daverab on 2006-06-01
Ok, I've been toying with DD 6.06 since about Flight 6. I thought this issue would have been resolved, but it hasn't.

I open OO Writer, Spreadsheet, Presentation, etc.

Everything looks ok, then I mouseover toolbar icons. They disapeer. I mouse over menu items, they disapeer. It seems to be some sort of refresh problem.

I had toyed with XGL in the past, but that's deactivated.

I'm not too sure if it is an issue with my Nvidia driver, Java or something like GTK.

Anyone have suggestions on at least what I should do to narrow down what the issue could be?

---

### Post by totfit on 2006-06-01
I too had this problem with Dapper Beta. I am not sure what happened. I also had an Nvidia card, but am not sure it was a problem. I noticed it after I installed KDE and have seen reference to there being a conflict that can occur between Gnome and KDE  and Open Office. I had reinstalled Breezy, then back to Dapper with no problems now of which I know. I too would like an answer. 

Gregg

---

### Post by marsopia on 2006-06-01
Same problem to mee, also have a Nvidia, MX4000, also Gnome and KDE instlled. This happens since upgrading to dapper RC.

Mariano

---

### Post by edoardo on 2006-06-12
[QUOTE=daverab]Ok, I've been toying with DD 6.06 since about Flight 6. I thought this issue would have been resolved, but it hasn't.

I open OO Writer, Spreadsheet, Presentation, etc.

Everything looks ok, then I mouseover toolbar icons. They disapeer. I mouse over menu items, they disapeer. It seems to be some sort of refresh problem.

I had toyed with XGL in the past, but that's deactivated.

I'm not too sure if it is an issue with my Nvidia driver, Java or something like GTK.

Anyone have suggestions on at least what I should do to narrow down what the issue could be?[/QUOTE]

happened to me after i installed kubuntu&various kde stuff on my vmware install
no nvidia/ati drivers ever here.

any known fixes  ?

---

### Post by wouterd on 2006-06-26
same here.. still no fixes?

---

### Post by ColinG on 2006-06-26
I also have mouseover problems although I see curser markers between each letter.

Also using  Nvidia .

Colin

---

### Post by ColinG on 2006-06-26
[QUOTE=ColinG]I also have mouseover problems although I see curser markers between each letter.

Also using  Nvidia .

Colin[/QUOTE]

Solved (so far anyway. ). installed the 686 kernel

---

### Post by edoardo on 2006-06-27
[QUOTE=wouterd]same here.. still no fixes?[/QUOTE]
remove openoffice-kde 

I logged this at [https://launchpad.net/bugs/50581](https://launchpad.net/bugs/50581)

---

### Post by wouterd on 2006-06-27
Thanks! I'm not sure it works, though, since I've never tried it. I got frustrated and removed the complete set of kde packages.. :confused: 
Anyway: that works.

---

