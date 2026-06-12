---
title: "apt-cache question"
date: 2005-10-26
forum: Desktop Environments
---

### Post by wwuster on 2005-10-26
I read that "apt-cache pkgnames" gives you a list of what is installed on your system and "apt-cache dumpavail" gives you a list of what is available.  Does the dumpavail also show what is currently installed?

Is there another way that I can get a list of what packages are available and not already installed?

I have a new "server" install and no gui.

thanks,
William

---

### Post by Stormy Eyes on 2005-10-26
The first thing I'd think to do is dump the output from both apt-cache commands to text files like this:
```
apt-cache pkgnames >> installed.txt
apt-cache dumpavail >> available.txt
```
And then use the diff command to compare the two:
```
diff installed.txt available.txt
```
However, the output diff provides can be a little hard to understand if you're not a geek. Try it, and see if that helps. If not, somebody else might know a better way.

---

### Post by arnieboy on 2005-10-26
[QUOTE=Stormy Eyes]However, the output diff provides can be a little hard to understand if you're not a geek. Try it, and see if that helps. If not, somebody else might know a better way.[/QUOTE]
a simpler way to read the diff output would be to use kdiff which gives u a side by side comparison.
```
sudo apt-get install kdiff
```

---

### Post by Stormy Eyes on 2005-10-26
[QUOTE=arnieboy]a simpler way to read the diff output would be to use kdiff which gives u a side by side comparison.
```
sudo apt-get install kdiff
```[/QUOTE]

kdiff is a good choice if you have X and KDE installed, but the original poster says he has a fresh server install without any sort of GUI.

---

### Post by wwuster on 2005-10-26
Does kdiff require a gui? I'm running strictly in console mode.

I did save "apt-cache pkgnames" to a file openssl, openssh-client, and openssh-server were listed, so I assumed that they were installed, but when I did apt-get install openssl etc I saw a message that said this was a NEW installation. I don't get it. What am I misunderstanding?


thanks,
William

---

### Post by arnieboy on 2005-10-26
aah sorry stormy eyes.. I hadnt read the first post.. so u are running on console eh?
well u may try the following... though am not sure it will work cuz I am not a linux box right now and I have no way to test it:
```
sudo dpkg -l \* | grep ^un >> available_but_not_installed.txt
```

---

### Post by herot on 2005-10-26
wwuster please remember that this is not a place for asking questions but is only for posting howtos...

---

### Post by poofyhairguy on 2005-10-27
Moved to correct forum.

---

