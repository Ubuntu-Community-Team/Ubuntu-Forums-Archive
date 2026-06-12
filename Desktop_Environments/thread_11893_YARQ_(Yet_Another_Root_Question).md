---
title: "YARQ (Yet Another Root Question)"
date: 2005-01-20
forum: Desktop Environments
---

### Post by DharmaOne on 2005-01-20
I am setting up Icecast and needed to create a text file for my configuration. I open the directory (/etc/icecast) and try to create a new text document but can't save to the directory.

I then create the file in my home directory and then try to drag it to the correct directory but can't.

Yea, I know why. So I ended up at the command line running:
sudo vi icecast.conf

and then insert the text I copied (to clipboard) in the new document and saved.

But I should not have to go through all that to edit/create a text document
without having to go to the command line.

Is there a way, from the desktop, to run apps as root or force root
privileges so you can save/edit files?

(note: other than this picky item (which I did find a work around) this has
been the sweetest OS I have ever used! I am now in the process of converting all I know to the "sweet joy of the way").

-DharmaOne

---

### Post by Rancoras on 2005-01-20
I haven't tested it, but you could probably create a launcher that used the command    
```
gksudo nautilus
```
Might start nautilus in root mode.  That way you can move and create files in /etc

---

