---
title: "java PATH"
date: 2006-01-26
forum: Desktop Environments
---

### Post by stepore on 2006-01-26
Not sure why i can't get the java path to work this time. i've got it working on a laptop but with a fresh install of breezy i can't set the path.

output of  'echo $PATH':
/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games:/usr/local/bin:/opt/java/jre1.5.0_06/bin:

jre looks good.

my .bash_profile:
PATH=$PATH:/usr/local/bin:/opt/java/jre1.5.0_06/bin:/sbin:$PATH
export PATH

but 'which java' still indicates:
/usr/bin/java

and 'java --version':
java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

Biggest setback, i can't get Limewire to work, because it doesn't see the java path.

what gives? anyone?

cheers

---

### Post by jrib on 2006-01-26
Depending on how you installed java, 'sudo update-alternatives --config java' should let you use the other jre.  

Otherwise, if you want to do it your way, add the java folder to the beginning of your path, not somewhere in the middle.  Right now it seems like you are doing $PATH:java:$PATH, why two $PATH's?  And iirc, .bash_profile does not get sourced when you log into gnome.  Use ~/.bashrc or /etc/login.defs.

---

### Post by stepore on 2006-01-27
[QUOTE=_jason]Otherwise, if you want to do it your way, add the java folder to the beginning of your path, not somewhere in the middle.  Right now it seems like you are doing $PATH:java:$PATH, why two $PATH's?  And iirc, .bash_profile does not get sourced when you log into gnome.  Use ~/.bashrc or /etc/login.defs.[/QUOTE]

thanks for the edit. must have lazy eyes. didn't notice the first $PATH. i still have it in .bash_profile and gnome seems to recognize it fine during login. kde too.

thanks again.

---

### Post by rockprincess on 2006-12-13
I'm sorry to bring this thread up again....but i followed your instruction but yet it still doesn't work for me :(

here's my .bashrc file:

```
# ---- language-env DON'T MODIFY THIS LINE!
# settings for german speaking users

LANG=de_AT@euro
export LANG
CLASSPATH="/home/theresa/Daten/Programmieren/JMF-2.1.1e/lib/jmf.jar"
export PATH=$PATH:/home/theresa/jdk1.5.0_09/bin

#LC_MESSAGES=de_AT@euro
#LC_CTYPE=de_AT@euro
#export LC_MESSAGES LC_CTYPE

```

I'm hopeless :(

---

