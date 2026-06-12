---
title: "Debian 3CX running on xfce host:  Lightdm not launching"
date: 2020-02-02
forum: Desktop Environments
---

### Post by Jonners59 on 2020-02-02
I am running Debian with 3CX on a xfce host, using virtualbox.  The guest machine is the problem here.

The Debian did an update and then rebooted, but unfortunately after reboot it only opens in a cmd line, I think it is called headless, happy to be corrected, I'm just trying to be smart.

I have done a lot of searches but found nothing that has worked to get the desktop back.  I am not very good at cmd, only knowing a few bits no bobs, so whilst the machine is working as it should I can not get in to do any maintenance or whatever.  I feel uncomfortable with it in this state.  It should be running STRETCH (Debian 9), but I see it is running EOAN ????

Can anyone help me get it back.  AN additional issue is that the repositories and licenses seem to also be a mess,  When I do try solutions and add apps or make changes ```
sudo apt-get install xxx
``` or```
 sudo apt-get autoremove
```, or ```
update
```, etc, all throw up lists of errors.  This is also not helping.
 
Can anyone assist me, please.  Screenshot attached.

---

### Post by guiverc on 2020-02-02
Debian names are based on Toy Story characters (releases after the Toy Story movie anyway; no names were given for releases pre-movie). So Stretch is a version of debian.

