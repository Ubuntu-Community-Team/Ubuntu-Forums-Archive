---
title: "Nautilus annoyances"
date: 2005-04-20
forum: Desktop Environments
---

### Post by anando on 2005-04-20
Hi

 I have recently installed Ubuntu Hoary and like it a lot. One annoyance that I have is that the Nautilus window changes its window size when I from one directory to another. Sorry if my English is not properly understood - this is what I mean : When I click on my home folder - the nautilus window is quite big and it shows all the files and directories - when I double click on say one of the directories in my home folder then the nautilus window size changes - this is very irksome. 

Can someone please tell me how to make Nautilus window size constant ?


Thanks,
Anando. ](*,)

---

### Post by ilari on 2005-04-20
The default operation of nautilus is called "spatial browsing", which means, that every directory/folder has it's own properties (ie. window size, window position etc.). If you don't like that, you can change the behaviour of nautilus to more "traditional" with gconf-editor. Just launch it from Applications->System tools->Configuration editor (or from shell with command 'gconf-editor') and navigate to key /apps/nautilus/preferences/ and tick the checkbox next to text 'always_use_browser'.

---

### Post by anando on 2005-04-20
Many thanks - it works !!  \\:D/

---

### Post by frijolito-ts on 2005-04-21
[QUOTE=ilari]The default operation of nautilus is called "spatial browsing", which means, that every directory/folder has it's own properties (ie. window size, window position etc.). If you don't like that, you can change the behaviour of nautilus to more "traditional" with gconf-editor. Just launch it from Applications->System tools->Configuration editor (or from shell with command 'gconf-editor') and navigate to key /apps/nautilus/preferences/ and tick the checkbox next to text 'always_use_browser'.[/QUOTE]
 Wow, thank you so much!

This spatial thing is *so* annoying! I'm sure it works very well for some people, and as I like to say, "to each his own". But to have it as default behavior... now that's just pedantic.

---

