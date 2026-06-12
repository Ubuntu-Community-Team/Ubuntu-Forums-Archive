---
title: "wubi Installs Ubuntu but I have no Internet"
date: 2009-01-13
forum: General Help
---

### Post by UNME on 2009-01-13
Hi All,


I have decided to try this Linux distro.

I wanted to install Ubuntu on windows using Wubi but I have no Internet with me.

I got ISO files and Wubi downloaded and placed them in same folder (In machine with no Internet) ..... 

But wubi tries to connect to Internet and after three attempts it fails to install.

Am I missing something?

Thank you :KS

---

### Post by Gen. Lee poor on 2009-01-14
Do you mean that Windows is not connected to the internet when you run the installer? I'm not 100% sure, but I had a feeling that Wubi needs to connect during the installation to do some checksum on the image.

---

### Post by UNME on 2009-01-14
Yeah, windows machine is not connected to Internet.

So we have no solution for this?

I thought wubi connects to Internet to download ISO file but then if file is present in same folder where wubi.exe is present, it should Install.

---

### Post by brandon88tube on 2009-01-14
Do you have to correct wubi.exe?

---

### Post by UNME on 2009-01-14
I did following two things:

1)Downloaded the wubi.exe from the website (The link for this was in wiki - Ubuntu) and also ISO file (wiki has link for this as well)

2)I downloaded ISO file burned it with MagicISO into some folder extracted wubi.exe and tried using it.

Both were trying to connect to INTERNET, I will try adding snapshots here.

I know there is some basic mistake from my side but not getting it.

---

### Post by azmo35 on 2009-01-14
Hi but burn iso to a folder!!> I downloaded ISO file burned it with MagicISO into some folder i think is something not right, but never mind check this to places [here]("http://wubi-installer.org/") and [here]("http://www.ubuntu.com/getubuntu/download") put the two togheder [iso and exe] in the same folder on that machine without internet.

---

### Post by brandon88tube on 2009-01-14
May I ask what version of Ubuntu you downloaded and are trying to install?

---

### Post by UNME on 2009-01-15
Thank you all.
This problem is solved.

_Description of why problem was occurring:_

I kept ISO file and the Wubi.exe in a server so when I was running wubi.exe from client connected to server (having Ethernet attached)... wubi was looking for Internet Path for the ISO file ....

It is how it should work (It is expected behavior)

_What I did to solve it:_

1)Copied ISO and wubi on local machine 
2)Unplugged the Ethernet
3)Started the installation

There was no flow break after that 

Thank you team .. :guitar:

---

