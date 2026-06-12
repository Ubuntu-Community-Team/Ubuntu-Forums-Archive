---
title: "Adding shortcuts?"
date: 2006-06-29
forum: Desktop Environments
---

### Post by knightsg on 2006-06-29
I'm having trouble working out how to create shortcuts of different types on the desktop. I'm using Xubuntu 6.06 (dapper), and of the posts I can find in this forum that relate to this topic, none of their suggestions seem to work. 

Well actually, I was able to create a desktop link to an application by creating a <application-name>.desktop file in my Desktop folder, but what I want to do now is create a desktop link to a folder on a mounted windows share. The share has been mounted already and I can access it through Thunar, but I have no idea how to create a link on my desktop. I tried right-clicking but there was no option to create a link or shortcut. Also, if there's an easier way to create shortcuts to applications than by manually creating a .desktop file, I'd appreciate that too.

Can anyone help me out here?

Thanks,
Guy

---

### Post by harishg on 2006-06-29
You can do it using the ln command in a terminal.

---

### Post by mustang on 2006-06-29
And to clarify the post above

```
ln <source file> <shortcut>
```

Example, lets say I have helloworld.mp3 in my mp3 folder and I want to create a shortcut to it on my desktop.

```
ln /mp3/helloworld.mp3 /Desktop/helloshortcut
```

In case you're interested, the **ln** command creates symlinks (symbolic links) which are essentially pointers.

---

### Post by exquest on 2007-11-20
so I'm curious how to deal with adding a shortcut to the "Document and Settings" folder in my windows partition.  Linux wont allow me to have spaces in the ln command.

---

### Post by 3rr0r on 2007-11-21
I'm going to guess you type it like this:

WINDOWS STUFF/Documents\ and\ Settings/


the "\" is used to denote a space.  let me know if it works.

---

