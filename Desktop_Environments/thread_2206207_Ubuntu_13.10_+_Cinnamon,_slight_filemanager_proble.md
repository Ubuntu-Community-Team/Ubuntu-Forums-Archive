---
title: "Ubuntu 13.10 + Cinnamon, slight filemanager problems."
date: 2014-02-17
forum: Desktop Environments
---

### Post by konsolkongen-o on 2014-02-17
Hi running Ubuntu 13.10 64bit with the Cinnamon desktop. The file manager used was nemo which worked alright, but I wanted to try nautilus instead, so I removed nemo. Unfortunately this didn't work so well, as nautilus doesn't autostart when i boot up the computer. I have to manually launch nautilus. Not the smartest idea to remove nemo, but I assumed that nautilus would automatically kick in and replace it :) 

I thought I could just reinstall nemo should anything happen, but that turned out not to be the case :(

So a couple of questions. First of I would like to reinstall nemo just in case I want to go back to the defaults. But when I try to install nemo from the terminal it says:

```
sudo apt-get install nemo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nemo : Depends: nemo-data (= 1.8.4-1) but 2.0.0-20131011010206-raring is to be installed
        Recommends: nemo-fileroller but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

And how would I make nautilus the default filemanager in Cinnamon should I end up liking that better? Prior to removing nemo, I found a suggestion that you had to edit the /usr/share/applications/defaults.list but when I looked there, nautilus was already listed as the only filemanager in the text file, no mention of nemo at all. And at that time nemo was already the default filemanager and worked fine. Perhaps I was looking in the wrong file?

---

