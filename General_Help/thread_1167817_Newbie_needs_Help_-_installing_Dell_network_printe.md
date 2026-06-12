---
title: "Newbie needs Help - installing Dell network printer"
date: 2009-05-23
forum: General Help
---

### Post by afk46 on 2009-05-23
Hello,

I am totally new to Linux (Ubuntu) and I am trying to figure out how to install the "filters" for the Dell 3010cn network printer.
[I]
[http://openprinting.org/show_printer.cgi?recnum=Dell-3010cn](http://openprinting.org/show_printer.cgi?recnum=Dell-3010cn)[/I]

I get to install the diver manually using either Ubuntu's printer configuration utility or CUPS page but everytime I try to print a test page, the following message appears:

*"Filter "rastertodpl" for printer "Dell3010cn" not available: No such file or directory"*

This file and a couple of others are in folders next to the one that contains the diver (ppd file). Unfortunatly, I have no clue on what to do with them since I was not asked for them in the process of installing my printer... Also, I understand nothing to the commands in the installation instructions that came with the drivers. It says something about a "makefile" which was included in the driver package but I have no clue on what to do with it... Here are these instructions:

__

[I]Perform the compilation by doing:

$ make

If no errors appear you can install the filter and the drivers in the superuser environment:

$ su
Password: (Enter the root password and try again if it fails :-)
# make install

To finish you have to visit [localhost:631] with your favorite browser
and add a new printer by selecting the correct printer in the list.[/I] 
__


Thank you very much for your help ! Hope these drivers will work because this problem is the last thing that keeps me from fully switching  to Ubuntu!

Jim

---

### Post by chili555 on 2009-05-23
To compile a .tar.gz file, affectionately know as a tarball by us whitebeard linicians, you will first need to do, from a terminal:```
sudo apt-get install build-essential
```In the case of the *dplix* package, you will also need to open System -> Administration -> Synaptic and search for libcups and find the -dev variant(s). Mark for installation and about 10 other dependencies will be added. Click Apply. Now back to the terminal. Assuming the dplix folder is on your Desktop, do:```
cd Desktop/dplix/
make
```Assuming there are no errors, please do:```
sudo make install
```You should be all set, although I read in the Install file that you should delete your printer first and reinstall it after you compile the driver as above.

Post back if you get stuck.

---

