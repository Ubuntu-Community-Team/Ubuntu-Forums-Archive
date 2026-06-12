---
title: "frusterated"
date: 2010-01-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lerichardson on 2010-01-11
[I] have a dell mini w/ ubuntu.
im tring to play a game on facebook and the screen prompts me to upgrade to adobe flash player 10. When I try to do this my OS says it does not recognise this flashplayer. I calleed dell and they said to ask the forums. Can someone give me directions on how to do this?
[/I]

---

### Post by dynamo2 on 2010-01-11
In a Terminal:
```
sudo apt-get install flashplugin-installer
```

---

### Post by lerichardson on 2010-01-11
I dont understand these directions. Im not very computer knowledgeable. Im tring to learn ubuntu. what does code mean?

---

### Post by lerichardson on 2010-01-11
ok i figured this out. it said that that code could not be found.

---

### Post by gabo.cr on 2010-01-11
Try this one:
If it doesn't work you would need to check if "multiverse" is active at the software manager.

```
$ sudo apt-get install flashplugin-nonfree
```

---

### Post by lerichardson on 2010-01-13
bash: $: command not found
This is the message it gave me. What do I do next?

---

### Post by lerichardson on 2010-01-13
how do I check if multiverse is the problem for using adobe flash player?

---

### Post by gabo.cr on 2010-01-13
> bash: $: command not found
This is the message it gave me. What do I do next? 

> how do I check if multiverse is the problem for using adobe flash player? 

Go to: System > Administration > Software Sources.
Make sure that "Restricted" and "Multiverse" options are checked, if not, then check it and run the Update Manager.

If that's checked, then another problem could be that you are not under the "sudoers" list. The command I gave you is working fine.

---

### Post by gabo.cr on 2010-01-14
Did it work?

---

### Post by teward on 2010-01-14
FYI: The command didn't work because you included the $ in the command.  Run the command without the $ and it should work.

---

