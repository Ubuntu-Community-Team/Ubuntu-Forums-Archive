---
title: "error in apt-get upgrade / update"
date: 2006-01-10
forum: General Help
---

### Post by razumihin666 on 2006-01-10
when i run the apt-get upgrade command i get this

[I]W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) etch Release: The following signatures couldn' t be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B90 7
W: You may want to run apt-get update to correct these problems[/I]

and when i run apt-get update i get the same thing

could you explain to me what this means and how to possible solve the matter?
this happens, too, in the same process...

[I]sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  ffmpeg libmjpegtools0 mjpegtools mplayer-386 qdvdauthor transcode
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.[/I]

---

### Post by Perfect Storm on 2006-01-10
You shouldn't add that to your sourcelist. You might end up screwing your system. What specific are you looking for?

---

### Post by razumihin666 on 2006-01-11
I'm not sure... as of lately I have been trying to install SecureFTP and DVDAuthor (or some sort of dvd authoring program, which I am still fishing around for)

So, I should just # it out or remove it completely?

---

### Post by lamego on 2006-01-11
Commenting it will be enough...

---

