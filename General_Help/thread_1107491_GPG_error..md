---
title: "GPG error."
date: 2009-03-26
forum: General Help
---

### Post by OsakaWilson on 2009-03-26
I've been getting the following error. Does anyone know what I need to do to fix this? I put the full text below.

----------------------------

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.


GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch [http://apt.boxee.tv/dists/intrepid/main/binary-amd64/Packages.gz](http://apt.boxee.tv/dists/intrepid/main/binary-amd64/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by sefs on 2009-03-26
Looks like you are missing the public key in synaptic/apt

This is the fingerprint (or whatever you call it) for the key 58403026387EE263GPG.

You will need installed on your machine gnupg and seahorse.  To do the next things.

First retrieve the key by going

```

gpg --keyserver subkeys.pgp.net --recv 58403026387EE263GPG

```

That will put where seahorse can access it... open seahorse ... UBUNTU MENU -> Accessories -> Password & Encryption keys

go to the "Other collected keys" tab and look for a key with mediabuntu in it...thats the first missing key i think and right click on it and export it to the desktop

You must then repeat the process from the top for 2EBC26B60C5A2783 ... and that looks like the boxee signing key.


So now you have both keys in two files on the desktop you can go into synaptic to the settings -> repositories.  Click on the authentication tab and use the "import key files" button to import both keys from the desktop.

Then try to install what you were trying to install again.  You should get further along unless you need to fetch more keys.

---

### Post by OsakaWilson on 2009-03-26
I checked in Synaptic and I have Seahorse and gnupg. So I put in the code <gpg --keyserver subkeys.pgp.net --recv 58403026387EE263GPG> into the command line, I assume that is what I was supposed to do.I got the following reply:

gpg: "58403026387EE263GPG" not a key ID: skipping

Edit: OK. Realized that the GPG at the end of the code was a run-on into the next statement and not part of the code, I tried it and it is working. Continuing...

---

### Post by OsakaWilson on 2009-03-26
Success!! Thank you very much.

---

