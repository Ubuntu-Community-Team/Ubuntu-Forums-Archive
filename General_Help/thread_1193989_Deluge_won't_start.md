---
title: "Deluge won't start"
date: 2009-06-22
forum: General Help
---

### Post by pappfer on 2009-06-22
Hi!

Deluge just won't start for me for a couple of days now. It was working fine before. I'm not sure if it was an upgrade or what which caused the error. I've searched a lot about it and I found a lot of info why Deluge wouldn't start but none was helping for me, it all seemed to be a different issue that's why I created this topic.

I'm using Deluge 1.1.9 from Deluge's repository and a full updated Ubuntu Jaunty.

The error message I get:
```
Traceback (most recent call last):
  File "/usr/bin/deluge", line 5, in <module>
    from pkg_resources import load_entry_point
  File "/usr/lib/python2.6/dist-packages/pkg_resources.py", line 2562, in <module>
    working_set.require(__requires__)
  File "/usr/lib/python2.6/dist-packages/pkg_resources.py", line 626, in require
    needed = self.resolve(parse_requirements(requirements))
  File "/usr/lib/python2.6/dist-packages/pkg_resources.py", line 524, in resolve
    raise DistributionNotFound(req)  # XXX put more info here
pkg_resources.DistributionNotFound: deluge==1.1.9

```

When I try apt-get -f install it tells me that there are dependency errors with Deluge.

---

### Post by Johnny B on 2009-06-22
can you install the dependencies? do you know what they are?

---

### Post by pappfer on 2009-06-22
> **Johnny B said:**
> can you install the dependencies? do you know what they are?
All dependencies are installed that's why I don't know what's the problem.

---

### Post by Johnny B on 2009-06-22
hmm.. go to /home/username/.config/deluge and check deluged.log

---

### Post by pappfer on 2009-06-22
> **Johnny B said:**
> hmm.. go to /home/username/.config/deluge and check deluged.log
The file is empty.

---

### Post by Johnny B on 2009-06-22
try to run deluge again and see if it updates that file with an error message.
i've fixed this problem more than once, but i need more to go on here, any more error messages anywhere?

---

### Post by pappfer on 2009-06-22
> **Johnny B said:**
> try to run deluge again and see if it updates that file with an error message.
i've fixed this problem more than once, but i need more to go on here, any more error messages anywhere?
The file stays empty.

I also get some Deluge-related error messages on Synaptic whenever I try to install / uninstall any package. The message says dependency errors.

Thanks for your willing to help!

---

### Post by Johnny B on 2009-06-22
what does the message say exactly?

---

### Post by pappfer on 2009-06-22
> **Johnny B said:**
> what does the message say exactly?
Error in Synaptic: [http://pappfer.se-portal.hu/temp/deluge-error-synaptic.png](http://pappfer.se-portal.hu/temp/deluge-error-synaptic.png)
deluge-core: Post installation script exited with error code 1
deluge-common, deluge, deluge-torrent: dependency error - the package stayed unconfigured

Error in terminal when trying to execute Deluge:
[http://pappfer.se-portal.hu/temp/deluge-error-terminal.png](http://pappfer.se-portal.hu/temp/deluge-error-terminal.png)

Error in terminal on sudo apt-get -f install:
[http://pappfer.se-portal.hu/temp/deluge-error-terminal-2.png](http://pappfer.se-portal.hu/temp/deluge-error-terminal-2.png)
(it also complains about dependency errors)

---

### Post by Johnny B on 2009-06-22
damn i dont know and i've got to go to work now.

---

### Post by Johnny B on 2009-06-23
> sudo apt-get remove -purge deluge
sudo gedit /etc/apt/sources.list

this is from the [deluge-team-ppa]("https://launchpad.net/~deluge-team/+archive/ppa")
Add this to the bottom of the file and save:
>  deb [http://ppa.launchpad.net/deluge-team/ppa/ubuntu](http://ppa.launchpad.net/deluge-team/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/deluge-team/ppa/ubuntu](http://ppa.launchpad.net/deluge-team/ppa/ubuntu) jaunty main 

Copy this public key:
> -----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXRcxwEEALFsjhB2o+pMvt4NJVlXzXaNjNL83V5RoGBB8C2Lv0epp57W72ixmIT0ehRe
ayvlW1FLN3ShsKBxC2stva9FjcxZ+9xTGkUQRJ7GsS6k8VXodF3aRTJk1a+DJpUWP8kotZiW
pdNCjGPmXe/LT0UUyMd+u9UDbSHIO0LWs7qeA8/LABEBAAG0HUxhdW5jaHBhZCBQUEEgZm9y
IERlbHVnZSBUZWFtiLYEEwECACAFAkl0XMcCGwMGCwkIBwMCBBUCCAMEFgIDAQIeAQIXgAAK
CRDF5qXtJJrSTDAHA/9ODPlwUfYrguSlvEc4Ld89dPqS4iUBZMZV2FaYcSKZ8hBsb9r5PF3c
6D3LQW23n+6kou36mqnSAidGR4JKz5mi30uwiXMH8AgIYu4T6ErRy+x3XoUMr6ZavSFyTMxb
H4pc/FsNiAFtT1y5YSXjAUdsnAqDnMbN/9kq2zHnSJ/Vtg==
=GsAD
-----END PGP PUBLIC KEY BLOCK-----


Paste the public key into a text editor and save it.
Open System->Administration->Software Sources and click the Authentication tab.
Click Import Key File, select the key you saved earlier

then try 
> 
sudo apt-get update
sudo apt-get install deluge

---

### Post by pappfer on 2009-06-24
I already had this PPA and Deluge but it just doesn't work.
I also tried to remove the PPA and reinstall Deluge and it just doesn't make any difference. I also deleted config folder, purged config files, etc...

---

