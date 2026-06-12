---
title: "Absolute beginner, lost software libraries"
date: 2006-07-24
forum: Desktop Environments
---

### Post by calvinthomas on 2006-07-24
Ok, i'm an absolute beginner to linux, I have had it installed a day and still don't know how to install except for using the add/remove section. I found out about adding new repositories and added one or at least tried, however it didn't show up in software packages and then when I went to update I got the following error:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences

There is a box below this but it is empty, when going to add/remove I get this error:

Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.

as basic as it may sound, I don't actually know how to do what it says there or if it would help, can anyone tell me how to get back to where I was?

I am running ubuntu on an Acer Ferarri 4000, with an AMD Turion 64Bit processor and prior to this problem it has been running without a problem. Help greatly appreciated

Calv

---

### Post by calvinthomas on 2006-07-24
When going into Synaptic Package Manager I get this error instead if that helps out at all

E: Malformed line 37 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

Calv

---

### Post by calvinthomas on 2006-07-24
Problem solved!

---

### Post by MerZo on 2006-07-24
How did you solve it?

---

### Post by calvinthomas on 2006-07-24
I logged in as root firstofall so I had the ability to edit my files

Then to /etc/apt/sources.list and removed the problem line, in my case line 37 and then saved

Then it worked!

Calv

---

