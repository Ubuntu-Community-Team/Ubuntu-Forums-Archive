---
title: "a couple of questions"
date: 2008-12-24
forum: General Help
---

### Post by Wartender on 2008-12-24
ok i have two questions to ask.
1) can you make a terminal profile that will have a specific size?
2) i have downloaded a client for tremulous (by following the instructions [here]("http://trem.tjw.org/")) but i can't run the .86 application i downloaded, it's weird because the original tremulous is a .x86 application and if i dowble-click it it runs, but when i double click the one i downloaded it says "There is no application installed for this file type", i checked properties and it says it's an application/x-executable, same as the other one. can anyone tell me how to make it run?
thanks in advance!

---

### Post by Wartender on 2008-12-24
solved the second question, can anyone answer the first one?

---

### Post by ajcham on 2008-12-24
In answer to your first question you can change the terminal dimensions by launching as follows:
```
gnome-terminal --geometry CCxLL
```
where CC is the width in characters and LL is the height in lines.
The terminal by default opens at 80x24.  Remember that the exact size of the terminal window is also determined by your choice of font (which *can* be changed in the profile).

Regarding the second question, if you have solved this yourself it would be best to post the solution so that others may also benefit from it.

---

### Post by Wartender on 2008-12-25
ok thanks that did it, by the way the solution to my first problem was right-clicking, going to properties->permission and checking the "allow executing file as program" box.

---

