---
title: "Account/rights question"
date: 2006-03-02
forum: Desktop Environments
---

### Post by MichaelZ on 2006-03-02
Hello,

I have a small question concerning Ubuntu 5.10. I have just installed it on an old Pentium III 500 MHz and it works well.

I have remarked the keyboard layout problem (see [http://ubuntuforums.org/showthread.php?t=77092](http://ubuntuforums.org/showthread.php?t=77092)) when I wanted to change the layout of my keyboard. 

Anyway, the question I have is the following. I have had to modify the file xorg.conf. By using the terminal, I just gave the command, prompt for my password and all was fine. Instead, browsing with the File Manager and then open the file, I was not prompt to put my password and therefore I could not modify the file. If I check the xorg.conf properties, I could not modify it read-only status, because I did not have the necessary rights. But if I am the administrator, which rights I still need? 

After installing Ubuntu, I have crerated my account, which should be the administrator account or? Do I miss something?

Sorry for the a bit stupid question, but I am a newbie and the last time I have worked with Linux it was with an old Red Hat distribution (5-6 years ago).

Thank you very much.

Best wishes,
Michael

---

### Post by carlosqueso on 2006-03-02
It has to do with the way Ubuntu handles root (administrator) privliges.  There is no root account (actually there is, but it's turned off), so you use the "sudo" command to get root privliges.  To be able to use nautilus to change those files, you'll have to open up a terminal and type ```
sudo nautilus
```  see [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) for more details.

---

### Post by pbaehr on 2006-03-02
From the command line you can edit xorg.conf by typing
```
sudo nano /etc/xorg.conf
```
You'll be prompted for your password (your user password) and you'll have administrative access to the file.

---

### Post by Ramses de Norre on 2006-03-02
Or use gedit instead of nano if you want a gui, that's a little easier.

---

### Post by MichaelZ on 2006-03-02
Hello,

Thank you very much for your replies.

I have used:

> 
sudo gedit -w /etc/X11/xorg.conf


After giving my password, I could modify and save the file.

Best wishes,
Michael

---

### Post by Ramses de Norre on 2006-03-02
What is the -w option for? It isn't mentioned in the gedit manuals.

---

### Post by MichaelZ on 2006-03-02
[QUOTE=Ramses de Norre]What is the -w option for? It isn't mentioned in the gedit manuals.[/QUOTE]

Sorry, but I do not know. The command I have used was posted here by JanZ:

[http://ubuntuforums.org/showthread.php?t=77092](http://ubuntuforums.org/showthread.php?t=77092)

Best wishes,
Michael

---

