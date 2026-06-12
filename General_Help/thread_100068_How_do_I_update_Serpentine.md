---
title: "How do I update Serpentine?"
date: 2005-12-06
forum: General Help
---

### Post by autonomy on 2005-12-06
:?:

---

### Post by carlosqueso on 2005-12-06
I believe the new serpentine is in the backports repo.  Make sure it is enabled (uncomment the breezy-backports in your /etc/apt/sources.list)
Type ```
sudo apt-get update
``` and ```
sudo apt-get upgrade
``` and all of your programs that aren't up to date will be.

---

### Post by autonomy on 2005-12-06
:???: I don't know how to uncomment backports. thanks though

---

### Post by funkydan2 on 2005-12-06
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by autonomy on 2005-12-07
Alright, now, you're not even the same lingo. I've already enabled Universe and Multiverse Repositories. Am I supposed to enable Outside Repositories?

---

### Post by carlosqueso on 2005-12-07
Grr...I'm not at home...so these instructions may be a little off...but here's what I think you have to do.

1. Open a terminal
2. Type ```
sudo gedit /etc/apt/sources.list
```
3. A window should open with a bunch of text.
4. Find the following lines in the file: ```
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse
``` They may have a country code before them (ie "us.archive.ubuntu.com".  If there is and it's "us", delete it because the us mirrors are awful.
5.  Uncomment those lines (remove the "#" before them).  If the lines are not there, copy them from here and paste. 

Hope this helps and I haven't screwed up, I have no way to check since I'm at work and have to use Winders.

---

### Post by autonomy on 2005-12-07
OK, I did that and your first reply, and it seems to be working.

---

### Post by carlosqueso on 2005-12-07
w00t! Always glad to help a fellow North Carolinian :-D

---

### Post by funkydan2 on 2005-12-07
Sorry about that.  With a new install of Breezy, the backports entry is already in your sources.list, just commented out.  Thus you can enable backports easily through synaptic.  If you've upgraded from Hoary however, that entry won't already be in there and you'll have to add it manually, like you've done.

---

### Post by autonomy on 2005-12-11
Maybe we can pull off a North Carolina [Ubuntu Local Community Team]("https://wiki.ubuntu.com/LoCoTeams")!

---

