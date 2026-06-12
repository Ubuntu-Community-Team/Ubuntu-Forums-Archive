---
title: "[Gutsy] Compiz Fusion on Nvidia 169.07"
date: 2008-01-13
forum: Desktop Effects &amp; Customization
---

### Post by daxLeet on 2008-01-13
Nevermind, solved, ignore this thread.

I was having random freeze issues so I upgraded to the Nvidia 169.07 BETA driver through envy.  I don't have the random freezes anymore, but Compiz Fusion doesn't work.  It says I need to install the restricted driver when I try to enable it in System> Preferences> Appearence.

Is there a way to use the 169.07 driver on Compiz Fusion, and it there a tutorial for it somewhere?



edit: "compiz --replace" :redface:

---

### Post by maxol on 2008-01-20
^^^

---

### Post by gspat on 2008-01-20
There is a fix for this somewhere on the forums (search isn't working for me ATM... I recall something about using envy and bypassing restrited driver manager though.

hope this is helpful!

---

### Post by maxol on 2008-01-21
A word of warning...

The Nvidia 169.07 drivers do not support CPUs without the SSE instruction set.

I spent quite some time wondering why all my 3D applications crashed  at startup on My Athlon 1.2 system before finding [this]("http://www.nvnews.net/vbulletin/showthread.php?p=1522860").

---

### Post by dhaniekonugroho on 2008-02-24
Dear All,

I have same problem with nvidia 169.07.
I just install nvidia geforce 8600, and i update my nvidia driver using envy, but compiz fusion wont start. 

Is there any other way to enable my dekstop effect?

please help me..:((

thanks

---

### Post by kaivalagi on 2008-03-02
The only way I got compiz to work was to set it up after envy, allowing it to switch back to standard restricted, then install envy again before the reboot..oh what fun

I need a way to stop the restricted driver requirement as envy is already in place 

I'm still searching :)

---

