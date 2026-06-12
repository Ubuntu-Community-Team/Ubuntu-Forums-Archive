---
title: "error on apt-get update"
date: 2009-06-14
forum: General Help
---

### Post by blur xc on 2009-06-14
I get this error-
```

W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2ED6BB6042C24D89
```

Any clues on what it means and/or how I can fix it?  I think it may have something to do w/ medibuntu.  I'm trying to be able to watch a dvd in totem, and it's not working; says I might not have permission or something...

thanks,
BM

---

### Post by fooman on 2009-06-14
you need to add the GPG key for a repository that you have added (yeah,  perhaps its medibuntu)....so open a terminal (applications > accessories > terminal)...and type or copy/paste the following into it:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 42C24D89
```see if that fixes it.

---

### Post by camper365 on 2009-06-14
It's not an error, it's a warning. I get that problem too when I use that (but then again I'm running Karmic and there isn't a Karmic repository there yet).
You can still use that repo just like any other, but you may have to deal with that message every time. What you can do is edit your sources.list file (/etc/apt/sources.list) and comment out the line for ppa.launchpad.net and run apt-get update. Every so often uncomment it and run apt-get update so that you get security updates (and other updates) or if you want to install a program that's there.

---

### Post by blur xc on 2009-06-14
> **fooman said:**
> you need to add the GPG key for a repository that you have added (yeah,  perhaps its medibuntu)....so open a terminal (applications > accessories > terminal)...and type or copy/paste the following into it:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 42C24D89
```see if that fixes it.

yay!  It *appears* as if that fixed it...  I'll get back to what I was doing see if I can get these DVDs to play...

BM

---

### Post by fooman on 2009-06-14
> **camper365 said:**
> It's not an error, it's a warning. I get that problem too when I use that (but then again I'm running Karmic and there isn't a Karmic repository there yet).
You can still use that repo just like any other, but you may have to deal with that message every time. What you can do is edit your sources.list file (/etc/apt/sources.list) and comment out the line for ppa.launchpad.net and run apt-get update. Every so often uncomment it and run apt-get update so that you get security updates (and other updates) or if you want to install a program that's there.

no need to comment/uncomment entries in /etc/apt/sources.list....when you see a GPG error as was posted by Barna Madau,  all that should be needed to do is import the key that it is referring to.

what you do is take the last 8 characters of the missing key (in this case the missing key it names is "2ED6BB6042C24D89",  so the last 8 characters are "42C24D89") and add them to the end of this command:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com
```which results in this:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 42C24D89
```

running that command should import the missing key and fix the error warning.

---

