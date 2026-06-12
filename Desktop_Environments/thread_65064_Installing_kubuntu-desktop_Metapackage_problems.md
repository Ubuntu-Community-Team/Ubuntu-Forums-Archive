---
title: "Installing kubuntu-desktop Metapackage problems"
date: 2005-09-12
forum: Desktop Environments
---

### Post by mfarquhar on 2005-09-12
please forgive my newbieness

i'm trying to install kubuntu-desktop metapackage on on a new ubuntu hoary install, but my only computer with internet access is a windows machine.

so how do i get the kubuntu-desktop through windows, burn it and then install it from a CD

is it even possible?

any help would be greatly appreciated

---

### Post by ltmon on 2005-09-12
You could burn the kubuntu hoary install cd, and then add it as a repository source via Synaptic (it's in the menus somewhere).

Then when you do:

sudo apt-get install kubuntu-desktop

it should grab the packages from the CD rather than the internet.

L.

---

### Post by mfarquhar on 2005-09-12
thanks a lot for your help ^_^

I was afraid i would have to do that

is there a way that i can get JUST kubuntu-desktop downloaded by itself

if not i'll have to do it the hard way.

thanks again for the help ^_^

---

