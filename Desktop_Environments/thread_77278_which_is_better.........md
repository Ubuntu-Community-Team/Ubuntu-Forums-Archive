---
title: "which is better........"
date: 2005-10-16
forum: Desktop Environments
---

### Post by EsunMC on 2005-10-16
Which  is better 5.10 or 5.04.  I have  the 5.04 ver. of ubuntu .If 5.10 is better how do i get for free and do i have to chnage the os im using now?
[FONT="Comic Sans MS"][COLOR="black"][COLOR="Blue"][SIZE="3"]****[/SIZE][/COLOR][/COLOR][/FONT]

---

### Post by audax321 on 2005-10-16
In my opinion, 5.10 is better. The new Gnome feels crisper and looks better. However, if you are using 5.04 right now and it works for you, it is up to you if you want to upgrade. 5.04 will continue to be supported for some time still.

Now, if you want to upgrade all you have to do is:

1.  sudo gedit /etc/apt/sources.list

When the file opens up, comment out any lines that contain unofficial Ubuntu repositories by placing # in front of them.

2.  Change all references of hoary in the repository list to breezy

3.  Save the file and exit.

4.  sudo apt-get update

This will update your list of sources in apg-get.

5.  sudo apt-get dist-upgrade

This will upgrade you from 5.04 to 5.10.

That said, this is at your own risk, although I've never had a problem upgrading like this before. So, make sure you backup before you try this.

Also, if you need clarification on any of this, check this out (it says it's for breezy experimental, but it's just outdated... same steps though): [http://www.ubuntuguide.org/#upgradehoarytobreezy](http://www.ubuntuguide.org/#upgradehoarytobreezy)


If you'd like to download a CD, get them from [www.ubuntulinux.org](www.ubuntulinux.org) (you can even order pressed CDs from here as well for free).

---

