---
title: "Change Directory Command not working at all D:!"
date: 2009-06-11
forum: General Help
---

### Post by XxsydenxX on 2009-06-11
Ok, so i go to change my directory in xubuntu....mind you this is a fresh install....i switched to xubuntu from ubuntu

open the terminal and type in

cd /home/xxsydenxx/launchpad-update.tar.gz

Doesn't find it....

I check there... oh HI, there it is @_@;

So I take it out of the tar and try going into the folder realizing this might have been my mistake...

Doesn't find it...directory doesn't exist...

So I try 

cd /home/xxsydenxx

Directory doesn't exsist?!?


Has anyone had this problem, id there a solution, because i need to to get this all set up..I have work to do @_@

Thanks to anyone whom takes the time.

---

### Post by michy99 on 2009-06-11
what is the output of```
ls -l /home
```

---

### Post by x33a on 2009-06-11
> **XxsydenxX said:**
> 

cd /home/xxsydenxx/launchpad-update.tar.gz

Doesn't find it....


here you are trying to cd into a file tar.gz.

first do
```
tar xvzf launchpad-update.tar.gz
```

then cd into the resulting folder.

---

### Post by XxsydenxX on 2009-06-11
> **michy99 said:**
> what is the output of```
ls -l /home
```

```
xxsydenxx@xxsydenxx-desktop:~$ ls -l /home
total 4
drwxr-xr-x 37 xxsydenxx xxsydenxx 4096 2009-06-11 22:22 xxsydenxx
xxsydenxx@xxsydenxx-desktop:~$ 

```

@ x33a

If you would have read further i already kinda took it out of the tar.gz =/

---

### Post by kerry_s on 2009-06-11
when you open a terminal, it's all ready in "/home/you" (~/)
use "ls -a" to see whats there.

the easy way is to use thunar right click> open terminal here

---

### Post by spillin_dylan on 2009-06-11
Also, make sure that your cases are correct.  Example:

```
cd /home/xxsydenxx
cd /home/XXsydenXX
cd /home/xxSYDENxx/
cd /home/xxSydenxx

```
...are all different.

Edit:  Nevermind, it looks like you got this part under control!

---

### Post by colau on 2009-06-11
> **XxsydenxX said:**
> Ok, so i go to change my directory in xubuntu....mind you this is a fresh install....i switched to xubuntu from ubuntu

open the terminal and type in

cd /home/xxsydenxx/launchpad-update.tar.gz

Doesn't find it....

I check there... oh HI, there it is @_@;

So I take it out of the tar and try going into the folder realizing this might have been my mistake...

Doesn't find it...directory doesn't exist...

So I try 

cd /home/xxsydenxx

Directory doesn't exsist?!?


Has anyone had this problem, id there a solution, because i need to to get this all set up..I have work to do @_@

Thanks to anyone whom takes the time.

```

cd /home/xxsydenxx/launchpad-update.tar.gz

```
launchpad-update.tar.gz is not a directory,you can't use cd commannd for that.
```

cd /home
ls -la

```

---

### Post by XxsydenxX on 2009-06-11
Eh, now when ever i run cd my computer shuts down, as if i was force shutting it down.

---

### Post by spillin_dylan on 2009-06-11
Well this certainly went from bad to worse....


Could this be something in ~/.bash_aliases or ~/.bashrc ?  Or could you have gotten haxx0red?

---

### Post by x33a on 2009-06-11
> **XxsydenxX said:**
> Eh, now when ever i run cd my computer shuts down, as if i was force shutting it down.

search the syslog for any suspicious entry, at the time the system shut down.

---

### Post by XxsydenxX on 2009-06-11
Well...i cant even use the terminal...just shuts down like i said before...

I think its best i reinstall?...i cant even use a safe session.

---

### Post by colau on 2009-06-11
> **XxsydenxX said:**
> Well...i cant even use the terminal...just shuts down like i said before...

I think its best i reinstall?...i cant even use a safe session.
Probably something is crashed with user-account.
Have a reinstallation.
Or you could try reinstalling gnome.
```

ALT+CTRL+F2
sudo aptitude update
sudo aptitude install gnome 
sudo aptitude install gnome-core
sudo aptitude instlal ubuntu-desktop

```

---

### Post by x33a on 2009-06-11
> **XxsydenxX said:**
> Well...i cant even use the terminal...just shuts down like i said before...

I think its best i reinstall?...i cant even use a safe session.

see if you can use the live cd, reinstall is the easiest way out, but it hampers your growth. i mean, you should at least try to diagnose the problem, fixing will come later.

---

### Post by kerry_s on 2009-06-11
> **XxsydenxX said:**
> Well...i cant even use the terminal...just shuts down like i said before...

I think its best i reinstall?...i cant even use a safe session.

go for it.

---

