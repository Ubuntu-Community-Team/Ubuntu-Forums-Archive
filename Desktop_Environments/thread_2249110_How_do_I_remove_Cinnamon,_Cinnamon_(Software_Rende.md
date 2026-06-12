---
title: "How do I remove Cinnamon, Cinnamon (Software Rendering), Gnome, Gnome Flashback?"
date: 2014-10-19
forum: Desktop Environments
---

### Post by Lethukuthula on 2014-10-19
Hello guys, I am new to ubuntu and generally new to linux. I think i have landed myself into a real problem here. I am using ubuntu 14.04 with unity DE. I had another DE, Gnome 3 installed but didn't really use it much. Today I thought Id try out the Cinnamon DE and downloaded it from [www.omgubuntu.co.uk/2014/07/new-cinnamon-ubuntu-14-04-ppa-stable/](www.omgubuntu.co.uk/2014/07/new-cinnamon-ubuntu-14-04-ppa-stable/). When I got to my login screen to try out cinnamon there were other DEs added automatically i did not know about, now my login screen had:
[LIST]
[*]Cinnamon
[*]**Cinnamon (Software Rendering)**
[*]Gnome
[*]**Gnome Flashback (Metacity)**
[*]**Gnome Flashback (Compiz)**
[*]Ubuntu
[/LIST]
Now how do i completely remove all the other DEs and only leave unity. And where do i install a good cinnamon DE?
Please help!! Thanks in advance.

---

### Post by ibjsb4 on 2014-10-19
ppa-purge

This program disables a PPA from your Software Sources and reverts your
system back to the official Ubuntu packages. You can use this to return your
system to normal after testing a new version from a PPA.

---

### Post by Lethukuthula on 2014-10-19
Could you please give me a step-by-step example if possible, I dont know how to use the terminal very well. Also I would like only to remove only the ppa that i got cinnamon from without removing others i previously had. Also instead of going through the pains, can i remove the DEs through synaptic?

---

### Post by ibjsb4 on 2014-10-19
ppa-purge has a GUI, its called 'Y PPA Manager'.
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Y+PPA+Manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Y+PPA+Manager&sa=Search&cof=FORID:9)

If you want to use synaptic, remove 'ppa:lestcape/cinnamon' from your sources list.
[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

Make sure these packages are removed:
[https://launchpad.net/~lestcape/+archive/ubuntu/cinnamon?field.series_filter=trusty](https://launchpad.net/~lestcape/+archive/ubuntu/cinnamon?field.series_filter=trusty)

And then clean up using synaptic filters.
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

