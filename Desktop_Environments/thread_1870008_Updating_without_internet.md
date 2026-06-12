---
title: "Updating without internet"
date: 2011-10-26
forum: Desktop Environments
---

### Post by linuxonbute on 2011-10-26
We have a friend who does not have internet access. She was having problems with her Windows installation and it was so badly corrupted it needed a re-install but she did not have the disk so i showed her my laptop with ubuntu 10.04 on it and she thought it was great. i have installed it for her and she is getting on fine with it. She has a large family who visit her often and some are beginning to talk about trying ubuntu.  i would like to be able to update the software on her PC - NOT upgrade to 10.10 or under any circumstances to go to 11.04 or 11.10 - so can I pull down updates, burn them to Cd and then update her system? 
If so how would I go about it?
tia
Norman
Any ideas please?

---

### Post by linuxonbute on 2011-10-28
Still looking for ideas. Anyone got any?

---

### Post by newbie-user on 2011-10-28
Well, you could take her computer to somewhere else that has internet access.

Otherwise, you'd have to manually download all update deb files for her computer from a repository, save them to cd or usb, then load them onto her computer.  If all the deb files are in one place, then simply navigating to the location in the terminal, then typing dpkg -i *.deb will install all the deb files.

Another possibility would be to bring an existing 10.04 repository server to her location (assuming you have one set up) and then update her computer from that repository.

If at all possible, tell her to sign up for internet access.  :)

---

### Post by JustinR on 2011-10-28
[apt-offline]("http://manpages.ubuntu.com/manpages/oneiric/man8/apt-offline.8.html")

---

