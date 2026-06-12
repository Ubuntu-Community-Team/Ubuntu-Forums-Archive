---
title: "VisualBoyAdvance-- beginner's mess"
date: 2011-10-14
forum: Emulators
---

### Post by Cu Rua on 2011-10-14
Extracted everything I could from a tar ball and now I don't know what to do with the mess I've made. I did manage to get the program running (mostly by accident), but now it sits on my desktop refusing to close, both sound and video were stuttery, don't really know what I'm doing. I get the feeling that all those text docs have something to do with it-- would somebody walk me through them? Here's a list: 

AUTHORS -------------                          -------------387 bytes       --------------author list
changelog                           -----------------------------26.3 KB         -----------------plain text document
changelog.Debian                -----------------4.5 KB            --------------ptd (plain text document)
conffiles                              ---------------------------------26 bytes         ------------ptd
control                                -----------------------------------1.0 KB           -----------------ptd
copyright                            -------------------------------1.1 KB-------------------            ptd
debian-binary                      --------------------------4 bytes----------------           ptd
md5sums                              ------------------------------958 bytes-----------------       ptd
NEWS                                  -------------------------------------26.0 KB         ---------------ptd
README                              ----------------------------------17.3 KB        ---------------README document
vba                                      ----------------------------------------999.1 KB       ----------------Link to executable
vba.glade                             ---------------------------------125.7 KB       ----------------Glade project
vba.mo                                 ----------------------------------14.5 KB         -----------translated messages (machine-readable)
visualboyadvance.conffiles      ----------26 bytes       -----------------ptd
visualboyadvance.list             -------------------926 bytes      -------------ptd
visualboyadvance.md5sums     -------------958 bytes      ------------ptd
visualboyadvance                  ------------------------999.1 KB       ---------------executable
visualboyadvance.----------------------------1                7.0 KB          -------------Troff document
visualboyadvance.cfg             -----------------------5.1 KB           -----------------ptd

They used to be neatly arranged into folders, but several files seemed to be duplicates of each other. I didn't delete or replace any of them, just in case. 

Also don't know what to do with what looked like configuration menus when the program first started up, and the only reason why I found the game I wanted to play was because I searched for it and carefully stashed it in my Documents folder when I first downloaded it (Final Fantasy Tactics Advanced, if that's any help). There's got to be an easier way to run this thing...

---

### Post by disturbedite on 2011-10-15
No need to compile or download an archive of it, just install VBA-M from the repos. (Not VBA or VBA Express, just VBA-M).

---

### Post by donkyhotay on 2011-10-15
> **disturbedite said:**
> No need to compile or download an archive of it, just install VBA-M from the repos. (Not VBA or VBA Express, just VBA-M).

+1, seriously the repos are the easiest way to install software. Don't compile unless you really have to.

---

### Post by Cu Rua on 2011-10-16
> **donkyhotay said:**
> +1, seriously the repos are the easiest way to install software. Don't compile unless you really have to.

Now to ask a dumb question: repos?

---

### Post by Perfect Storm on 2011-10-16
> **Cu Rua said:**
> Now to ask a dumb question: repos?

Repository. Ubuntu Software Center. Everything you want to install is there (almost).

---

### Post by Cu Rua on 2011-10-17
> **Artificial Intelligence said:**
> Repository. Ubuntu Software Center. Everything you want to install is there (almost).

Does that have anything to do with the synaptic package manager?

---

### Post by Perfect Storm on 2011-10-17
> **Cu Rua said:**
> Does that have anything to do with the synaptic package manager?

You can get it through Synaptic Package Manager, but if you're new to Ubuntu/Linux Ubuntu Software Center is easier to use.

---

### Post by donkyhotay on 2011-10-17
synaptic, apt-get, and the ubuntu software center all automatically download and install software from the same place, the ubuntu software reposistory (repos). Apt-get is a command line program, synaptic has some more advanced options to it and is more powerful if you know what your doing. If you just want to install a program then the software center is easy to use and where you should go first.

---

### Post by Cu Rua on 2011-10-20
Synaptic can't find anything in the line of VBA, visualboyadvance, or VBA-M. What's up with that?

---

### Post by thatguruguy on 2011-10-21
That's really strange.

Open the Ubuntu Software Center.  Click on "Edit" in the global menu, then "Software Sources".

Make sure that the entries for "universe" and "multiverse" are checked.
 
Close the Software Sources dialog, and try your search again.

---

### Post by juancpryor on 2012-01-14
Try looking for vbam. It's there.

---

