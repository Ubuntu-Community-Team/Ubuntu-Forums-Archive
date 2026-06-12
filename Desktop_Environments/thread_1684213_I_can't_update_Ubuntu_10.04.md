---
title: "I can't update Ubuntu 10.04"
date: 2011-02-08
forum: Desktop Environments
---

### Post by penn919 on 2011-02-08
Every time I try to update Ubuntu via the Update manager, I get the following error messages.

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2019EA84E7532C8

W: Failed to fetch [http://deb.opera.com/opera/dists/stable/Release](http://deb.opera.com/opera/dists/stable/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

I already tried sudo apt-get update:

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://deb.opera.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2019EA84E7532C8

W: Failed to fetch http://deb.opera.com/opera/dists/stable/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

sudo apt-get upgrade

```
Err http://deb.opera.com/opera/ stable/non-free opera 11.00.1176
  404  Not Found
Failed to fetch http://deb.opera.com/opera/pool/non-free/o/opera/opera_11.00.1176_i386.deb  404  Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

and sudo apt-get upgrade --fix-missing

```
Err http://deb.opera.com/opera/ stable/non-free opera 11.00.1176
  404  Not Found
Failed to fetch http://deb.opera.com/opera/pool/non-free/o/opera/opera_11.00.1176_i386.deb  404  Not Found
```

I also tried changing my software sources server from United States to Main Server, but it didn't make any difference.

What do you guys think is wrong?

---

### Post by TBABill on 2011-02-08
Probably just a missing key. Can you ```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
``` This information came from [http://deb.opera.com/](http://deb.opera.com/) if you want to see it. Or you can check [https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

---

### Post by Frogs Hair on 2011-02-08
Hi,
For one Opera has upgraded to 11.01 and the key for the version 11.00.1176 has expired and a new key was issued for 11.01.

Go to the website and install the current version via the.deb package and you should get a new key. Remove the old key from your source list.

---

### Post by penn919 on 2011-02-09
Frogs Hair's post seems to have solved the problem. Once I removed the Opera key from the source list I was able to successfully update ubuntu. I thought that Ubuntu would've automatically updated the Opera browser, so I never paid attention to the versions. However, I'm still curious why it prevented the rest of the programs from being updated. 

I have another Ubuntu desktop at my office that's been experiencing the same problem. It also has opera installed, so it's a safe bet the solution will be the same.

I'll remove the opera key source on it tomorrow, and report back the results.

---

### Post by penn919 on 2011-02-10
Alright I just finished updating my office desktop and everything went fine. 

Thanks for the help!

---

