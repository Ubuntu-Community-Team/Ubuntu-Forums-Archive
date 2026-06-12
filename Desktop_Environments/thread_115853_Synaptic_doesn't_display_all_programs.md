---
title: "Synaptic doesn't display all programs"
date: 2006-01-11
forum: Desktop Environments
---

### Post by Westerberg on 2006-01-11
Synaptic Package Manager displays the progams I have installed, but not the long list of potential installations from the repositories.  Also, with the Add Applications client all the potential programs to install are in light gray font and when I click on one I get the message:
[INDENT]> This program is not currently installable. It should be available in the "universe" section of the repository. Enable that section in the Repositories dialog in the Settings menu to install it.[/INDENT]
even though I have all binary repositories enabled.
When I try to install a program that should be availiable using apt-get, I get an error message -- "E: Couldn't find package ________".
I've apparently  mucked something up.  Any suggestions on how to fix the problem(s)?

---

### Post by emperor on 2006-01-11
Did you run "apt-get update" after you enabled the additional repos?

---

### Post by Westerberg on 2006-01-11
Thanks for replying.  Yes.  I ran "sudo apt-get update".  It made no difference.

---

### Post by daschl on 2006-01-11
please post your sources.list here :)

---

### Post by Westerberg on 2006-01-11
Thanks for your help, but I think I have it sorted now. 
When I logged on this morning, for some reason all the files in my /var/lib/apt/lists folder were gone.  When I opened Synaptic, it gave me an error message for each of the missing files.  Feeling bold and adventurous, I  created the missing files using "touch missingfilename".   Synaptic didn't like my files (I assume because they lacked a  proper PGP signature) and so couldn't update its repository list.  I now realize I simply should have used "sudo apt-get update" to create the files Synaptic needed.
Oh, well. Live and learn.

---

