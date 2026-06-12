---
title: "i want to run a script like an executable from a panel,how can i do it?"
date: 2005-03-14
forum: Desktop Environments
---

### Post by lorap on 2005-03-14
i've a matlab installed,but anytime i need use it i just go to the shell and run the script.is there any possibility to create a shortcat to the panel(not to the desktop)and just run it as executable?
thanks.
pavel

---

### Post by bored2k on 2005-03-14
[QUOTE=lorap]i've a matlab installed,but anytime i need use it i just go to the shell and run the script.is there any possibility to create a shortcat to the panel(not to the desktop)and just run it as executable?
thanks.
pavel[/QUOTE]
 This is an example script : the script name is lime.sh
>  #!/bin/bash
cd /opt/LimeWire/; sh runLime.sh
then i do chmod 755 lime.sh

In the launcher  I just type
sh lime.sh 
[just that because lime.sh is in my desktop]


Hope it helps

---

### Post by kafton on 2005-03-14
Since you already have a script to run your program, you could open Nautilus to where the script is and drag the script to the panel. Fill in the proper information in the dialog box that pops up, and your done. Works in Warty anyway.
Ed

---

### Post by lorap on 2005-03-14
thank you very much guys.
i'll try it once i get home.
pavel

---

