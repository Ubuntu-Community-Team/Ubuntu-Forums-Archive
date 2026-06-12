---
title: "Nautilus"
date: 2005-07-20
forum: Desktop Environments
---

### Post by James_Black on 2005-07-20
How do I put an launcher in Nautilus? For instance, when I want to put the Apollon icon in "Applications --> Internet", I type "nautilus applications:///Internet" in my console. But then I get this error:

```
"applications:///Internet" is not a valid location. Please check the spelling and try again.
```

---

### Post by Mr Frosti on 2005-07-20
I believe what you are asking is how to make changes to the "Applications" menu that is a part of Gnome. 

Nautilus is a file-manager with some other built in functions, similar to Windows Explorer. To make changes to your "Applications" menu, try installing the following utility:

```
sudo apt-get install smeg
``` 

This is a menu editor for Gnome, and is very useful. To start the program, click "Applications" -> "System Tools" -> "Smeg", or type "smeg" into a terminal. 

Some locations that are available in Nautilus are:

computer:/// - a list of available devices, similar to "My computer"
trash:/// - A list of files that have been marked for deletion, similar to "Recycle Bin"
burn:/// - (if you have optical drive that writes) - a list of files waiting to be copied to CD / DVD

---