Ubuntu names however are a word + animal; eoan (fully it's eoan ermine) is a recent release name of Ubuntu, so the connection between a debian release name and a Ubuntu release name shouldn't occur in the way you describe, so your description is missing key bits I suspect.

You mention debian 3CX (I have no idea what 3CX is) on a XFCE host (XFCE is a desktop, not an OS), where normally one refers to a host OS - so this is probably related.

It may help if you
[LIST]
[*] define 3CX,
[*] is 'debian' a VM or virtual-machine running on a host?
[*]if you have host & guest OS, what OS is the host running (it maybe the ubuntu or the 'eoan' if 'stretch' is the vm), and what OS is the virtual machine (VM)
[*] and to which does XFCE (a desktop) belong?
[/LIST]

FYI: headless means no screen is attached (eg. racks of machines; that maybe running desktops/GUI though usually aren't for maximum efficiency).

---

### Post by Jonners59 on 2020-02-02
> **guiverc said:**
> Debian names are based on Toy Story characters (releases after the Toy Story movie anyway; no names were given for releases pre-movie). So Stretch is a version of debian.

Ubuntu names however are a word + animal; eoan (fully it's eoan ermine) is a recent release name of Ubuntu, so the connection between a debian release name and a Ubuntu release name shouldn't occur in the way you describe, so your description is missing key bits I suspect.  Thank you.  Didn't know that.
 
> **guiverc said:**
> You mention debian 3CX (I have no idea what 3CX is) on a XFCE host (XFCE is a desktop, not an OS), where normally one refers to a host OS - so this is probably related.

It may help if you 
[LIST]
[*] define 3CX,
[/LIST]
Is an IP-PBX, or IP based  telephone system/PBX.  It has historically been a Windows based system but a year of so ago they launched, thankfully, a Debian based.  They only work on Debian and  only on STRETCH


> **guiverc said:**
> 

[LIST]
[*]is 'debian' a VM or virtual-machine running on a host?
[/LIST]
The Debian 3CX is a virtual machine, a GUEST, running on a HOST machine


> **guiverc said:**
> 


[LIST]
[*]if you have host & guest OS, what OS is the host running (it maybe the ubuntu or the 'eoan' if 'stretch' is the vm), and what OS is the virtual machine (VM)
[/LIST]
 
 So if I have this correctly the HOST is XFCE and the GUEST/Virtual Machine is DEBIAN EOAN, but SHOULD be STRETCH    


> **guiverc said:**
>  

[LIST]
[*] and to which does XFCE (a desktop) belong?
[/LIST]
As above, it is the HOST machine



Sorry, I have not made this clear....  Does this answer your questions correctly?  The HOST is fine and working OK, it is ONLY the GUEST machine I have the problems with.  I suspect, based on what you have said, when the Lightdm stopped working after the Debian upgraded to STRETCH, all the messing about I did upgraded it somehow to EOAN.  EOAN is not supported for 3CX, though from experience of similar scenarios does not necessarily say it wouldn't work perfectly well, it is just not supported and may raise an eyebrow or two. 

> **guiverc said:**
> FYI: headless means no screen is attached (eg. racks of machines; that maybe running desktops/GUI though usually aren't for maximum efficiency).  Thank you, excellent for correcting me.  Teach me for trying to be a smart ****.  :-D

---

### Post by guiverc on 2020-02-02
Ubuntu 19.10 is Eoan Ermine.

Debian and Eoan do NOT relate to each other as they are different Operating Systems; there is no Toy Story character named Eoan (*it's not a noun anyway*). You can look up [https://wiki.debian.org/DebianReleases](https://wiki.debian.org/DebianReleases) for the list of Debian names (Buzz, Rex, Bo, Hamm, Slink, Potato, Woody, Sarge, Etch, Lenny, Squeeze, Wheezy, Jessie, Stretch, Buster, Bullseye.. and there is **no** crossover between debian names & ubuntu names).

Stretch is a valid debian release; also called Debian 9 (or debian *old-stable; stable is always the latest released version, old-stable the preceding version, old-old-stable the LTS or **preceding*..)

Hosts are OSes like Ubuntu or Debian, or many other OS (operating systems).

XFCE is a desktop (a graphical user interface or GUI) and is not an OS so cannot be a host.  It can run on a host yes, but can also run on a client. Debian can use XFCE, as Ubuntu can use XFCE.   Ubuntu with XFCE is normally called Xubuntu, though many people still call it Ubuntu with XFCE (or XFCE on Ubuntu). XFCE is only a user interface for an OS (be it debian, ubuntu, opensuse or something else)

3CX is very clear, thank you.

I suspect Ubuntu is your host OS, and debian is your client/guest OS, and possibly XFCE runs on one or both of them (it's just a user-interface so can run on both), but details need to be clear in order to help.

---

### Post by Jonners59 on 2020-02-02
> **guiverc said:**
> Ubuntu 19.10 is Eoan Ermine.

Debian and Eoan do NOT relate .. and there is **no** crossover between debian names & ubuntu names).

Stretch is a valid debian release; also called Debian 9 
Debian 9 STRETCH makes sense.  That is where it should be.  So, how did I manage to get from Debian STRETCH to Ubuntu EOAN and how do I reverse it?

  
> **guiverc said:**
> I suspect Ubuntu is your host OS, and debian is your client/guest OS, and possibly XFCE runs on one or both of them (it's just a user-interface so can run on both), but details need to be clear in order to help.
Yes, that makes sense, bar the GUEST/Debian, I do not recall if the GUEST is XFCE as it has no desktop to view anymore, or could that be the problem, not Lightdm?

---

### Post by Jonners59 on 2020-02-02
OK, so I cheated.  I saved current state on the snapshot view of the vBox and then restarted using the original snapshot.  That put me back to a working STRETCH and desktop/lightdm.

That said, I do not know how I had got myself in to the mess, so not learned not what to do nor how to correct it properly and I still have a lot of errors coming up when i ```
sudo apt-get update
```.

Here are the errors:
[HTML]p.leaders{max-width:18cm;padding:0;overflow-x:hidden;line-height:120%}p.leaders:after{float:left;width:0;white-space:nowrap;content:". . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . "}p.leaders span:first-child{padding-right:0.33em;background:white}p.leaders span+span{float:right;padding-left:0.33em;background:white;position:relative;z-index:1}        @page { size: 21cm 29.7cm; margin: 2cm }        p { margin-bottom: 0.25cm; line-height: 115%; background: transparent }        a:link { color: #000080; so-language: zxx; text-decoration: underline }    Ign:1http://ftp.uk.debian.org/debian stretch InRelease
Get:2http://downloads-global.3cx.com/downloads/debian stretch-testingInRelease [8,917 B]
Hit:3http://ftp.uk.debian.org/debian stretch-updates InRelease                                           
Get:4http://downloads-global.3cx.com/downloads/debian stretch InRelease[8,890 B]                        
Hit:5http://security.debian.org/debian-security stretch/updates InRelease                               
Hit:6http://ftp.uk.debian.org/debian stretch Release                    
Ign:2http://downloads-global.3cx.com/downloads/debian stretch-testingInRelease
Ign:4http://downloads-global.3cx.com/downloads/debian stretch InRelease
Fetched17.8 kB in 1s (16.8 kB/s)
Readingpackage lists... Done
W:http://downloads-global.3cx.com/downloads/debian/dists/stretch-testing/InRelease:The key(s) in the keyring /etc/apt/trusted.gpg are ignored as thefile is not readable by user '_apt' executing apt-key.
W:GPG error: http://downloads-global.3cx.com/downloads/debianstretch-testing InRelease: The following signatures couldn't beverified because the public key is not available: NO_PUBKEYD34B9BFD90503A6B
W:The repository 'http://downloads-global.3cx.com/downloads/debianstretch-testing InRelease' is not signed.
N:Data from such a repository can't be authenticated and is thereforepotentially dangerous to use.
N:See apt-secure(8) manpage for repository creation and userconfiguration details.  
W:http://ftp.uk.debian.org/debian/dists/stretch-updates/InRelease: Thekey(s) in the keyring /etc/apt/trusted.gpg are ignored as the file isnot readable by user '_apt' executing apt-key.
W:http://downloads-global.3cx.com/downloads/debian/dists/stretch/InRelease:The key(s) in the keyring /etc/apt/trusted.gpg are ignored as thefile is not readable by user '_apt' executing apt-key.
W:GPG error: http://downloads-global.3cx.com/downloads/debian stretchInRelease: The following signatures couldn't be verified because thepublic key is not available: NO_PUBKEY D34B9BFD90503A6B
W:The repository 'http://downloads-global.3cx.com/downloads/debianstretch InRelease' is not signed. 
N:Data from such a repository can't be authenticated and is thereforepotentially dangerous to use.
N:See apt-secure(8) manpage for repository creation and userconfiguration details.
W:http://security.debian.org/debian-security/dists/stretch/updates/InRelease:The key(s) in the keyring /etc/apt/trusted.gpg are ignored as thefile is not readable by user '_apt' executing apt-key.
W:http://ftp.uk.debian.org/debian/dists/stretch/Release.gpg: The key(s)in the keyring /etc/apt/trusted.gpg are ignored as the file is notreadable by user '_apt' executing apt-key.

[/HTML]

Any ideas for a fix, please?

---

### Post by Jonners59 on 2020-02-04
OK, as my machine was in a VM I could just simply revert to an old snapshot to restore.  Then delete the old current one.  Needed to manually adjust the clock and date.

The next issue was simply fixed with

```
sudo mv /etc/apt/trusted.gpg /etc/apt/trusted.gpg.orig
```

---

