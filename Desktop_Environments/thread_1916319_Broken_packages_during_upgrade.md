---
title: "Broken packages during upgrade"
date: 2012-01-27
forum: Desktop Environments
---

### Post by cespinal on 2012-01-27
Hi guys... I was updating amarok and for some reason muon froze. 

I am now left with no amarok and unable to install it: 

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 amarok : Depends: amarok-common (= 2:2.5.0-0ubuntu4~oneiric1~ppa1) but 2:2.5.0-0ubuntu1~ppa1 is to be installed
E: Unable to correct problems, you have held broken packages.

```

I have tried clean, -f and similar commands to no avail.... 

any hints??? :( this was going soooo good....

---

### Post by manvvip on 2012-01-27
I had updated the packet manager today (Synaptic)
And it asked me to remove Amarok????? (No Way)

Am waiting to try updating later on in the day to see if this is resolved.

Output:

TO BE REMOVED:
amarok will be removed (Existing ver. 2:2.5.0-0ubuntu1~ppa1)
                       (Latest ver. 2:2.5.0-0ubuntu4~oneiric1~ppa1)

TO BE UPGRADED:
amarok-utils (version 2:2.5.0-0ubuntu1~ppa1) will be upgraded to version 2:2.5.0-0ubuntu4~oneiric1~ppa1
plymouth-theme-kubuntu-logo (version 1:11.10ubuntu4) will be upgraded to version 1:11.10ubuntu4.1~oneiric1~ppa1

Help

---

### Post by Frogs Hair on 2012-01-27
This can happen if a package has been withheld or is corrupted . I have found that is best to wait and keep checking for updates .

---

### Post by manvvip on 2012-01-28
The repository's been cleared up now, you can try again now.

This occasionally happens

Alls working fine now, just update and upgrade as normal.

---

### Post by cespinal on 2012-01-28
I can confirm is working now... Thanks for the update!!

---

