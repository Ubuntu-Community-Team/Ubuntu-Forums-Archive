---
title: "Bluefish 1.0"
date: 2005-01-13
forum: General Help
---

### Post by Smash on 2005-01-13
Hello, i'd like to install Bluefish 1.0, but i can't find a Warty package.
Could i use this [http://pkedu.fbt.eitn.wau.nl/~olivier/downloads/bluefish_1.0_unoficial-1_i386.deb](http://pkedu.fbt.eitn.wau.nl/~olivier/downloads/bluefish_1.0_unoficial-1_i386.deb) ? it's built for a debian unstable.

Thanks. Bye

---

### Post by Johan on 2005-01-13
[QUOTE=Smash]Hello, i'd like to install Bluefish 1.0, but i can't find a Warty package.
Could i use this [http://pkedu.fbt.eitn.wau.nl/~olivier/downloads/bluefish_1.0_unoficial-1_i386.deb](http://pkedu.fbt.eitn.wau.nl/~olivier/downloads/bluefish_1.0_unoficial-1_i386.deb) ? it's built for a debian unstable.

Thanks. Bye[/QUOTE]
 It will *probably* work. But if it's been in unstable for a while, you might be better off by enabling the universe repository and install it from there.

---

### Post by Smash on 2005-01-13
We have a 0.12 in Warty and a 0.13 in Hoary.
But it will be nice to have a 1.0  :mrgreen:

---

### Post by Smash on 2005-01-14
I tried to compile from source, but i have some problems with version of libraries (GTK etc..).

Can i upgrade only that lib from Hoary?  8-[ 
..i think no  :-( 

It's possible to backport?

---

### Post by mirtux on 2005-02-01
Hi (ciao...),
    i think you can use pick an rpm file, for example the one for Fedora Core 3 ([ftp://ftp.ratisbona.com/pub/bluefish/downloads/bluefish-1.0-1.fc3.i386.rpm]("ftp://ftp.ratisbona.com/pub/bluefish/downloads/bluefish-1.0-1.fc3.i386.rpm")), and then use  **alien** **bluefish-1.0-1.fc3.i386.rpm**. It will create a .deb package you can install with **dpkg -i ****bluefish-1.0-1.fc3.i386.deb**.
  
  Hope this can help,
  Regards,
  MC
  
  PS: buona giornata! Difficile scrivere in inglese quando sai che chi legge e' italiano!

---

### Post by mirtux on 2005-02-01
Hi,
     just another question only partly related to Bluefish: do you know a good _tutorial_ for starting creating web pages? I would like to build a new one, without losing to much time learning html books...
   
   Sorry, maybe this question is a little off topic.... [img]http://www.ubuntuforums.org/images/smilies/eusa_shifty.gif[/img]
   MC

---

### Post by machiner on 2005-02-01
Here's how I did it. Pretty standard Ubuntu install - I "upgraded" some things with debian repos:

Download the  src.rpm:
[http://rpm.pbone.net/index.php3/stat/26/dist/41/size/1378470/name/bluefish-1.0-1.1.fc3.fr.src.rpm](http://rpm.pbone.net/index.php3/stat/26/dist/41/size/1378470/name/bluefish-1.0-1.1.fc3.fr.src.rpm)
transmorgrify  that into .deb pkg with alien:

# alien bluefish-1.0-1.1.fc3.crc.rpm

you'get a .deb pkg as well as a .bz2 file.
Easy.

I ran 
# sudo dpkg -i bluefish_1.0-2.1_i386.deb  and it installed some files; icons...not the proggy. I had to then compile the .bz2 file...

Start 'er up ...extract the files, gothere run 
#./configure

I had to install a C compiler, and ARGH! there were 2 other files but I cannot find the log in synaptic -- I know I've seen it before...

Anyway - you'need to install 2 more files ( they have deps. as well)

so, after 
#./configure 
tells you the files you need (D'oh! sorry - I should've written them down)
run 
#make 
then 
#sudo make install.

See the pic.

[http://www.madcarters.com/bluefish.png](http://www.madcarters.com/bluefish.png)

---

### Post by WW on 2005-02-01
Did bluefish ever make it into jdong's backports repository?

---

### Post by mirtux on 2005-02-01
[QUOTE=machiner]
   
   Download the  src.rpm:
   [http://rpm.pbone.net/index.php3/stat/26/dist/41/size/1378470/name/bluefish-1.0-1.1.fc3.fr.src.rpm]("http://rpm.pbone.net/index.php3/stat/26/dist/41/size/1378470/name/bluefish-1.0-1.1.fc3.fr.src.rpm")
   transmorgrify  that into .deb pkg with alien:
   
   # alien bluefish-1.0-1.1.fc3.crc.rpm
   
  [/QUOTE]
   Hi,
     i think you have to download the compiled version here [ftp://ftp.ratisbona.com/pub/bluefish/downloads/bluefish-1.0-1.fc3.i386.rpm]("ftp://ftp.ratisbona.com/pub/bluefish/downloads/bluefish-1.0-1.fc3.i386.rpm") and then use **alien**.
   
   Regards,
   MC

---

### Post by machiner on 2005-02-01
sure -- I wanted to use source. Do what you feel.

---

### Post by mirtux on 2005-02-01
So, no problem!  :D

---

### Post by pavkonti on 2005-02-04
it needs libpcre.so to run. where i can find this library?

---

### Post by mirtux on 2005-02-04
It is the same for me.... libpcre3 are available in Warty repositories but it seems that bluefish 1.0 need libpcre0....

---

### Post by kleeman on 2005-02-04
I compiled from source and needed libpcre3-dev but it worked OK apart from that. I recommend using checkinstall so you can dump the package if needed.

---

### Post by mirtux on 2005-02-04
Thanks,
   i'll try to make it work.... BTW do you if there is a good HTML tutorial to start builing web pages?
 
 Thanks,
 MC

---

### Post by mirtux on 2005-02-05
[QUOTE=kleeman]I compiled from source and needed libpcre3-dev but it worked OK apart from that. I recommend using checkinstall so you can dump the package if needed.[/QUOTE]
Thanks, i've got it running well compiling from sources.... no problems with libpcre libraries, but i didn't understand why is not working with alien'converted packages!

Regards,
MC

---

### Post by kleeman on 2005-02-05
Perhaps it is because Mandrake has a different library setup than Ubuntu so the package is told to look in the wrong place for support libarires after alien does its work.

---

### Post by mirtux on 2005-02-06
Hi,
   thanks for reply but the problem is the same whatever precompiled version i choose (Fedora, Slackware etc...). However it's not a problem since now i have compiled from sources and it works..

Regards,
MC

---

