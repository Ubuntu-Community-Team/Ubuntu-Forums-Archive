---
title: "Panel not showing"
date: 2009-03-26
forum: General Help
---

### Post by RobClews on 2009-03-26
Hi All,
I apologise if this is a common problem and I am completely useless at using the search feature!

I've just installed a dual boot Windows and Ubuntu. However, when I was experimenting with the desktop panel in Ubuntu, it froze and completely disappeared, so I restarted only to find that the panel does not show at all. 

Effectively, it means I am unable to do anything apart from click on the two desktop items my Computer and Opera. How can I restore it to default?

Thanks,
Rob

---

### Post by nothingspecial on 2009-03-26
No panels at all, or do you still have one?

---

### Post by fooman on 2009-03-26
try pressing the alt-f2 keys....see if a run dialog box pops up.

if it does,  then type the following into it:

```
gnome-panel &
```then click on "run"...  see if that gets them back.

---

### Post by RobClews on 2009-03-26
Hi, 
Im afraid nothing came up?

---

### Post by RobClews on 2009-03-26
I did click a few more buttons and got a command like screen asking for my user name and pass so i tried it in there but it didn't recognise it?

---

### Post by fooman on 2009-03-26
you mean no run dialog box when you pressed alt-f2 ?

ok then,  try this....right click on the desktop and choose "create launcher" from the menu.  in the box that pops up, type "terminal" in the name space and "gnome-terminal" (do not include the quotes when you type those out) in the command space.

then click ok.

that should place a launcher for the terminal on your desktop....click on it.

when it opens,  type the following into it:

```
gnome-panel &
```

press enter and see if that works.

---

### Post by RobClews on 2009-03-26
It doesn't appear as if that is working either?

---

### Post by fooman on 2009-03-26
sorry,  but which part did not work?

did you get a menu when you right clicked on the desktop?

---

### Post by RobClews on 2009-03-26
> **fooman said:**
> 
ok then,  try this....right click on the desktop and choose "create launcher" from the menu.  in the box that pops up, type "terminal" in the name space and "gnome-terminal" (do not include the quotes when you type those out) in the command space.

then click ok.

that should place a launcher for the terminal on your desktop....click on it.

when it opens,  type the following into it:

```
gnome-panel &
```

press enter and see if that works.

the run window doesn't appear - the menu appears but when i click on place a launcher nothing happens

---

