---
title: "Update GPG keys"
date: 2009-01-21
forum: General Help
---

### Post by gimfred on 2009-01-21
In searching for the gpg key to get rid of the dreaded "... public key is not available: NO_PUBKEY..." error, I found that, **after all these years of searching for the specific key**, I could have been easily adding the key! Thanks Robert Di Gioia who wrote this solution at [https://answers.launchpad.net/ubuntu/+question/20586](https://answers.launchpad.net/ubuntu/+question/20586).

> run apt-get in a terminal again. it will likely say something like:

The following signatures couldn't be verified because the public key is not available: NO_PUBKEY <a bunch of numbers>

then type the following in the terminal, substituting the actual string of numbers received in the error messge above for <a bunch of numbers>

gpg --recv-keys <a bunch of numbers>

gpg --export <a bunch of numbers> | sudo apt-key add -

sudo apt-get update

when the system asks for a password, enter your user password. the system will not show what you type in, that is ok, just press enter after you've typed your password in.

hope this helps.

---

