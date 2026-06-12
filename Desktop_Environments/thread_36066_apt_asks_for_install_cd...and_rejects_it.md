---
title: "apt asks for install cd...and rejects it"
date: 2005-05-21
forum: Desktop Environments
---

### Post by Samer on 2005-05-21
I just installed Kubuntu from the live+install DVD.  I opened up bash to install firefox, and it forces me to pop in the install disk instead of just going to the network.  Is this a simple matter of editing the apt repositories?  If it is, how do I do that without synaptic?  (I get the same error when installing that.)  

> samer@porky:~$ sudo apt-get install mozilla-firefox
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  [blah blah blah]
Suggested packages:
  [blah blah blah]
Recommended packages:
  [blah blah blah]
The following NEW packages will be installed:
  [blah blah blah]
0 upgraded, 26 newly installed, 0 to remove and 3 not upgraded.
26 not fully installed or removed.
Need to get 0B/19.1MB of archives.
After unpacking 75.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
[b]Media change: please insert the disc labeled
 'Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)'
in the drive '/cdrom/' and press enter[/b]
<enter>
[b]Media change: please insert the disc labeled
 'Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)'
in the drive '/cdrom/' and press enter[/b]

Thanks,
-Samer

---

### Post by f.prisson on 2005-05-21
You have to edit your /etc/apt/sources.list for telling apt where to get new programs. Type ```
sudo vi /etc/apt/sources.list
``` and comment out the first entry ```
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted
``` like that.

---

### Post by dbooth27 on 2005-05-27
I am getting a very similar response when I try to install Ubuntu on my G3 mac tower.  Can I comment out the similar line and get the install to continue?

---

### Post by reinibaerli on 2005-05-27
I fixed it a different way. It seems that the line with the path to the cdrom is wrong. There is a program called apt-cdrom that helps you by telling what to write into /etc/apt/sources.list.
```
sudo apt-cdrom add
``` 

in its output it shows you the right entry to put into /etc/apt/sources.list

```
Benutze CD-ROM-Einhängpunkt /cdrom/
Hänge CD-ROM aus
Warte auf CD...
Please insert a Disc in the drive and press enter
Hänge CD-ROM ein...
Identifiziere... [96e0570eb362af6d901aa7492ab3a5bb-2]
Suche auf CD nach Index-Dateien...
Fand 2 Paketindexe, 0 Quellenindexe und 1 Signaturen
Diese CD heißt jetzt:
»Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)«
Kopiere Paketlisten...gpgv: Signature made Don 07 Apr 2005 08:18:12 CEST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Fertig
Schreibe neue Quellliste
Quelllisteneinträge für diese CD sind:
deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted
Hänge CD-ROM aus...Repeat this process for the rest of the CDs in your set.
``` 

so I did not comment the deb cdrom.... line in sources.list out but replaced it with the output of apt-cdrom which in my case is

```
deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted
```

Then I could use the cd again for updating.


[QUOTE=f.prisson]You have to edit your /etc/apt/sources.list for telling apt where to get new programs. Type ```
sudo vi /etc/apt/sources.list
``` and comment out the first entry ```
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted
``` like that.[/QUOTE]

---

### Post by E_K on 2007-10-03
just installed xubuntu 7.04 on a real old system and was getting annoyed by the same problem, though sometimes it would accept the cd, it was just annoying because i knew it wasn't needed

Thanks

---

