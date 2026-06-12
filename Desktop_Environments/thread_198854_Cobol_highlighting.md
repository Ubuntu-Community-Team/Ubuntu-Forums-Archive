---
title: "Cobol highlighting?"
date: 2006-06-17
forum: Desktop Environments
---

### Post by [S|G] on 2006-06-17
Is there any way to add cobol syntax highlighting to an editor such as kwrite? I know gvim has it, but right now I can't afford to stop working to learn how to deal with it (I will later, though).

Thanks!

---

### Post by asimon on 2006-06-22
Kwrite uses the kate's editor component but you are out of luck, there is no Cobol [syntax definition for Kate](http://kate.kde.org/syntax/index.php?kateversion=2.5). So either you have to wait until someone does a Cobol syntax definition for kate or you have to write your own syntax definition, see [Writing a Kate Highlighting XML File HOWTO](http://kate.kde.org/doc/hlhowto.php).

BTW, under Kubuntu you find the syntax files under /usr/share/apps/katepart/syntax/ .

---

