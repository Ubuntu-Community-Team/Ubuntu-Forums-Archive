---
title: "update-manager not prompting for authorisation, won't install updates"
date: 2012-09-05
forum: Desktop Environments
---

### Post by steveferson on 2012-09-05
Not sure why this is happening but I did a fresh install of Lubuntu 12.04 the other day, and for some reason update-manager seems to be broken.

I get messages flashing up telling me there are updates available and listing them out, as expected.  But when I hit install nothing happens - no prompt for authorisation.

The system looks like it's thinking about doing something for a second or two but then just goes back to its original state, still showing the same list of updates to be done.

If I go to the command line and
```
sudo update-manager
```
then the updates are applied fine (without the authorisation prompt, obviously).

Has anyone else had this?  It's hardly a show-stopper but seems odd.  I'm fairly sure the Lubuntu VM I set up earlier today didn't feature this, but the only significant difference I can think of is that I'm accessing this one via Remote Desktop, surely that's not it?

---

### Post by irv on 2012-09-05
> **steveferson said:**
> Not sure why this is happening but I did a fresh install of Lubuntu 12.04 the other day, and for some reason update-manager seems to be broken.

I get messages flashing up telling me there are updates available and listing them out, as expected.  But when I hit install nothing happens - no prompt for authorisation.

The system looks like it's thinking about doing something for a second or two but then just goes back to its original state, still showing the same list of updates to be done.

If I go to the command line and
```
sudo update-manager
```
then the updates are applied fine (without the authorisation prompt, obviously).

Has anyone else had this?  It's hardly a show-stopper but seems odd.  I'm fairly sure the Lubuntu VM I set up earlier today didn't feature this, but the only significant difference I can think of is that I'm accessing this one via Remote Desktop, surely that's not it?
You may want to go to the packagae manager and try doing a reinsatall on the update-manager. It would be a good place to start.

As a side note. Your discription of your OS says 7.10 in the side bar  maybe you should update it to 12.04.

---

### Post by marinara on 2012-09-06
please file a bug, someone has to

---

### Post by Epodx64 on 2012-09-07
Try running "sudo apt-get update && sudo apt-get upgrade" from a terminal there may be a new fixed version of the update manager already there.

---

