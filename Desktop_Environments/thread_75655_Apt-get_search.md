---
title: "Apt-get search ?"
date: 2005-10-14
forum: Desktop Environments
---

### Post by dbee on 2005-10-14
How do I search for packages from the 

apt-get 

command line ???

thanks

---

### Post by pburch on 2005-10-14
aptitude search <package_name>

---

### Post by Dr. Nick on 2005-10-14
Use synaptic, its a gui for apt-get 
Or you can use wildcards from the command line such as ```
sudo apt-get install lin*
``` but I dont recommend it as its sorta a pain, Synaptic seems easiest


Or just look up one post :) Perfect timing

---

### Post by dbee on 2005-10-14
cool, thanks guys 

I do have another question though, pburch

what does the 

i
p
c
v
 
before the packages list stand for ???  

(i = installed obviously)

---

### Post by joscar on 2005-10-14
or use apt-cache search

---

### Post by dbee on 2005-10-14
Thanks joscar, I'm having a bit of a problem though with the search string, when I enter 

apt-cache search apache

I get a load of packages that have apache in neither their title's nor descriptions
When I enter

apt-cache search ^apache$

I get only packages that have the SPACEapacheSPACE in their titles or descriptions
But when I enter 

apt-cache search ^*apache*$ 

I get an error, how do I get a nice description of packages with apache in their titles or descriptions like synaptic gives me ???

---

### Post by dbee on 2005-10-14
ok, now I found it

apt-cache --name-only search apache

---

### Post by dbee on 2005-10-14
right, now just one more thing and I'll be sorted 

how do I see which of those packages I've already installed ???

is there any easy way to get the ease of use of the gui synaptic with the convienence of the command line ??

---

### Post by golfie on 2005-10-14
As already refered to in a previous message:

aptitude is probably what you are looking for..

---

### Post by zojas on 2005-10-15
yes, but what exactly do I type to get a list of packages installed on the system, with their version numbers?  in redhat, I could do 'rpm -qa' and in gentoo, it's 'qpkg -I -v'

---

### Post by DJ_Max on 2005-10-15
[QUOTE=zojas]yes, but what exactly do I type to get a list of packages installed on the system, with their version numbers?  in redhat, I could do 'rpm -qa' and in gentoo, it's 'qpkg -I -v'[/QUOTE]
As suggested, aptitude is what you're looking for.

---

### Post by khc on 2005-10-15
dpkg -l

---

### Post by b34r on 2005-10-15
dpkg -l | grep package

---

### Post by zojas on 2005-10-15
thanks, 'dpkg -l' seems to do exactly what I want.

aptitude may do it too, but I can't seem to see how. I tried "aptitude -F '%p %V %v' show" but that didn't work.

---

### Post by SilentCacophony on 2005-10-15
[QUOTE=zojas]thanks, 'dpkg -l' seems to do exactly what I want.

aptitude may do it too, but I can't seem to see how. I tried "aptitude -F '%p %V %v' show" but that didn't work.[/QUOTE]

Just in case you didn't know, **aptitude** can be run as a 'full console' ncurses app which lets you browse through packages, see descriptions, what is installed, etc... I prefer it over synaptic, myself. You can perform name searches by using '/' (find) and '\' (find next) from within the interface. Also has a drop-down menu via F10, and will change to root access as needed. Just run simply:

aptitude

in a terminal.

---

### Post by sizzam on 2005-10-16
[QUOTE=zojas]yes, but what exactly do I type to get a list of packages installed on the system, with their version numbers?  in redhat, I could do 'rpm -qa' and in gentoo, it's 'qpkg -I -v'[/QUOTE]

I like synaptic

```
sudo synaptic
```

Its a nice GUI, and you can look at stuff in categories or all at once.

---

### Post by zojas on 2005-10-16
yes, I agree it's a nice gui, and I use synaptic too. sometimes though I just want to get a text listing of installed packages and their version numbers. 'dpkg -l' seems to do that

---

### Post by matw on 2005-10-16
Some have suggested using "dpkg -l", but it truncates long package names. I had better luck using "dpkg-query --show". I ended up embedding
dpkg-query --showformat='${Package} ${Status}\n'
along with "grep installed" in a shell script that I used to keep track of installed packages.

---

### Post by Curlydave on 2005-10-16
Synaptec.

---

### Post by zojas on 2005-10-18
[QUOTE=matw]I had better luck using "dpkg-query --show". [/QUOTE]

awesome, this has been added to my 'aptcommands' file. :)

---

### Post by rasty on 2008-02-08
Also from the full gui(synaptic package manager) this is possible through status filter and checking installed...I think cause I'm writing from windows right now. aptitude is fine also. maybe even better than synaptic. It's more stable and faster I think.also allows browsing using mouse pretty cool

---

### Post by syrnick on 2008-04-20
> **dbee said:**
> cool, thanks guys 

I do have another question though, pburch

what does the 

i
p
c
v
 
before the packages list stand for ???  

(i = installed obviously)

The following is from "man aptitude"

Each search result is listed on a separate line. The first character of each line indicates the current state of the
           package: the most common states are** p**, meaning that no trace of the package exists on the system, **c**, meaning that
           the package was deleted but its configuration files remain on the system, **i**, meaning that the package is installed,
           and **v**, meaning that the package is virtual. The second character indicates the stored action (if any; otherwise a
           blank space is displayed) to be performed on the package, with the most common actions being** i**, meaning that the
           package will be installed, **d**, meaning that the package will be deleted, and **p**, meaning that the package and its
           configuration files will be removed. If the third character is **A**, the package was automatically installed.

---

