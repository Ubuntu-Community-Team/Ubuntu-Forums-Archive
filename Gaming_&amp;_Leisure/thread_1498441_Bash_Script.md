---
title: "Bash Script"
date: 2010-05-31
forum: Gaming &amp; Leisure
---

### Post by endoglastic on 2010-05-31
Hey guys, i need help writing a very simple bash script. I know nothing about writing scripts but that's why i'm posting here.

I need a script that will run my counter-strike 1.6 server by using the terminal and running ./start_hldssurf.sh

My folder is located in the filesystem/hlds_surf.

All i need it to do is cd /hlds_surf , and run this command


./hlds_run -binary ./hlds_i686 -game cstrike -autoupdate +maxplayers 12 +port 27015 +map surf_ski_2 +pingboost 2 +ip 192.168.1.104 +tickrate 66


Thanks for your help, if you need any more information please post.

---

### Post by matchett808 on 2010-05-31
basically dump all that stuff in a text file and ur done! ( with a #!/bin/bash header )

---

### Post by endoglastic on 2010-05-31
ok but it automatically goes to root/ , i need it to go to /  . Everytime i start my server i use cd .., then cd /hlds_surf

---

### Post by matchett808 on 2010-05-31
just do 
cd /full/path/to/folder

---

### Post by endoglastic on 2010-05-31
sweet thanks that worked!! one more thing. Is there a way to do it through putty so that it does not open it in the putty terminal but rather opens it up on the actual linux box?

---

### Post by matchett808 on 2010-05-31
is it a graphical programme?

if not just add an ampersand (&)

---

### Post by endoglastic on 2010-05-31
the thing itself is just a terminal with constant information displaying.

---

### Post by endoglastic on 2010-05-31
I just put this in putty ./start_hldssurf &          , and it didnt work. once i exited out of putty the server went down.

---

### Post by matchett808 on 2010-05-31
put this at the end of the line that runs teh server:

&> /dev/null

---

### Post by matchett808 on 2010-05-31
sorry, try adding the ampersand to the command that runs the server

---

### Post by endoglastic on 2010-05-31
ok so add that in the bash script?

this one
 ./start_hldssurf &> /dev/null


or this one

./hlds_run -binary ./hlds_i686 -game cstrike -autoupdate +maxplayers 12 +port 27015 +map surf_ski_2 +pingboost 2 +ip 192.168.1.104 +tickrate 66 &> /dev/null

---

### Post by matchett808 on 2010-05-31
sorry this:
./hlds_run -binary ./hlds_i686 -game cstrike -autoupdate +maxplayers 12  +port 27015 +map surf_ski_2 +pingboost 2 +ip 192.168.1.104 +tickrate 66  &

should work

---

### Post by endoglastic on 2010-06-01
wow you are a genius!!! THANK YOU SO MUCH!!!

---

### Post by matchett808 on 2010-06-01
lol, not really, it just takes some geting used to.....

---

