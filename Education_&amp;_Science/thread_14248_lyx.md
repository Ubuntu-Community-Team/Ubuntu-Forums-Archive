---
title: "lyx"
date: 2005-02-05
forum: Education &amp; Science
---

### Post by vale on 2005-02-05
Hi all,
I don't konw if it is the right place for my questions... but I try :-)
1) How can I exatly do to install lyx (the friendly latex) in ubuntu?
2) I'm trying too install another program, but I get 
" error while loading shared libraries: libssl.so.4: cannot open shared object file: No such file or directory" 
do you know where can I find libssl.so.4 and how install it?
  
   cheers
    vale

---

### Post by kleeman on 2005-02-05
1) sudo apt-get install lyx-qt (I found it looks better if you also install kde)
    after installation execute with lyx-qt
2) I don't see this library on my system. Why do you need it? One thing to try is

      sudo ln -s /usr/lib/libssl.so.0.9.7 /usr/lib/libssl.so.4
(you are pretending that the Ubuntu ssl library is the one you need)
BTW you will need to install libssl0.9.7

---

### Post by vale on 2005-02-05
thanks
1) how can I also install kde?
2)I need that library to install "root", a program for physics analysis.
  cheers
   vale

---

### Post by vale on 2005-02-05
Sorry,
 but to correct use Lyx, do I need to install also some latex package?
If yes how?
 thanks
  vale

---

### Post by kleeman on 2005-02-05
Yes you need some tetex packages installed (tetex-base tetex-bin and tetex-extra) but I think these are standard with Ubuntu (you can check with synaptic). You may also want to install latex-xft-fonts to get math fonts. To install kde you need to have the universe repository enabled then just do "sudo apt-get intall kde"

---

### Post by vale on 2005-02-06
Ok I installed lyx,
but if I click "View" I can't see the options "DVI" and "PS".
Where are these?
I used Lyx under redhat and if I remember well there are these options!
   
 :-s 
thanks
      vale

---

### Post by kleeman on 2005-02-06
Sounds like you don't have some image viewing packages installed. This page lists
some recommended additional packages you might want to try....

[http://packages.debian.org/unstable/editors/lyx-common](http://packages.debian.org/unstable/editors/lyx-common)

You will need to reconfigure lyx when these are installed (Edit --> Reconfigure)

---

### Post by vale on 2005-02-06
Thanks!
I think all is warking now
  bye
    vale

---

### Post by felix.rommel on 2005-04-23
Hello,

I have the same problems here with Lyx. I installed version 1.3.4 from Ubuntu and all the dependencies.

But I get no DVI/PDF/PS preview in the menu.

Did you solve the problem?

Sorry, I haven't done the following:
> 
You will need to reconfigure lyx when these are installed (Edit --> Reconfigure)

Now it works, thanks. :)

---

### Post by kinnla on 2005-07-23
> you will need to reconfigure lyx when these are installed (Edit --> Reconfigure) 
good hint!

this thread contains all information needed to install lyx. working perfectly now. thx!

---

