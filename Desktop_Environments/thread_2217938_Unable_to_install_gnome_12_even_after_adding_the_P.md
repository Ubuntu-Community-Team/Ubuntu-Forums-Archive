---
title: "Unable to install gnome 12 even after adding the PPA"
date: 2014-04-19
forum: Desktop Environments
---

### Post by drofart on 2014-04-19
Hello guys,

        I recently installed trusty on my pc. As Gnome 3.12 is not officially available so i added the PPA
[HTML]sudo add-apt-repository ppa:gnome3-team/gnome3
 Before upgrading your system to a new Ubuntu release (i.e. from Ubuntu 13.04 to 13.10), you should probably run ppa-purge ppa:gnome3-team/gnome3 first.

*** You need to run 'sudo apt-get dist-upgrade' to avoid problems. ***
Please read the output before entering 'Y' to make sure important packages won't be removed.

=== Ubuntu 14.04 (Trusty) ===
GNOME 3.12 that didn't made it into the normal Ubuntu 14.04 repositories.
Also a staging area of 3.10 packages for the official Ubuntu repo.

=== Ubuntu 13.10 (Saucy) ===
GNOME 3.10 that didn't made it into the normal Ubuntu 13.10 repositories.

=== Ubuntu 13.04 (Raring) ===
GNOME 3.8 that didn't made it into the normal Ubuntu 13.04 repositories. Other parts of GNOME 3.8 are available in the https://launchpad.net/~gnome3-team/+archive/gnome3-staging PPA but beware that many of those components have known regressions from their GNOME 3.6 versions.

=== Ubuntu 12.10 (Quantal) ===
Parts of GNOME 3.6 that didn't make it into the normal Ubuntu 12.10 repositories.

=== Ubuntu 12.04 (Precise) ===
Parts of GNOME 3.4 that didn't make it into the normal Ubuntu 12.04 repositories.

=== Bugs ===
On Saucy (13.10) and newer please use 'ubuntu-bug' to report bugs against packages in this PPA
 More info: https://launchpad.net/~gnome3-team/+archive/gnome3
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmp8bd4hm38/secring.gpg' created
gpg: keyring `/tmp/tmp8bd4hm38/pubring.gpg' created
gpg: requesting key 3B1510FD from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp8bd4hm38/trustdb.gpg: trustdb created
gpg: key 3B1510FD: public key "Launchpad PPA for GNOME3 Team" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK

[/HTML]

And also did an update but still i am not able to upgrade gnome 3.10 to 3.12

Any idea?

---

### Post by keithy on 2014-04-19
Hi

3.12 is not in the stable PPA yet

If you're feeling brave you can add the staging PPA!

[https://wiki.ubuntu.com/UbuntuGNOME/Developers](https://wiki.ubuntu.com/UbuntuGNOME/Developers)

good luck

---

