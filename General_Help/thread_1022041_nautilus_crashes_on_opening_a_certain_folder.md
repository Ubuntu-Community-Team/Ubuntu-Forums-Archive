---
title: "nautilus crashes on opening a certain folder"
date: 2008-12-26
forum: General Help
---

### Post by DMcA on 2008-12-26
I've recently upgraded to Intrepid and I can no longer open my 'downloads' directory in my home folder. The directory has 351 contents totalling 1.8G and I can access it fine from the command line. 


running "nautilus downloads" in the terminal gives an entry in the window list called "Starting File Browser" which lasts for a few seconds and disappears. 

running as root gives:

```
Initializing nautilus-share extension
seahorse nautilus module initialized
Segmentation fault

```

The window appears for less than a second in the window list and disappears. 

"gksudo nautilus downloads" gives

```
Initializing nautilus-share extension
seahorse nautilus module initializeduser@host:~$ 

```

i.e. no line break before the promt

and just clicking on "downloads" from an already open window in my home folder gives the same result as running "nautilus downloads". Does anyone know what's going on?

---

### Post by DMcA on 2009-01-17
bump?

---

### Post by mdurham on 2009-01-17
maybe you have a strange file name in there that Nautilus can't handle?

---

### Post by DMcA on 2009-01-18
Cheers, I never thought of that. Apparently there was a single file with some invalid encoding in the file name, no idea where it came from mind.

I wouldn't have thought that should crash nautilus but at least the problem's gone.

---

