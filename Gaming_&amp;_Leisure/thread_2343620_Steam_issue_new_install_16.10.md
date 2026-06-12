---
title: "Steam issue new install 16.10"
date: 2016-11-17
forum: Gaming &amp; Leisure
---

### Post by Disposition96 on 2016-11-17
New to linux, have gotten as far as this but can't seem to figure out the next step or the issue pertaining to why it wont work.

```
~$ sudo apt update && sudo apt install steam
[sudo] password for jory: 
Ign:1 http://ppa.launchpad.net/jfi/ppa/ubuntu yakkety InRelease
Hit:2 http://ca.archive.ubuntu.com/ubuntu yakkety InRelease         
Hit:3 http://archive.canonical.com/ubuntu yakkety InRelease         
Get:4 http://security.ubuntu.com/ubuntu yakkety-security InRelease [93.3 kB]
Err:5 http://ppa.launchpad.net/jfi/ppa/ubuntu yakkety Release                  
  404  Not Found
Get:6 http://ca.archive.ubuntu.com/ubuntu yakkety-updates InRelease [94.5 kB]  
Hit:7 http://ca.archive.ubuntu.com/ubuntu yakkety-backports InRelease
Reading package lists... Done
E: The repository 'http://ppa.launchpad.net/jfi/ppa/ubuntu yakkety Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

---

### Post by howefield on 2016-11-17
There is no yakkety repository for [http://ppa.launchpad.net/jfi/ppa/ubuntu](http://ppa.launchpad.net/jfi/ppa/ubuntu), you are querying a non existent repository.

Remove the files pointing to that repository from /etc/apt/sources.list.d/

If you are not sure how to do that, post the output of the terminal command..

```
ls /etc/apt/sources.list.d/
```

---

### Post by Disposition96 on 2016-11-17
I didn't know how to do that, I appreciate your help. :)


~$ ls /etc/apt/sources.list.d/
jfi-ubuntu-ppa-yakkety.list  jfi-ubuntu-ppa-yakkety.list.save

---

### Post by howefield on 2016-11-17
```
sudo rm /etc/apt/sources.list.d/jfi-ubuntu-ppa-yakkety.list*
```

Then try your update and install commands again.

---

### Post by Disposition96 on 2016-11-17
Worked perfect, thank you sir. :)  What does what you all did do exactly?

---

### Post by howefield on 2016-11-17
Well, it is more a matter of what you did.

By putting a file in /etc/apt/sources.list.d/ pointing to a non existent repository ensured that apt threw it hands in the air complaining that it couldn't find it, unsurprisingly enough. All you did was remove the erroneous files to keep apt happy.

---

### Post by Disposition96 on 2016-11-17
Ah ok, so why did it put a file there to begin with?   I would have thought that the commands people would give would be for new setups so everyone could do it easily.  Or was it I didn't setup my new unit properly?

---

### Post by howefield on 2016-11-17
You added a PPA (Personal Package Archive) to your system, presumably to get the psensor package ?

---

### Post by Disposition96 on 2016-11-17
Ah ok, I just copy and pasted things, so how do I make sure that doesn't happen again, or does it just happen with every new app and you have to revert it?

---

### Post by howefield on 2016-11-18
> **Disposition96 said:**
> Ah ok, I just copy and pasted things, so how do I make sure that doesn't happen again, or does it just happen with every new app and you have to revert it?

You, I, or anyone else can create a PPA (Personal Package Archive) and stick anything in it, so there is an inherent risk in using them either because someone is acting with malice or decides to stop maintaining the PPA for any of a number of reasons, in this case had you been on any release other than Yakkety you would have been fine because that particular repository supports up to Xenial. 

The "*does not have a Release file.*" was the clue in your error that there was no Yakkety repository. To check this, you can go to the PPA launchpad page

```
https://launchpad.net/~jfi/+archive/ubuntu/ppa
```

Click in the *Overview of published packages > Published in:* drop down field and you won't see a Yakkety entry, so no point using it in a Yakkety installation ;)

There are ways around it by using eg, the Xenial option but it is seldom a good idea to mix repositories like that, it is likely to end up badly down the line but technically possible to do.

Most of the time using PPAs are a good way of getting software that isn't available in the official repositories and you won't encounter any problems but just remember that you are opening the door of your system to any Tom, **** or Harry ;)

---

### Post by Disposition96 on 2016-11-23
Thanks a lot fo your help. :)

---

