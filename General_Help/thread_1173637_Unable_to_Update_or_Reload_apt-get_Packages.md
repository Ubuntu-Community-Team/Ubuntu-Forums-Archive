---
title: "Unable to Update or Reload apt-get Packages"
date: 2009-05-29
forum: General Help
---

### Post by andrew.schwartzmeyer on 2009-05-29
As of late, I have been unable to update Ubuntu or reload packages in apt-get. Here is the error message I get:

> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

---

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC66403D8670A035

Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)/dists/jaunty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)/dists/jaunty/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Some index files failed to download, they have been ignored, or old ones used instead.

It is not a connection problem, as it does download all the index files. It just does not verify them. I do not know why it is talking about CD-ROMs, as I am attempting to use the regular update manager to update via internet (obviously). By the way, I get similar error messages when trying to reload packages in the package manager.

It seems to me that the public keys it uses to verify the indexes have gone missing (which is odd); where might I find and add the keys I need? I have looked around, but been unable to locate them.

Thank you very much for your help,

:: AeroSabre

---

### Post by andrew.schwartzmeyer on 2009-05-30
Would anyone know what I could do to fix this? Obviously everything I have tried has thus far failed. I cannot even install new software.

---

### Post by paulchinnz on 2009-05-30
Hi same problem here since 30 May 2009.

---

### Post by Danno2468 on 2009-05-31
I have also had the same identical error since may 1st 09

---

### Post by mercenaryhmster on 2009-05-31
open synaptic, go to add repository, and untick the cd as a source.  then refresh the repositories

---

### Post by Danno2468 on 2009-05-31
I tried something else
sudo gedit /etc/apt/sources.list
 and then I # out the 1st line that looked really close to the error line.
I am not sure if this is the same as that... but it worked too.
But to me in either case it seems like we are just putting tape on engine warning light not really fixing the problem... because after a month of not updating all i had to update was flashplayer and that was it. there should have been more.

---

### Post by paulchinnz on 2009-05-31
+1 Danno2468. The original problem i.e. not being able to update ubuntu remains.

---

### Post by paulchinnz on 2009-06-13
Been getting a few updates randomly periodically including today. Not convinced it's fixed properly yet though because it now says it was last updated 9 days ago.

---

### Post by paulchinnz on 2009-07-10
Been getting what appears to be usual weekly updates last few weeks. Something's still not quite right though: updater still says it hasn't updated for 37 days and counting. Poor noobuntu.

---

### Post by paulchinnz on 2009-10-31
Nothing like an OS upgrade to sort some of these things out... mine seems sorted here with 9.10

---

### Post by soluckytouselinux on 2009-11-23
Hi people. can't update either. I hope a fix comes out soon. other than that a really cool ver.

---

