---
title: "DELL 1535  w / Ubuntu - Update Problem - DELL Warning"
date: 2009-04-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Starfield on 2009-04-04
Hello,

I recently purchased a laptop from Dell:

Model: Dell Studio 1535
Purchase date: Mar, 2009 (approx)
** Preloaded at factory with UBUNTU 8.04 **


The Problem:

The " UPDATE " button is shown down in the tool bar as expected (new machine).  I clicked on it, and after some downloading took place, a dialog box was displayed that said that Ubuntu could not "authenticate" some of the updates.

I called DELL, and **DELL support told me NOT to hit the "update" button on the tool bar**.  **They said that this has caused machines to _crash_**.  They told me to update through DELL instead.  I went to DELL, and I can't find their section where I can update Ubuntu.  I searched around for awhile and I could not find any links or explanations.  It is either buried or my search foo is weak.  Furthermore, I went to DELL - Product Support - Drivers and Downloads, and entered in my Service Tag number, and it only displayed updates for VISTA (cough - cough), which is obviously wrong.

This all seems very odd to me.

Questions:

1) Does anyone know where I can update my laptop through DELL to get future security fixes, etc.?

2) Are there any other recommended methods for updating the DELL OEM version of Ubuntu with future security fixes, etc., without my Dell machine going on the rocks?

Thanks for the help, and I have enjoyed reading everyone's posts here.

Take care.**[B]**[/B]****

---

### Post by armandh on 2009-04-04
I dumpted dell's 8.04 from my mini9 and I am much happier with OOTB Ubuntu 8.10

besides avoiding dells 'bloat ware for linux' I get an OS that works with the real Ubuntu repositories.

with other dell hardware YMMV.

---

### Post by anjilslaire on 2009-04-04
Agreed.
Also, I've purchased and installed regular 8.04 on 2 Dell 1420 laptops as well. FLawless performance.

---

### Post by novafluxx on 2009-04-04
Dell makes their images available for download [not including LinDVD] on their Linux wiki.

I'm not sure why the update button crashes anything.

As previously stated, the standard Ubuntu will run fine on your system

---

### Post by superm1 on 2009-04-05
> **Starfield said:**
> Hello,

I recently purchased a laptop from Dell:

Model: Dell Studio 1535
Purchase date: Mar, 2009 (approx)
** Preloaded at factory with UBUNTU 8.04 **


The Problem:

The " UPDATE " button is shown down in the tool bar as expected (new machine).  I clicked on it, and after some downloading took place, a dialog box was displayed that said that Ubuntu could not "authenticate" some of the updates.

I called DELL, and **DELL support told me NOT to hit the "update" button on the tool bar**.  **They said that this has caused machines to _crash_**.  They told me to update through DELL instead.  I went to DELL, and I can't find their section where I can update Ubuntu.  I searched around for awhile and I could not find any links or explanations.  It is either buried or my search foo is weak.  Furthermore, I went to DELL - Product Support - Drivers and Downloads, and entered in my Service Tag number, and it only displayed updates for VISTA (cough - cough), which is obviously wrong.

This all seems very odd to me.

Questions:

1) Does anyone know where I can update my laptop through DELL to get future security fixes, etc.?

2) Are there any other recommended methods for updating the DELL OEM version of Ubuntu with future security fixes, etc., without my Dell machine going on the rocks?

Thanks for the help, and I have enjoyed reading everyone's posts here.

Take care.
This is because the PPA system added authentication after the factory image was created.  You can install this package (from the Dell PPA) to get around the issue:

[https://launchpad.net/%7Edell-team/+archive/ppa/+files/dell-team-keyring_2009.02.11~hardy1_all.deb](https://launchpad.net/%7Edell-team/+archive/ppa/+files/dell-team-keyring_2009.02.11~hardy1_all.deb)

It adds the PPA's keyring to your keyring database.

---

