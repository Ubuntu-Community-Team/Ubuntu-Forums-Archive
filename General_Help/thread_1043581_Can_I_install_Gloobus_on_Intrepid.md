---
title: "Can I install Gloobus on Intrepid ?"
date: 2009-01-18
forum: General Help
---

### Post by Fionnzer on 2009-01-18
Can I install Gloobus on Intrepid ?
I only saw a version for hardy on the site so im wondering

---

### Post by mssever on 2009-01-18
> **Fionnzer said:**
> Can I install Gloobus on Intrepid ?
I only saw a version for hardy on the site so im wondering
Try it and see. Odds are, it'll work.

---

### Post by Fionnzer on 2009-01-19
> **mssever said:**
> Try it and see. Odds are, it'll work.

it doesnt 
any ideas \??

---

### Post by DJ_Peng on 2009-01-19
I'm also having some issues on Intrepid, and I've posted a query on the [Gloobus support thread]("http://www.ubuntuforums.org/showthread.php?t=828774"). You may want to see if my issue is the same as yours, as well as get info on the latest versions, debs, etc., there.

---

### Post by mssever on 2009-01-19
> **Fionnzer said:**
> it doesnt 
any ideas \??
Details? Error messages? Are you installing from a .deb or building from source or doing something else? I don't use Gloobus, so I can't tell you specifics, but if you post the errors I might be able to help.

---

### Post by Fionnzer on 2009-01-19
> **mssever said:**
> Details? Error messages? Are you installing from a .deb or building from source or doing something else? I don't use Gloobus, so I can't tell you specifics, but if you post the errors I might be able to help.

Well Im a complete n00b on linux

I first tried [this .Deb for hardy ]("http://www.getdeb.net/release/3007") it didnt work > Error: Dependency is not satisfiable: libavcodec1d So I downloaded some of those .tar.gz files Which I just cant ever seem to work even after hours of googleing everyone just says "use the source" Which I havent a clue how to do 
I also tried using synaptic and add remove with no avail

Any help will be great

---

### Post by mssever on 2009-01-19
> **Fionnzer said:**
> Well Im a complete n00b on linux

I first tried [this .Deb for hardy ]("http://www.getdeb.net/release/3007") it didnt work  So I downloaded some of those .tar.gz files Which I just cant ever seem to work even after hours of googleing everyone just says "use the source" Which I havent a clue how to do 
I also tried using synaptic and add remove with no avail

Any help will be great
According to the thread DJ_Peng linked, the dependency error you get from the .deb is because a library got renamed in Intrepid for some reason, so the .deb file needs to be updated. If the Gloobus project is indeed dead as speculated in the other thread, there's not a whole lot of hope for that to happen.

To build from source, you first need to install build-essential and dust off your terminal (building from source is done from the terminal). Then, you need to extract the tarball (.tar.gz or .tar.bz2) and look for instructions. In many cases, you can cd to the source directory and run ```
./configure && make && sudo make install
``` after installing any necessary dependencies. However, that doesn't always work, so you need to look for a readme file or some other file that contains instructions.

---

