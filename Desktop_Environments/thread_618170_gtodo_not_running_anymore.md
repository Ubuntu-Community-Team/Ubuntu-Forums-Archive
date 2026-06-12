---
title: "gtodo not running anymore"
date: 2007-11-20
forum: Desktop Environments
---

### Post by arno77 on 2007-11-20
I really liked using gtodo because it helped me staying organized ... but now it does not run anymore :(. When calling the program it tells me the following:

arno@CM1032710-A:/usr/bin$ gtodo
cl_path: /home/arno/.gtodo/todos
size: 5876
Entity: line 39: parser error : xmlParseEntityRef: no name
ummary>Master thesis Paul Martinussen</summary><comment>Read and comment Intro &
                                                                               ^

Can anybody help me with this?

---

### Post by smartbei on 2007-11-20
I have never used gtodo so this may be off. However, it looks like it stores the todos in a basic xml file. It looks like this file is mildly corrupted - it should probably be <summary> and not ummary>. I would open the file with gedit, go to line 39 and see if it needs repairing. If you are not sure how to repair it post an excerpt from the file of about 5 lines with the bad line in the middle and maybe we will be able to help.

BTW - this should probably be under General Help, and not Desktop Environments (the problem isn't with gnome, it is with a specific program).

---

