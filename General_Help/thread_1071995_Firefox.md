---
title: "Firefox"
date: 2009-02-16
forum: General Help
---

### Post by 3dmatrix on 2009-02-16
If i close a Firefox window and try to open a new window again i sometimes get the following error message :

[B]Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system.
[/B]
After this no matter how long i wait to open a new window of Firefox, it keeps giving this same error message though there is no window of Firefox open.

Finally i have to restart the system. How can i view and delete the process ? As we do in windows by pressing ctrl+alt+del. What other way i can open firefox without having to restart the system ?

---

### Post by sylecn on 2009-02-16
You can use
> pkill firefox
to close the "running" firefox, and try start it again.

detailed process infomation can be list by
> ps -ef |grep firefox

---

### Post by alberto.cerna on 2009-02-16
Right clic on taskbar / panel, select Add to panel, then search for Force quit.

An icon will be added to your taskbar. Left click on this icon and your cursor will change to "+" then clic on the program you wanna close.

I hope this works for you.

---

### Post by 3dmatrix on 2009-02-17
Thanx for the help
I will  try it next time i face this problem.
 alberto.cerna
I do not have any Firefox window running at athat time to click with that + sign. How do I close it then ? I need a list of such 'running processes' to select and kill. Do we get it in ubuntu ? Else i will have to use the terminal.

---

### Post by sylecn on 2009-02-18
In GUI, you can find it here: GNOME Menu -> System -> Administration -> System Monitor
You get a list of running process and a "End Process" button.

---

### Post by glotz on 2009-02-18
> **3dmatrix said:**
> Else i will have to use the terminal.
The Horror. . . The Horror. . .

---

### Post by 3dmatrix on 2009-02-19
Thanx sylecn
That is exactly what i was looking for but pkill firefox is also working well :)  How can I make a short cut to it so that I just need to press that and it does the work !

---

