---
title: "errors while trying to update"
date: 2009-03-08
forum: General Help
---

### Post by hunterkasy on 2009-03-08
I have installed Ubuntu and I was in the process of doing all of the updates, not all updated, when I went to the add/remove I got this message:

failed to check for installed and available applications

this is a major failure of your software management system. please check for broken package with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt -get update' and 'sudo apt -get install _f'


when I went to the synaptic manager and looked for broken packages it was with firefox, no matter what I try to do with the firefox packages I get this:


An error occurred

the following details are provided


E:/var/cache/apt/archives/firefox-3.0_3.0.7 + nobinonly - 0ubuntu0.8.10.1_i286.deb: corrupted file system tarfile - corrupted package archive


What can I do to fix this? and remember I am a noob with linux
Edit/Delete Message

---

### Post by taurus on 2009-03-08
First, close down synaptic package manager.  Then, open a terminal and clear out the cache.  Now, see if you can upgrade your machine.

Applications -> Accessories -> Terminal
```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by hunterkasy on 2009-03-08
I did what you said and everything is working now thanks

---

