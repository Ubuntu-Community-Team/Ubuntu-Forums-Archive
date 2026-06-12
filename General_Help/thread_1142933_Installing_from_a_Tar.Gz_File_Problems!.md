---
title: "Installing from a Tar.Gz File Problems!"
date: 2009-04-29
forum: General Help
---

### Post by IBUA on 2009-04-29
Hey,

I've been trying to install the game "N" but have been having lots of problems.

The file is a tar.gz, but nothing i've tried to do has worked, i've been through the generic commands for extracting the file and so on and nothing works, most of the time the terminal says "this file or directory doesn't exist".

Please could anyone give me any tips/nudges in the right direction? E.g. maybe i've been doing the commands wrong, so give me a run through of them.

Cheers for the help

(P.S. The "Readme" file is no help whatsoever)

---

### Post by spiderbatdad on 2009-04-29
could you link to where you got the file...i'll give it a try

---

### Post by IBUA on 2009-04-29
> **spiderbatdad said:**
> could you link to where you got the file...i'll give it a try

Here: [http://www.thewayoftheninja.org/n_downloads.html]("http://www.thewayoftheninja.org/n_downloads.html")

Cheers

---

### Post by ddrichardson on 2009-04-29
Its a dependancy issue, if you untar it there is a single executable but if you run it from the terminal it asks for libgtk-1.2```
sudo apt-get install libgtk
```will do it. You might find it wants other deps - so run it from the terminal:```
./n_v14
```

---

### Post by IBUA on 2009-04-29
If this helps:

whenever i try ANY commaned it always comes up with this:

```
tar: n_v1linux.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```

The file is on my desktop.

---

### Post by IBUA on 2009-04-29
> **ddrichardson said:**
> Its a dependancy issue, if you untar it there is a single executable but if you run it from the terminal it asks for libgtk-1.2```
sudo apt-get install libgtk
```will do it. You might find it wants other deps - so run it from the terminal:```
./n_v14
```

Aweomse, ill try that. Thanks

---

### Post by IBUA on 2009-04-29
> **ddrichardson said:**
> Its a dependancy issue, if you untar it there is a single executable but if you run it from the terminal it asks for libgtk-1.2```
sudo apt-get install libgtk
```will do it. You might find it wants other deps - so run it from the terminal:```
./n_v14
```

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libgtk
```

:confused:

---

### Post by ddrichardson on 2009-04-29
Dude, from a command line - if it's on your desktop```
tar xvfz ~/Desktop/n_v1linux.tar.gz
```

---

### Post by Simian Man on 2009-04-29
You can also right-click on it and choose "Extract here".

---

### Post by ddrichardson on 2009-04-29
Sorry, it's libgtk1.2 in synaptic so```
sudo apt-get install libgtk1.2
```

---

### Post by IBUA on 2009-04-29
> **ddrichardson said:**
> Dude, from a command line - if it's on your desktop```
tar xvfz ~/Desktop/n_v1linux.tar.gz
```

Ah right thanks, but how do i install it?

---

### Post by ddrichardson on 2009-04-29
It doesn't need installed its a single executable file - change into the folder it untarred and type:
```
./n_v14
```

---

### Post by IBUA on 2009-04-29
> **ddrichardson said:**
> It doesn't need installed its a single executable file - change into the folder it untarred and type:
```
./n_v14
```

What do you mean change into folder?

Thanks for all the help!!

---

### Post by ddrichardson on 2009-04-29
Open a terminal and type```
ls
```There should be a folder called n_v1linux, type```
./n_v1linux/n_v14
```

---

### Post by spiderbatdad on 2009-04-29
ok as you've discovered this is a binary file you will launch from the terminal after you cd into the n_v14 folder.
You will then likely encounter a file not found error for libc6.2-2.so.3
You will need to create a symbolic link:
```
sudo ln -s /usr/lib/libstdc++.so.6.0.10 /usr/lib/libstdc++-libc6.2-2.so.3

```Then run the program.

---

### Post by ddrichardson on 2009-04-29
And you've discovered why package management is such a good idea ;-)

---

### Post by IBUA on 2009-04-29
> **spiderbatdad said:**
> ok as you've discovered this is a binary file you will launch from the terminal after you cd into the n_v14 folder.
You will then likely encounter a file not found error for libc6.2-2.so.3
You will need to create a symbolic link:
```
sudo ln -s /usr/lib/libstdc++.so.6.0.10 /usr/lib/libstdc++-libc6.2-2.so.3

```Then run the program.

YAAYYY it works  now!!! thanks to all :)

---

