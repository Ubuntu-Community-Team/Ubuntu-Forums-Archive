---
title: "just installed compiz now I don't have a keyboard layout"
date: 2006-09-21
forum: Desktop Environments
---

### Post by genesiss on 2006-09-21
I followed instructions in here [http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit]("http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit") but still I have not been able to fix this, can anyone help me here???

---

### Post by MetalMusicAddict on 2006-09-21
Are you talking about your keyboard shortcuts? If so Compiz now controls them instead of Metacity. [SIZE="1"](do I have that right?)[/SIZE] So you have to set you keys thought the Compiz config.

---

### Post by genesiss on 2006-09-21
ok when i need to use some keys on my keyboard  they wont work, like numpad, when i go to System-preferences-keyboard and then layout, the keyboard model is unknown, and when i click on add ( available layouts windows) is empty
thanks

---

### Post by dimkotz on 2006-10-17
I have exactly the same problem.any solution?
do i have to change something in xorg.conf?

---

### Post by dimkotz on 2006-10-17
silly me.the solution is at the end of the page[http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit]("http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit")

the line
load "xkb"
was mising from the "Section Modules" in xorg.conf file.
so i added it there and then folowed the instructions of the link above

---

