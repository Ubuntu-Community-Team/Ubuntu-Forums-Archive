---
title: "No C compiler in path"
date: 2005-10-27
forum: Desktop Environments
---

### Post by CharlieC on 2005-10-27
I am trying to install a tar.gz file. I got it opened just fine but when I did ./configure my error was no C compiler in path. I put the tar.gz file in /usr/local, which is what I did in suse. Then I tried it again from my home directory, same result. I went looking for C and did not really find anything I understand in synaptic. 
    Either I need to open the file someplace where the c compiler is in the path or find out what a c compiler is and where it is located. I know c is a programing language but I dont know anything about programing.
    Go easy on me I am pretty new to linux and brand new to Ubuntu and Gnome.

TIA
Charlie

---

### Post by GeneralZod on 2005-10-27
```

sudo apt-get install build-essential

```

There's no need to place the .tar.gz anywhere special :)

I seem to recall that there's a decent HOWTO on installing from source somewhere on these boards; I'll see if I can track it down :)

You might also want to enable the extra repositories in synaptic and see if an already-compiled version is available for a nice, easy install.  I'll try and find a HOWTO on this, too! (Edit: [Here](http://www.psychocats.net/sources.html) it is!)

---

### Post by Corvillus on 2005-10-27
I'd also recommend using checkinstall if you're compiling an application from source. You can get it by doing
```
sudo apt-get install checkinstall
```
Then when installing the package, instead of typing "sudo make install" type "sudo checkinstall". This will create a deb package when the program is installed, making it easy to uninstall with package management tools.

---

