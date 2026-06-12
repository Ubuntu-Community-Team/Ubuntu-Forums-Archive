---
title: "Kiba"
date: 2006-11-02
forum: Desktop Environments
---

### Post by samjones on 2006-11-02
](*,)  oh i am so stupid

i have tried and tried to install kiba  and i just dont know what i need to do...
this is what ive done so far...


1. First installed  packages
> 
**sudo apt-get install libgtk2.0-dev libssl-dev build-essential cvs libgconf2-dev libgconf2-dev**

**2. downloaded kiba dock from the cvs repository**
> 
**cvs -d:pserver:anonymous@metascape.afraid.org:/cvsroot co kiba-dock**

3. moved into the directory it has downloaded to
> 
**cd ./kiba-dock**

[INDENT]This is where the fun starts...:confused: [/INDENT]
Step four 
4. Run the make command
[B]
make  
[/B]
](*,) ](*,) ](*,)  HOW DO I DO THIS????

if anyone could be kind enough to tell me that would be good... please dont be nasty ive only used this os for a few days like this   i love it i just really want a DOCK  and not a crappy desklet one.

THANKS in advance for all your help !

Sam :KS

---

### Post by Paerez on 2006-11-02
you should just type "make" in the kiba-dock folder. If not, look for a "src" folder. You need to be in the directory where the code is. You'll know because there will be a file called "Makefile" or "makefile". You have to run make in that folder.

Good luck

---

### Post by TheWizzard on 2006-11-02
you'll need build-essentials installed for the make command.
i also strongly advice you to use checkinstall.

---

