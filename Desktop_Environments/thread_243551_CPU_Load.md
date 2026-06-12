---
title: "CPU Load"
date: 2006-08-25
forum: Desktop Environments
---

### Post by Tantalus90 on 2006-08-25
Seems abnormally high (up to 100 %) when playing java games

The Ubuntu processes list lists 2 processes one using about 2% and the other using about 10 to 20 % (this is the one displaying the active processes etc)

Where does the extra 80% come from ?

Thanks

---

### Post by apjone on 2006-08-25
open a terminal and run the top command and that should tell you where the extra loads is from. Java is a pig anyway

---

### Post by Ramses de Norre on 2006-08-25
If it's java: which jre do you run? The one from sun (in the multiverse repo) works fine here.

---

### Post by Tantalus90 on 2006-08-25
Standard java from the multiverse repo and yes i know java is a hog but it seems to be using 20% or so according to top

the load is coming fron xorg itself (up to 50%) , any suggestions ?

thanks 
Tant

---

### Post by orb9220 on 2006-08-25
xorg loads problems of high cpu usage are usally a result of no or improper config of video drivers for the type of card you have.

Even with the right drivers you need to know if it supports things like 3d,glx,etc.. sorry not fully knowledgeable in this area but it appears here in the threads of the forums here.

---

### Post by Tantalus90 on 2006-08-25
That is a great help mate 

Didnt realise it could eat sooooooooooooo much processor 

Nvidia drivers are on my todo list but last time i tried it crunched the entire system and refused to load X at all 

maybe I should either wait till a new driver comes out or try one of the older versions ?

Tant

---

### Post by orb9220 on 2006-08-25
[https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper)

---

### Post by Tantalus90 on 2006-08-25
Yup got there, many thanks , Used method 2 from 

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#METHOD_2](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#METHOD_2)

Tant

---

