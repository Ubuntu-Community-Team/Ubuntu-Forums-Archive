---
title: "ubutu 9.04 trying to work assualtcube"
date: 2010-12-03
forum: Gaming &amp; Leisure
---

### Post by masterrob213 on 2010-12-03
* *libSDL 1.2*
                         * *libSDL_image*
                         * [I]OpenAL
can anyone give me the turminal codes for those?
[/I]

---

### Post by thatguruguy on 2010-12-03
Where did you get your copy of assault cube?  Did you install it from synaptic?

---

### Post by masterrob213 on 2010-12-03
[http://assault.cubers.net/download.html](http://assault.cubers.net/download.html) and click the os you have and it will download

---

### Post by VastOne on 2010-12-03
> **masterrob213 said:**
> * *libSDL 1.2*
                         * *libSDL_image*
                         * [I]OpenAL
can anyone give me the turminal codes for those?
[/I]

Very clearly stated at the bottom of the link you gave...

If you're on a Debian or Ubuntu based system, you can run this command in a terminal to install these libraries: 

```
sudo apt-get install libsdl1.2 libsdl-image1.2 libopenal1 libsdl-ttf2.0-0 
```

---

### Post by masterrob213 on 2010-12-03
yea thats for all except the openAL  file that is the only one i am missing...... i think

---

### Post by VastOne on 2010-12-03
> **masterrob213 said:**
> yea thats for all except the openAL  file that is the only one i am missing...... i think

```
sudo apt-get install alsoft-conf
```

---

### Post by masterrob213 on 2010-12-03
that didn't work i got sudo apt-get install alsoft-conf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package alsoft-conf

---

### Post by VastOne on 2010-12-03
> **masterrob213 said:**
> that didn't work i got sudo apt-get install alsoft-conf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package alsoft-conf

Try Ubuntu Software Center or Synaptec and search for:

OpenAL-Soft

---

### Post by gbestrada on 2010-12-03
> **masterrob213 said:**
> yea thats for all except the openAL  file that is the only one i am missing...... i think

Have you already tried to run the game because I'm also a Ubuntu user and when I tried
to install those libraries It says that the last one was not found using old ones instead .
then I ran the game  and it worked perfectly.  :p

---

### Post by masterrob213 on 2010-12-04
yes i tried to run it and i get a black screen and my computer freezes so i don't know what i am doing wrong

just a thought could it becouse of my graphics card? if so can anyone tell me how i can upgrade it?

or do i need to upgrade to 9.10

---

