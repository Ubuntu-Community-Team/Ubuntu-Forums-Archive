---
title: "i get some weird error :("
date: 2005-01-21
forum: Desktop Environments
---

### Post by akurashy on 2005-01-21
well i wanted to install amsn on my pc so i checked synactip and when i mark it for installation it says :"depends  libim 1" i dont know why some packages tell me that :(

---

### Post by albersag on 2005-01-21
[QUOTE=akurashy]well i wanted to install amsn on my pc so i checked synactip and when i mark it for installation it says :"depends  libim 1" i dont know why some packages tell me that :([/QUOTE]
 Try on shell

sudo apt-get install amsn

It downloads 2,2 MB and then it works :)

Tk programs are a little old (gui talking). Try gaim. I think is better in my personal opinion.

---

### Post by akurashy on 2005-01-21
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  amsn: Depends: imlib1 but it is not installable
E: Broken packages

---

### Post by akurashy on 2005-01-21
root@akulinux:/home/akurashy # sudo apt-get install imlib1
Reading Package Lists... Done
Building Dependency Tree... Done
Package imlib1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package imlib1 has no installation candidate

---

### Post by Rancoras on 2005-01-21
You're not using Hoary are you?  imlib may be broken at the moment.  Try again later.

---

### Post by akurashy on 2005-01-21
oh no no... problem fixed well kinda :P 

i forgot to enable some reposatory links and reload
so now i have the imlib and all

but i get a problem in aMSN (everything i press remember password and press ok it get stuck and i have to restart because i dont know how to kill the process :(

---

### Post by alynx on 2007-06-08
to kill a process you could 

```

ps ux |grep amsn

```

look for the process number then 

```

kill (process number)

```

---

