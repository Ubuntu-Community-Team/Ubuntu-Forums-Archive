---
title: "Stupid Question - Frets on Fire"
date: 2010-01-10
forum: Gaming &amp; Leisure
---

### Post by Zyrtec on 2010-01-10
I downloaded Frets on Fire v1.3.110, and I have the folder in my Home directory. How do I get the game to install/launch? I know this is a stupid question, but I've just been using the programs from the repository so far... so yeah!

---

### Post by Zyrtec on 2010-01-10
Was this the wrong board to post this question D:

Can somebody please help?


Edit: Oh, I suppose I should add why I'm not just using the FoF from the Ubuntu Software Center. The FoF from the Software Center is jumpy and glitchy, and I've read that the game installed from the actual website is updated and works best.

---

### Post by 5nak3 on 2010-01-10
This should help


Go to applications -> accessories -> terminal and type


cd <pathtoextractedfolder> e.g. cd /home/Zyrtec/fretsonfire

press enter

then type 

fretsonfire <- i think this is the name of the executable file within the directory.

Let us know if it works!

---

### Post by Saiko Berry on 2010-01-10
...Get DMenu and activate it then type frets + enter? >_>

@Snake: No. It's more like

cd path/to/file
nohup ./fretsonfire &

---

### Post by xuCGC002 on 2010-01-11
> **Saiko Berry said:**
> ...Get DMenu and activate it then type frets + enter? >_>

@Snake: No. It's more like

cd path/to/file
nohup ./fretsonfire &

He downloaded the source from the FoF website, meaning he'll have to compile.

go to the directory where the folder was extracted, and type these three commands:
sudo ./configure
sudo make
sudo make install

And post the output.

---

### Post by meborc on 2010-01-11
nonono

i can see that everyone is just answering without really knowing what they are suggesting :)


this is how to get FoF working after downloading the tar from sourceforge


1) install dependencies (in my case **python-opengl** and **python-pygame**) this depends on what packages are already installed on your computer... you might also need **build-essential**

2) go to where you downloaded the tar file... right click and select extract here

3) open terminal... **cd** into the folder that was created from the tar file (in my case **cd /home/username/Downloads/Frets\ on\ Fire-1.3.110/**)

4) cd into the **src** folder

5) type **python FretsOnFire.py**

enjoy the game

after installing the dependencies you can also launch the game with this command (if you have the game folder in Downloads)
**cd && python Downloads/Frets\ on\ Fire-1.3.110/src/FretsOnFire.py**



this game needs no configure and no make... btw, never use sudo when you don't have to... ./configure and make will run just as well without sudo... the last make install has to be invoked with a sudo to get a system wide install... this is just a reminder - to keep systems safe, use sudo/root as little as possible

btw, FoF has the most hilarious tutorial :D

---

