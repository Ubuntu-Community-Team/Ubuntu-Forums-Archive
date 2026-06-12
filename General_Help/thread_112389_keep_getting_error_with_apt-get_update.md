---
title: "keep getting error with apt-get update"
date: 2006-01-04
forum: General Help
---

### Post by taseal on 2006-01-04
here is the error I get

```

zip2: (stdin) is not a bzip2 file.
Err http://public.planetmirror.com breezy/non-free Packages
  Sub-process bzip2 returned an error code (2)
Fetched 113kB in 22s (5117B/s)
Failed to fetch http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz  Sub-process bzip2 returned an error code (2)
Failed to fetch http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
W: GPG error: http://public.planetmirror.com breezy Release: Unknown error executing gpgv
W: Couldn't stat source package list http://public.planetmirror.com breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 Böyle bir dosya ya da dizin yok)
W: Couldn't stat source package list http://public.planetmirror.com breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by taseal on 2006-01-04
same problem when I tried to install skype

```

Fetched 7906kB in 9m36s (13,7kB/s)
W: Couldn't stat source package list http://public.planetmirror.com breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 B&#246;yle bir dosya ya da dizin yok)
W: Couldn't stat source package list http://public.planetmirror.com breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 B&#246;yle bir dosya ya da dizin yok)

Paketler &#246;nyap&#305;land&#305;r&#305;l&#305;yor ...
Selecting previously deselected package skype.
(Reading database ... 99905 files and directories currently installed.)
Unpacking skype (from .../skype_1.2.0.18-1_i386.deb) ...
Setting up skype (1.2.0.18-1) ...
W: Couldn't stat source package list http://public.planetmirror.com breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 B&#246;yle bir dosya ya da dizin yok)
W: Couldn't stat source package list http://public.planetmirror.com breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 B&#246;yle bir dosya ya da dizin yok)
W: You may want to run apt-get update to correct these problems

```

---

### Post by JamesNorris on 2006-01-04
What happens when you run sudo apt-get update from the terminal?

---

### Post by taseal on 2006-01-04
[QUOTE=JamesNorris]What happens when you run sudo apt-get update from the terminal?[/QUOTE]


what I just posted happens....

everything goes fine til those errors pop up...

---

### Post by JamesNorris on 2006-01-04
Sorry, I missed that, just saw in the second post that is said to run update. Seems like a problem with the planetmirror package info file. Seems like apt is looking for a bz2 file rather than a gz file... Not sure how to fix it, though.

If you're just using it for skype, someone on these forums made a skype package for breezy based on the debian one, but with the qt3 deps changed to ubuntu versions. You could just search for it. If not, I can't really say what would work, but it seems apt really doesn't like that repository.

---

### Post by ldavey on 2006-01-04
I got the same problem with that repository and was just browsing these forums to see if anyone else has, guess i got my answer lol :D

not sure how to fix it but im sure a simple command will, i am just starting out on linux tbh .. anyone got a solution please ?

---

### Post by taseal on 2006-01-04
same here... i'm new to linux so i'm not sure

I would say its something that u'd have to change in the source file 

tried it with adept, and got the same error, 2 of those sites sort of 'time out'

---

### Post by ipaidforthisname on 2006-01-04
I am getting the same there here. It wasn't happening yesterday. It's happening on all my Ubuntu and Kubuntu machines. I think the repository is down. If it doesn't fix itself, you could disable those mirrors in your sources.list. 

```

Get:11 http://public.planetmirror.com breezy/free Packages
99% [11 Packages bzip2 0] [Waiting for headers]                     24.7kB/s 0sbzip2: (stdin) is not a bzip2 file.
Err http://public.planetmirror.com breezy/free Packages
  Sub-process bzip2 returned an error code (2)
Get:12 http://public.planetmirror.com breezy/non-free Packages
99% [Working]                                                       24.7kB/s 0sbzip2: (stdin) is not a bzip2 file.
Err http://public.planetmirror.com breezy/non-free Packages
  Sub-process bzip2 returned an error code (2)
Fetched 172kB in 7s (23.1kB/s)
Failed to fetch http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz  Sub-process bzip2 returned an error code (2)
Failed to fetch http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
W: GPG error: http://public.planetmirror.com breezy Release: Unknown error executing gpgv
W: Couldn't stat source package list http://public.planetmirror.com breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://public.planetmirror.com breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
G
```

---

### Post by JamesNorris on 2006-01-05
If it's a sudden thing, then it is likely there is a problem with the repo. I'd just comment it out of your sources.list and keep trying it again until it works...

---

### Post by taseal on 2006-01-05
how do i comment it out out of my sources? (never touched it, dnt even know where it is)

still happening btw...

whats at those addresses anyways?

---

