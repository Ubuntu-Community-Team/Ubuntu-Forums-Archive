---
title: "[SOLVED] import key file button crashes software sources"
date: 2008-12-04
forum: General Help
---

### Post by GeorgeSmiley on 2008-12-04
Hi,

New user Ubuntu 8.04LTS, generally favorable. Configured as a dual boot with Windows XP using separate disks for each OS. Struggled with getting Big Desktop to work with my ATI 9800 Pro, but after one sleepless night, finally got it working.

Lots of help in forums from expert users.

Ok, the problem. I want to use Wine but need to add an authentication key in Software Sources. For reference, the Ubuntu download page for Wine is at

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

The link to the key file is given on this same web page for Ubuntu users (Scott Ritchie's key). Ok so far.

Now when I go to my Software Sources App under the Authentication tab and hit the import key file button, it crashes the Software Sources GUI. Tried it multiple times after rebooting etc with the same result.

I found only one user reporting a similar problem. The GUI problem was not solved but some code was provided as a work-around.

I tried the suggested work around code in a terminal window as follows:

sudo wget -q -O - [http://wine.budgetdedicated.com/apt/Scott%20Ritchie.gpg](http://wine.budgetdedicated.com/apt/Scott%20Ritchie.gpg) | sudo apt-key add -

apt-get update

The only change I made to the suggested code was to substitute the web address I needed to the Scott Ritchie key.

I get the following error message 

gpg: no valid OpenPGP data found.

Don't know what that means.If you go to the link you can see the software key.

Anybody have any ideas on a work-around or how to solve the GUI problem?

---

### Post by GeorgeSmiley on 2008-12-05
Ok, found the solution.

It was a simple terminal command.

After downloading the key file to ScottRitchie.gpg just enter the terminal command

sudo apt-key add ~/Desktop/ScottRitchie.gpg

Nice thing about Ubuntu/Linux is workarounds if the GUI's don't do it.

---

