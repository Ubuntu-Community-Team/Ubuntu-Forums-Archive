---
title: "Assaultcube reloaded"
date: 2012-05-26
forum: Gaming &amp; Leisure
---

### Post by TimmyK. on 2012-05-26
Hi, can anyone give me a step by step walkthrough on this? Thanks.

---

### Post by HolgerB on 2012-05-26
May be it helps if you elaborate what kind of guide you expect ?

---

### Post by TimmyK. on 2012-05-26
Just simple, start-to-finish instructions on how to go from not having it at all to playing it.

---

### Post by TimmyK. on 2012-05-26
Actually, I found instructions, but this line confuses me:
In a console, change your location (cd) to the main AssaultCube directory and then execute assaultcube.sh.
How would I do this?

---

### Post by asdk on 2012-05-26
Firstly, can't you get get Assaultcube from the software center? 

But, to your comment, in a terminal, you can type in 

$ cd Desktop/Home etc.

I'm not sure what directory you're using which has Assaultcube, I'm assuming you downloaded it, so it'd be

$ cd Downloads

Without the $.

---

### Post by HolgerB on 2012-05-27
1) Grab AssaultCube from here:
[http://sourceforge.net/projects/actiongame/files/AssaultCube%20Version%201.1.0.4/AssaultCube_v1.1.0.4.tar.bz2/download]("http://sourceforge.net/projects/actiongame/files/AssaultCube%20Version%201.1.0.4/AssaultCube_v1.1.0.4.tar.bz2/download")

2) Open up the downloaded tar with the archive manager from your filemanager

3) Choose to where to extract Assault Cube (e.g. /home/<your-user>/assaultcube)

4) Open a XTerminal of you choice

5) Typ cd /home/<your-user>/assaultcube and hit enter

6) Type ./assaultcube.sh and hit enter

Edit: Not to sound too offensive but here is all the information what you need to do:
[http://assault.cubers.net/docs/getstarted.html](http://assault.cubers.net/docs/getstarted.html)

Essentially some shell knowledge does not hurt.

---

### Post by TimmyK. on 2012-05-27
No, I've already got Assaultcube. I'm trying to get Assaultcube *Reloaded*.

---

### Post by HolgerB on 2012-05-27
> **TimmyK. said:**
> No, I've already got Assaultcube. I'm trying to get Assaultcube *Reloaded*.
Well then....
Assaultcube Reloaded shares the same file structure
/bin_linux/linux_client
or
/bin_linux/linux_64_client

And guess what:
assaultcube.sh calls those two binaries....

HTH,
Holger

---

### Post by TimmyK. on 2012-05-27
OK, I got the CD on downloads, but when I type in *assaultcube.sh* it doesn't do anything. What command do I execute?

---

### Post by Dlambert on 2012-05-28
isn't it ./assaultcube.sh? or Sudo?

---

### Post by TimmyK. on 2012-05-28
When I do that, it says "File or directory not found."

---

### Post by thatguruguy on 2012-05-28
> **TimmyK. said:**
> When I do that, it says "File or directory not found."

Make sure that it is executable.

---

### Post by TimmyK. on 2012-05-28
Make sure what is executable? I'm really confused. I got the part about setting the cd to downloads, but what command to I issue next?

---

### Post by Dlambert on 2012-05-29
Right click on the file, properties, "allow executing as a program"

---

### Post by HolgerB on 2012-05-29
> 
Make sure what is executable? 

That the file you want to execute is executable ?

Hint: man chmod

> 
I'm really confused. 

That is obvious ! Not to sound somehow offensive but IMO it makes little sense to provide further guidance unless you are willing to deepen your Linux knowledge.
All what is required to run Assault Cube has been elabourated above. 

To quote yourself from the previous page:
> 
Just simple, start-to-finish instructions on how to go from not having it at all to playing it.

There is no simple start-to-finish instructions if you are lacking the basic skills for working at shell level.

It is like asking for a simple, start-to-finish guide for driving a car if one does not even know what a steering wheel is. Or a simple start-to-finish guide for a heart transplant...
OK, I am exagerating a bit here.

I know that this is going against the Ubuntu code of coduct but I do not know how to make it clearer. I can either speak the truth or leave you here without answers.

Go, grab some book for Linux newbies. There are even a few out there which give you a quickstart in the console. We all started there.
Galileocomputing has a nice book for entering the Linux world but unfortunately it is in german:
[http://openbook.galileocomputing.de/linux/](http://openbook.galileocomputing.de/linux/)

I have no clue if there are any equal english books. May be someone else can suggest something identical ?

All the best,
Holger

---

### Post by TimmyK. on 2012-05-29
OK, thanks. I'll come back when I understand a little more.

---

### Post by Dlambert on 2012-05-29
I told you, did you try what I said?

---

### Post by 1204 on 2012-11-15
Hey this works even on my low-end pc and easy as unzip and play. Multiplayer works too. Downloaded from here [http://acr.victorz.ca/](http://acr.victorz.ca/)

---

