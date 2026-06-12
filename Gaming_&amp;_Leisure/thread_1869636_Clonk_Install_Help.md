---
title: "Clonk Install Help"
date: 2011-10-26
forum: Gaming &amp; Leisure
---

### Post by croney30 on 2011-10-26
Hello all, i'm relatively new to ubuntu and i'm having trouble trying to install clonk. I have it downloaded from the website, but i'm clueless from that point, all help will be appreciated. thanks

---

### Post by Perfect Storm on 2011-10-26
Right click on the package, and click 'EXtract here'.

Go into the the folder and double click 
a) clonk (32/bit) 
b) clonk64 (64/bit).

---

### Post by croney30 on 2011-10-26
I've extracted the files, but when i try to open the clonk or clonk 64 nothing happens when i click it.

---

### Post by Perfect Storm on 2011-10-26
Open the terminal.
Drag and drop clonk or clonk64 into the terminal
Hit enter.

Please post the output of the terminal.

---

### Post by croney30 on 2011-10-26
this is for clonk
'/home/connor/Downloads/cr_full_linux/clonk' 
/home/connor/Downloads/cr_full_linux/clonk: error while loading shared libraries: libSDL_mixer-1.2.so.0: cannot open shared object file: No such file or directory

and this is for clonk 64
'/home/connor/Downloads/cr_full_linux/clonk64' 
bash: /home/connor/Downloads/cr_full_linux/clonk64: cannot execute binary file

---

### Post by Perfect Storm on 2011-10-26
Before we advancing further:
Are you using 32bit or 64bit Ubuntu system?

---

### Post by croney30 on 2011-10-26
32

---

### Post by Perfect Storm on 2011-10-26
Ok, then there's no reason to get clonk64 working.


Here's what you do:
either install libsdl-mixer from Ubuntu Software Center

or by the terminal:
```
sudo apt-get install libsdl-mixer1.2
```

That should install the missing library that Clonk is complaining about.

---

### Post by croney30 on 2011-10-26
Thanks, it worked fine but it wasn't the version i was trying to get. if you know a place where you can get clonk classic for linux i would be very grateful. if not thank you so much for all your help, i am extremely grateful for this website and i will be using it in the future.

thanks

---

### Post by Perfect Storm on 2011-10-26
The clonk Classics can't run in Linux Native. Some of them you need  either Dosbox or wine to run.

---

### Post by croney30 on 2011-10-26
i have wine

---

