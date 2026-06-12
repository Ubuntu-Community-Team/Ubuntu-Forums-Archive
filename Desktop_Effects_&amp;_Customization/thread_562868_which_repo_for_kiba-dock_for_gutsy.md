---
title: "which repo for kiba-dock for gutsy"
date: 2007-09-29
forum: Desktop Effects &amp; Customization
---

### Post by waldorf on 2007-09-29
Should I use :

    * deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
    * deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

or something different?

Is there a gutsy repository?

Thanks!

---

### Post by ThrobbingBrain66 on 2007-09-29
Until there is a Gutsy repo for AWN, you should compile the packages yourself. Using a Feisty repo will theoretically work, but you raise the risk of running into dependency issues and other nasty problems.

---

### Post by Rupertronco on 2007-09-29
I'm sure Trevino will make a Gutsy repo as soon as he can, but As ThrobbingBrain said, compiling is definitely the best way to go in the meantime.

---

### Post by waldorf on 2007-09-29
Thanks for the feedback!. I have never compiled anything in my life so I'm curious if y'all can recommend a howto. I saw there was one on the Kiba-dock wiki and this one:

[http://ubuntuforums.org/showthread.php?t=554127&highlight=kiba-dock+howto](http://ubuntuforums.org/showthread.php?t=554127&highlight=kiba-dock+howto)

Not sure which way is the best way to go.

Thanks in advance!

---

### Post by Rupertronco on 2007-09-29
Compiling software isn't really that tricky. The most important thing is to check out the readme or install notes if they exist. 

Sometimes you have to install build tools for the software such as autogen (that should be mentioned in the install notes if required). But basically you download the tar.gz file and extract it using 
```
 tar -xzvf packagename
```

then change into the newly created directory and type (this step might differ based on isntall notes)
```
./configure
``` 

after that
```
make
```

last
```
 sudo make install
```

It may stop you in the configure process and ask you for some additional dependency packages.

---

### Post by waldorf on 2007-09-29
Rupertronco

Thanks for the basic lesson. It occurs to me. If I compile from source, then I don't get the usual apt-get update notifications and the ubility to update through apt-get - right?

If that is the case, I think I will sit tight until there is a repository. Or maybe I'm not thinking of something . . .  and its no problem to compile from source.

At any rate, thanks!

---

### Post by Levo75 on 2007-11-19
Can i have a link to the tar.gz file that worked for any of you?

---

