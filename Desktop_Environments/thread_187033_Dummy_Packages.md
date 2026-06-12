---
title: "Dummy Packages"
date: 2006-06-02
forum: Desktop Environments
---

### Post by ahaslam on 2006-06-02
Hi,
I'm very pleased with Dapper Drake, it works brilliantly on my laptop.
I Just have a quick question, what's with all the 'Dummy Packages' in the repositories?
Here's a screenshot of Synaptic after searching for mplayer:
[ATTACH]10452[/ATTACH]
I have enabled all of the repositories in the list, could it be this that's causing the problem?
[ATTACH]10453[/ATTACH][ATTACH]10454[/ATTACH][ATTACH]10455[/ATTACH]
Cheers,
Tony.

---

### Post by ahaslam on 2006-06-02
When selected, the description pane tells you about the package and at the end they've added, "This package is only a transitional dummy package which depends on the real [package name] package".

Does this mean that it's just for upgrades, and will removed at a later date?

I never noticed any 'Dummy Packages' in  Breezy, so I really just want to know if this is normal.

Cheers,
Tony.

---

### Post by ubnoobie on 2006-06-02
it's what it is.. a transitional package to facilitate a change in how that application is packaged. instead of a gazillion different versions for each cpu type, there is now just 'mplayer'. 

the dummy packages exist because other packages may depend upon the old package names specifically and they allow those other packages to still pull in the new 'mplayer' package.

this is "normal" and there are more instances of this than you've noticed. ;)

---

### Post by ahaslam on 2006-06-02
[QUOTE=ubnoobie]it's what it is.. a transitional package to facilitate a change in how that application is packaged. instead of a gazillion different versions for each cpu type, there is now just 'mplayer'. 

the dummy packages exist because other packages may depend upon the old package names specifically and they allow those other packages to still pull in the new 'mplayer' package.

this is "normal" and there are more instances of this than you've noticed. ;)[/QUOTE]
Thanks for for your reply. 
I understand now, cheers.

---

### Post by greggh on 2006-06-04
I still don't understand. I installed mplayer, but I notice that the "dummy package" mplayer-686 is not marked in Synaptic. Should I select that dummy package and install it too since my PC is a 686? :confused:

---

### Post by ahaslam on 2006-06-04
[QUOTE=greggh]I still don't understand. I installed mplayer, but I notice that the "dummy package" mplayer-686 is not marked in Synaptic. Should I select that dummy package and install it too since my PC is a 686? :confused:[/QUOTE]
From the reply given by 'ubnoobie', it's my understanding that the dummy packages only exist to sort out dependencies for other applications that require say the K7 or 686 version. As he pointed out, there is now only one Mplayer version and the dummys are transitional packages only.

There's no need to install the dummy packages.

Tony.

---

### Post by greggh on 2006-06-04
So if a user is never supposed to install a "dummy package" why do so many of them appear in Synaptic? I am still very confused about this. Also, explaining a dummy package as a transitional package doesn't help me much because I'm not understanding what is really meant by a transitional package either. Oh well, hopefully I'll figure this out at some point, but right now I'll steer clear of dummy packages until I can figure out what they are and when you would need to install them. :confused:

---

