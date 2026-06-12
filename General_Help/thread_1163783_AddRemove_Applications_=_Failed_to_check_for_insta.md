---
title: "Add/Remove Applications = Failed to check for installed and available applications"
date: 2009-05-19
forum: General Help
---

### Post by hexilum on 2009-05-19
Whenever I try to access the Add/Remove application, I encounter this error:

```
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
```

I've tried the recommended terminal commands with no ado:
```
'sudo apt-get update' and 'sudo apt-get install -f'.
```

I've also tried clearing my cache and upgrading like recommended on another forum I found through google.
```

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

Nothing seems to work. Can someone who resolved this issue in Ubuntu 9.04 help me? Thank you.

---

### Post by lisati on 2009-05-19
What about this one:????
```
sudo dpkg --configure -a
```

---

### Post by hexilum on 2009-05-19
Still doesn't work :(

---

### Post by hexilum on 2009-05-19
This worked for me. 
[img]http://i44.tinypic.com/fusxgg.jpg[/img]

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Whenever I tried using 'sudo apt-get update' it would always bring up this at the end:

```
W: GPG error: http://packages.medibuntu.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783 
```

I looked up the solution, and found the fix. Thanks for the help.

---

