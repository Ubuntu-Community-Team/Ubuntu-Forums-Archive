---
title: "debian problems whit update manager"
date: 2008-05-22
forum: Debian
---

### Post by cmay on 2008-05-22
hi
i just installed debian etch yesterday.
i have installed whit allow no root login so 
i would expect to use sudo for any
 administrative work.
which of course was what i 
intened to do like in ubuntu.
when the updatemanager tells me there are new updates i click on the icon and normally it should ask for password and install updates automatic
how ever the messagebox that pops up asking for my password cant accept my password for some reason but
if i start a terminal and use apt-get or as example sudo synaptic it works whitout any problems.
how can i fix this so i can just do as normal and click on the install updates and it accept my password as it should do.
its a fresh install and i dont think i did anything that was wrong. could it be a slight bug or did i do something that i shouldent have.

thanks for reading this.

---

### Post by Raven_Oscar on 2008-05-23
Please try to run update manager from a console on behalf of your non-root user and show us its output.
Probubly it is possible to use sticky bit to start it on behalf of root every time you need this app but I am not sure that this is a secure way to use it.

---

### Post by cmay on 2008-05-23
hi thanks for the reply .
i did sudo apt-get update right now but this shows up.

E: Kunne ikke opnå låsen /var/lib/apt/lists/lock - open (11 Resursen midlertidig utilgængelig)
E: Kunne ikke låse listemappen

i use danish language settings so for those that cant make any out of this its saying 
e:cant open lock /var/apt/list/lock -open (11 resurce temporary uot of reach
e:could not open listfolder

i nerver had any problems as such whit debian before
 use it just as an ordinary computer user and i dont fidle around whit it in any way.
so i have not /.configeret any thing .
thanks for the help.

---

### Post by cmay on 2008-05-23
sorry its this i should have poested right?

sudo /usr/bin/update-manager

the output ->

/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
current dist not found in meta-release file

thanks

---

### Post by cmay on 2008-05-25
problem had to be fixed!
i broke something but the last coupel of hours i wonder why i did not just use lenny
all this time.
i love debian .

i build it from base install and i am so happy whit this that i had to show all of you this cool desktop :)
i found the wallpaper at minix homepage.

thanks for the help anyway

---

