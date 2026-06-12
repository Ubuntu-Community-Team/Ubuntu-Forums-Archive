---
title: "cvs cedega ?"
date: 2005-03-14
forum: Gaming &amp; Leisure
---

### Post by Beire on 2005-03-14
today i tried to install cedega through cvs again.

All stept completed ok. but i can't launch it. Just gives me the unknown command line.

bash: cvscedega: command not found
bash: wineCVS: command not found
bash: winex: command not found


i used the linux-gamers script running as root and i've got a .WineCVS directory in my /root and home folders

---

### Post by thegnark on 2005-03-14
[QUOTE=Beire]today i tried to install cedega through cvs again.

All stept completed ok. but i can't launch it. Just gives me the unknown command line.

bash: cvscedega: command not found
bash: wineCVS: command not found
bash: winex: command not found


i used the linux-gamers script running as root and i've got a .WineCVS directory in my /root and home folders[/QUOTE]

after you get cedega fro mthe cvs you need to ensure you have some development tools installed to build it. you'll need:

build-essentials
bison
yacc
xorglib-dev (i think this is the name. it's something like this or libxorg-dev, or something to that effect)

i think there's some other package you need that has to do with x header, but i can't remember offhand

once you've installed all the above, cd to the winex directory that was created upon cvs download then you just need a `sudo ./tools/wineinstall`

i think wineinstall just does a configure, make, make install, install

anyway, that's what i did after many hours of banging my head on the wall

p.s. once installed (i installed from .debs) you just need `cedega /path/to/win32file.exe`

---

### Post by joe897897 on 2005-07-06
What i understand from your question is that the install of cvscedega is ok but your just can't run it as you type : $cvscedega
I ran into the same problem, the cvscedega binary is in /home/yourname/bin/
So, to run the command, your just have to try ~/bin/cvscedega install.exe for exemple.

Hope this helps

---

