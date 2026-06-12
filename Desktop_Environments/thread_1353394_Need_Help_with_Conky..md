---
title: "Need Help with Conky."
date: 2009-12-12
forum: Desktop Environments
---

### Post by Therekku on 2009-12-12
I cannot find the "Conky" Folder, Which is supposed to be located at usr/shared/doc/conky/examples/

I can only get up to usr/shaerd/doc/conky, after that there is only 3 folders and 1 file.

3 fodlers: 

changelog.debian.gz
changelog.dz
NEWS.debian.gz

1 File: 

"Copyright"

Am i missing folders or something?

been trying to find a solution for this for a long time, doesnt seem to work

( i tried to copy the config file from etc/conky. and made a folder in my "home folder" ( maybe here is where im going wrong? --> Places--> Homefolder --> Create Folder, Named it Conky, and pasted the file there, renamed it .conkyrc and changed the code inside it, and ran conky in terminal, however the "Default" one came up flickering, so what did i do wrong?

any tips appreciated.

---

### Post by roggenschrotbrot on 2009-12-12
".conkyrc" has to b placed in your home folder unless you select a special rc file with "concy -c <file>". if no .conkyrc exists there, a new one should be created, so this doesn't explain your flickering though.

---

### Post by spiderbatdad on 2009-12-12
>  Places--> Homefolder --> Create Folder, Named it Conky, and pasted the file there, renamed it .conkyrc 

not aware of running conky from ~/conky/conky.rc, but usually from ~/conky.rc

---

### Post by Therekku on 2009-12-13
Im not sure, but all the guides ive read say.
Go to usr/share/doc/conky/examples/conky.example should be there, that should be copied into
~/conky/ and named conky.rc.
(what does ~ stand for though)
and then edited with the desired code.
However i only get up to usr/share/doc/conky and after that i cant find example folder, which therefor means i cant find the file im supposed to copy.
I did try making a folder in my home folder called Conky and pasted the code i wanted there, and hit conky at terminal, however i only got the default one coming up instead of the one i wanted.

---

### Post by spiderbatdad on 2009-12-13
From user space ~/ is equivalent to /home/<user name>/
So, ~/Pictures is the same as /home/<user>/Pictures

From karmic I just ran apt-get install conky to see what is going on. It appears the default config file is now /etc/conky/conky.conf. IDK if it was previously there. Anyway that is the file you want to copy to ~/.conkyrc as a building block. There is a .conkyrc thread in this forum with 100's of examples posted.
Also just ran, and appears to work fine from ~/.conkyrc.
```
cp /etc/conky/conky.conf ~/.conkyrc
```Then edit the file to your liking...for example ```
double_buffer yes
background yes
#Then run it:
conky
```
You should see it is using your file.

---

### Post by stinkeye on 2009-12-13
[_[COLOR="DarkRed"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]_]("http://ubuntuforums.org/showthread.php?p=5436679#post5437628")

---

