---
title: "alien arena"
date: 2010-04-07
forum: Gaming &amp; Leisure
---

### Post by nismo_2005 on 2010-04-07
ok so i downloaded alien arena from the repo. and when i click the icon in my games menu it dose nothing. when i try to launch it by typing alien arena with alt f2 it says there is no file. is this a common problem? what should i try to fix it? 
 the game looks great but i would like to be able to at least see a menu lol. oh and im in karmic

---

### Post by Perfect Storm on 2010-04-07
Copy the Alien Arena launch command (by editing the menu) to your terminal and execute it from there.

---

### Post by nismo_2005 on 2010-04-08
when i just copied and pasted the command it did nothing at all it did not even bring up the next line in the terminal.

but the comand was

> /usr/games/alien-arena --quiet

so i took out the --quiet (not sure why i did)

and that gave me this

> eddie@eddie-desktop:~$ /usr/games/alien-arena
using /home/eddie/.alien-arena/data1/ for writing
using /home/eddie/.alien-arena/arena/ for writing
execing default.cfg
bind <key> [command] : attach a command to a key
Unknown command "wave 4"
couldn't exec config.cfg
Console initialized.

------- sound initialization -------
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
AL lib: oss.c:179: Could not open /dev/dsp: Device or resource busy


---

### Post by Perfect Storm on 2010-04-08
It's a known issue, get the lateset version of AA from playDeb: [http://www.playdeb.net/welcome/](http://www.playdeb.net/welcome/)

If the issue is still there, look at this thread: [http://ubuntuforums.org/showpost.php?p=8312124&postcount=94](http://ubuntuforums.org/showpost.php?p=8312124&postcount=94)

---

### Post by nismo_2005 on 2010-04-08
ok i will let you know how it go's

---

### Post by nismo_2005 on 2010-04-08
ok i cant get playdebs website to open for some reason (most like isp related) so i tried the version on djl and still nothing the error djl gives me is

---

### Post by nismo_2005 on 2010-04-09
ok i got the newest version of aa from playdeb. no go. so i made the folder like in the file like in the link you posted. where am i supposed to put that file? and also my aa install only shows to folders inside the main one.

arena and data1 arena only has a file in it that says gconsol.log and data1 is empty.

---

