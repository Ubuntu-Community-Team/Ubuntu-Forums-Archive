---
title: "Adding fah to startup"
date: 2005-12-26
forum: General Help
---

### Post by Glottis on 2005-12-26
Hello, forum nOOb here, so please be nice :rolleyes: 
Im trying to get Fah running on my machine but i cannot get it to start.

Ive made the following .sh file, and have added it to session startup programs

cd /home/jon/Folding@Home/
chmod +x FAH504-Linux.exe
./FAH504-Linux.exe

cd /home/jon/Folding@Home/FahMon
chmod +x FahMon.exe
./FahMon.exe

Id like to get fah to stay up in the terminal window but i cannot figure out how to :( 
Finally managed to escape the wrath of M$ so im determined to get my system up and running.

Thanks in advance :D

Athlon64 2800 / 1GB Kingston PC3200/ DFI Lanparty UT 250gb / Ubuntu 5.1 x64

---

### Post by ardchoille on 2005-12-26
is fah a .exe file from the Windows world? If so, it's not going to run at all unless you run it with wine or something similar. .exe files do not run natively in Linux.

---

### Post by Glottis on 2005-12-26
thanks for the quick reply :D

no its not a windows .exe. Its a Linux tar.gz file downloaded from stanford. I ran ./configure and make install on both the files successfully. When i did this the first time the files ran ok. When i restarted the session i cannot get them to show up. I think my session startup "addition" is wrong but im fairly new to linux so i little help would be apprecieted :cool:

EDIT: the following files are in the folding directory (if it helps)


client.cfg
FAH504-linux.exe
FahCore_78.exe
FAHlog.txt
machinedependent.dat
MyFolding.html
queue.dat
src.tar.bz2
unitinfo.txt

---

### Post by sunshine02 on 2005-12-26
I can't help you with putting it into a startup file - I don't start up that often, but I open a terminal and code

cd <FAH directory>
./FAH502-Linux.exe

and it runs in the terminal where I can check on it when I wish. I keep it open on a separate desktop and when I do shutdown to work in XP, the terminal is available the next time I move back to Ubuntu, where I can just go to it and code:

./FAH502-Linux.exe

Hope this helps.

---

### Post by Glottis on 2005-12-26
worked a treat, thanks :D

---

