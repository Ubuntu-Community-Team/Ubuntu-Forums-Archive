---
title: "[SOLVED] question about kde 3.5"
date: 2008-03-18
forum: Desktop Environments
---

### Post by syms on 2008-03-18
hello,
i browse files with konqueror and when i open pdf or picture or any other document then it opens it on konqueror, i dont like this. i want that it will open with application. like pdf will be opened with kpdf, pictures with picture viewer. thanks and regards.

---

### Post by rigol on 2008-03-18
rightclick one file with the appropriate format -> Properties -> Open with tab -> add or choose your desired application

---

### Post by der_joachim on 2008-03-19
[LIST]
[*] Open kcontrol. If it is not installed, install it (*sudo aptitude install kcontrol *in a konsole should do the trick). It is more complete than Kubuntu's system settings utility. In KDE4, this menu is reachable by Clicking the tab 'Advanced' and then selecting 'File associatons', but I do not know whether the KDE3 version has it in the same place.
[*] Click KDE Components >> File associations
[*]In the textbox labeled 'Find filename pattern' you enter the file fype.
[*]Select the appropriate file type.
[*] In the right hand box, select the app of your choice and click 'Move up' until it is on top.
[*] Click 'Apply'.
[/LIST]

Good luck.

---

### Post by syms on 2008-03-19
thank you that helped

---

