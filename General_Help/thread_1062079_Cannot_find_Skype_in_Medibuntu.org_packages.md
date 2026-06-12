---
title: "Cannot find Skype in Medibuntu.org packages"
date: 2009-02-06
forum: General Help
---

### Post by arepaking on 2009-02-06
Hello,
I am running a 64bit Ubuntu 8.10 version. I added the packages.medibuntu.org/non-free PPA and its corresponding gpg key. After reloading the packages I still can't find the Skype installation.

As a side note, I have a 32bit Ubuntu 8.10 version running in another computer and I am able to see the skype package.

How can I see this packages in synaptic on 64bit installation? 

Thanks in advance,
AK

---

### Post by curtlee2002 on 2009-02-07
it doesn't matter that you are using 64bit.  Yes, it is true that skype was built for 32bit.  But Medibuntu has a package for 64bit that depends on 32bit libraries.  

Did you run?:
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

and run:
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by HavocXphere on 2009-02-07
I grabbed it straight off the Skype page. Works fine...but I suspect that it won't auto-update if installed that way.:|

EDIT: curtlee's way is probably the better way to do it.

---

### Post by konqueror7 on 2009-02-07
also, you could try using [**ubuntutweak**]("http://ubuntu-tweak.com/") if you want some partner/3rd party software and other tweaks...

---

### Post by arepaking on 2009-02-07
All,
Thank you very much for all of your replies. This issue seems to be a bug within synaptic. For more information please visit the launchpad website: [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/281898](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/281898)

Now, the way that worked for me was executing the following command:

```
sudo update-apt-xapian-index
```

This command updated my package list and afterwords I was able to see the Skype package using the Quick search feature.

Kind Regards,
AK

---

