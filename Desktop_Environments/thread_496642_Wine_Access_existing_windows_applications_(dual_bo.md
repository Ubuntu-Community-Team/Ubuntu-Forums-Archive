---
title: "Wine: Access existing windows applications (dual boot)"
date: 2007-07-09
forum: Desktop Environments
---

### Post by neoflight on 2007-07-09
Hello,

I have a system dual booting XP and linux. 
How can I install wine so that I can use the applications I already have in the XP installation. This is an office PC and I do not have the XP cd's to install thru wine. 

Thanks

---

### Post by scrooge_74 on 2007-07-15
to install wine you can do from terminal

sudo apt-get install wine


the usual way for wine to work (when the app is supported) is to tell wine to install the program and then you can run it.  You just can't use wine to run a program already installed.  I am not sure that will work.

But you can install from CDs by doing wine setup.exe (or install.exe it depends on the program)  from a terminal and then you can either get an entry in your Apps menu in Gnome or through the terminal go to ~/.wine/drive_c/the_rest_of_the_path_for_your_app and then wine the app

You can also check [http://winehq.org](http://winehq.org)  for more ingo

---

### Post by neoflight on 2007-07-16
> **scrooge_74 said:**
> the usual way for wine to work (when the app is supported) is to tell wine to install the program and then you can run it.  You just can't use wine to run a program already installed.  I am not sure that will work.



thanks...thats what i was wondering...i havent found any literature explaining how to access the windows applications when dual booting...alas, i do not have the cd's.. applications are all from the school preinstalled...

---

### Post by scrooge_74 on 2007-07-16
You may be able to copy the entire directory for the app into the wine directory tree and then register it using wineconfig

That is your best bet at getting it working

---

### Post by soapytheclown on 2007-07-16
not always true, i play world of warcraft through wine straight off my XP installation not configuring at all and it runs perfectly, sure a few frames slower than in windows but more than playable.

not sure that this will help you but if u can find your way to the exceutable on your XP partition from terminal then give it a try thats what i did.

---

### Post by w3po on 2007-09-23
Hello Gents
I know the thread has been quiet for a bit but I was wondering if anyone has figure out a solution to the wine question as I am looking for a way to run win apps on a dual boot Feisty/ winMe, and both OS are on the same drive. Please let me know if you figure something out.
Cheers 
Patrick

---

