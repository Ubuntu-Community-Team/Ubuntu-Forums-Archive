---
title: "bring up task manager during fullscreen freeze"
date: 2010-05-12
forum: Desktop Environments
---

### Post by likethesauce on 2010-05-12
I've run into the situation recently where a fullscreen application freezes, and I can't regain control. Is there a way to bring up the task manager or simply kill the app in this event? ctr+alt+del, ctr+alt+backspace, alt+f4 and alt+f2 don't always work. Is there a way to set any of these commands so that they take priority in the event of a freeze?  Note: I'm on ubuntu Lucid, but I have had this problem on other versions.

---

### Post by DaymItzJack on 2010-05-12
You can try Ctrl+Alt+F1 to get you to a new login screen. Log in and then use the command "top". Switch back using Ctrl+Alt+F8.

---

### Post by BoneKracker on 2010-05-12
ctrl+alt+F1 to a terminal and log in
```
sudo kill $(pgrep stupidapp)
```
If that doesn't work, do```
kill -9 $(pgrep stupidapp)
```

Obviously, replace "stupidapp" above with whatever your frozen application is called (enough of its command-line name to uniquely identify it).

---

### Post by likethesauce on 2010-05-24
Thanks, I'll try this out if I get another crash. There's no reason I should have to do a hard restart in linux.

---

### Post by BoneKracker on 2010-05-24
That's essentially true.

Also, even in rare cases where the system seems to be completely locked up, you can use Alt+SysRq to do some important things (such as reboot safely):

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

Remember: "Raising Elephants Is So Utterly Boring" :)

---

