---
title: "Can I backup some files through the terminal only?"
date: 2009-02-17
forum: General Help
---

### Post by vizitorq on 2009-02-17
I upgraded to 8.10 which ended up being a bad idea because now I can't get xorg to run, so basically My computer boots, i see the ubuntu logo and the progress bar, then it goes back to the terminal, and then it won't load xorg. it says I have no monitors... whatever... anyway, I have some really really important data on it and I'd like to burn cd-r or dvd-r to back it up, but I only have access to do it through the shell. can I do this? how do i do it?

---

### Post by whoop on 2009-02-17
I searched the forums for you; maybe this helps:

[http://ubuntuforums.org/showthread.php?t=454282](http://ubuntuforums.org/showthread.php?t=454282)

---

### Post by beesthorpe on 2009-02-17
Yes I'm sure you can do this from the cli but if it were me I'd boot a live cd and use that to back up the files before trying to fix xorg.

---

### Post by brian_p on 2009-02-17
> **vizitorq said:**
> 

... anyway, I have some really really important data on it and I'd like to burn cd-r or dvd-r to back it up, but I only have access to do it through the shell. can I do this? how do i do it?

```
sudo apt-get install mkisofs wodim
```

and/or

```
sudo apt-get install dvd+rw-tools
```

---

### Post by kanikilu on 2009-02-17
There's a section in this guide on how to do it from the CLI:

[https://help.ubuntu.com/community/CdDvd/Burning](https://help.ubuntu.com/community/CdDvd/Burning)

And another guide on how to burn data DVD's:

[http://www.debuntu.org/2006/06/03/61-how-to-burn-dvds-from-the-command-line](http://www.debuntu.org/2006/06/03/61-how-to-burn-dvds-from-the-command-line)

> Yes I'm sure you can do this from the cli but if it were me I'd boot a live cd and use that to back up the files before trying to fix xorg.
+1 This seems like the easiest option if you have a live cd handy...although you would either need a 2nd CD drive to burn to, or a USB flash drive to copy your files to.

---

