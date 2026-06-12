---
title: "start program without entire path"
date: 2009-04-28
forum: General Help
---

### Post by wesg on 2009-04-28
Where should I put a script/application so that I can start it from the command line without entering the entire path?

Ie. instead of entering ~/Downloads/Application just entire Application and have the program run

---

### Post by wesg on 2009-04-28
Wait, I just found /usr/bin ... Is that right?

---

### Post by cariboo on 2009-04-28
I use a script to check the ip addresses of computers on my network, the script is located in /usr/local/bin, so to run the script I just type:

```
scan_all
```

---

### Post by 3Miro on 2009-04-28
If you have a script in /home/me/dir, then you can call it in several ways:

Via Full path, from anywhere:
```
/home/me/dir/script
```

Via /usr/bin:
```

sudo ln -s /home/me/dir/script myscript
```
Then from anywhere call:
```
myscript
```

Directly from the same dir:
```
cd /home/me/dir
./script
```

---

### Post by benj1 on 2009-04-28
you can use that, /usr/local/bin is prefered for hand installed things

or if you add a bin folder to ~/ 
then add 
```
export PATH=$PATH:~/bin
```
to ~/.bashrc
and you can put it in there without having to mess with sudo etc.

---

### Post by Anthon on 2009-04-28
if from the commandline you type 
  echo $PATH
you will get a colon seperated list of all the paths that are searched for commands
You can put your script/application in any of these (assuming you have write access)
You can of course also create a ~/bin directory and add that to the PATH env. variable in the .bashrc script using:

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

(You have to login again to get this to be added to path).

---

