---
title: "Intrepid~ can anyone tell me how to fix the update problem?"
date: 2009-05-08
forum: General Help
---

### Post by KEE on 2009-05-08
ok so I removed the flashplugin nonfree last night, booted my computer this morning and the updater was missing now that got it (thanked the person ywho helped me) ```
sudo apt-get install update-manager 
``` so I get this as an error window =S ```
W: GPG error: http://packages.medibuntu.org intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: http://wine.budgetdedicated.com intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
<close>
```

---

### Post by plucky on 2009-05-08
Add the GPG keys.From a terminal

For Medibuntu ```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
For Wine ```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

Good Luck

---

### Post by KEE on 2009-05-08
> **plucky said:**
> Add the GPG keys.From a terminal

For Medibuntu ```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
For Wine ```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

Good Luck
hey thanks =) I get this at the bottom though ```
Fetched 390B in 2s (184B/s)
Reading package lists... Done
W: GPG error: http://wine.budgetdedicated.com intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems
me@me-desktop:~$ wget -q http://wine.budgetdedicated.com/apt/387ee263.gpg -o- | sudo apt-key add -
gpg: no valid OpenPGP data found.
me@me-desktop:~$ wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
OK
me@me-desktop:~$ sudo apt-get add- wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
E: Command line option 'O' [from -O-] is not known.
gpg: no valid OpenPGP data found.
me@me-desktop:~$ 

``` any ideas? thank so much by the way

---

### Post by kostkon on 2009-05-08
It seems that you have added the Wine key successfully, try now to give a
```
sudo apt-get update
```
in a terminal and see if you will get any warnings.

---

### Post by darkstaar on 2009-05-08
> **KEE said:**
> hey thanks =) I get this at the bottom though...any ideas? thank so much by the way

Yes. That server is often overloaded. It's that busy. Keep trying. You'll get it eventually.

--Leisa

---

