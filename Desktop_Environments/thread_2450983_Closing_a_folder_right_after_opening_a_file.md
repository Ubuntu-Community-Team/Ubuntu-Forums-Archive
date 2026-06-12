---
title: "Closing a folder right after opening a file"
date: 2020-09-24
forum: Desktop Environments
---

### Post by srv666 on 2020-09-24
Hello Ubuntu Community,

I wanted to ask if there is any way to program a behavior so that when I open a file, the folder that contained that file closes behind it right away.

Any help would be appreciated, thanks!

---

### Post by TheFu on 2020-09-26
Why not just open the file without opening the directory? 
I must be missing something in your workflow.

You can open most files from the program that can read that file by passing the filename in as the last option on the command. If the same file will be opened daily, just setup  script.  For example:
```
libreoffice "~/GTD-Todo.ods" &
```
Put that into a file, name it whatever you like, chmod +x it, and now you can run it from anywhere.  Depending on the DE you run, you can place a launcher on the desktop for it.  I don't think gnome3 supports that, by other DEs do.

---

### Post by metacell on 2020-09-28
You may want to use a folder menu on your panel. It gives you a drop-down menu of any folder, and when you click a file, the menu closes and the file opens.

Is that what you're looking for?

---

### Post by srv666 on 2020-10-11
Yes sir, that is awesome, thanks! :-)

---

### Post by metacell on 2020-10-12
To make it show files (not just folders), you need to type an asterisk in the File pattern box:

[IMG]https://imgur.com/xKdaK5B.png[/IMG]

(Sorry, can only screenshot the Swedish language version)

---

