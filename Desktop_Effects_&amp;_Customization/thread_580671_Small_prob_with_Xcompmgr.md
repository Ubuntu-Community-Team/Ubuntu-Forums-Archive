---
title: "Small prob with Xcompmgr"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by Ominae on 2007-10-19
hi there

i had to install xcompmgr to get kiba doc workin right now i have a small problem 
when i click the power button on the bar the window pops up but is now invisible
i know this becouse i was randomly clickin on the screen as it seemed the screen
was locked an then the laptop restarted..

now bein a compleet newb with Ubuntu i have no idear what this is could any one help

---

### Post by FuturePilot on 2007-10-19
That's a bug in Xcompmgr
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/80343]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/80343")
If it happens just press Esc and it will get everything "unfrozen" again. Right now there's no real workaround for it other than killing xcompmgr before logging out or disable the logout dialog, but then when you press Quit you just get logged out.

---

### Post by Ominae on 2007-10-19
okay sso how do i get the off button to be just that an off button an bypass the logg off screen or can i even

---

### Post by NoWhereMan on 2007-10-23
news! news! xcompmgr now DOES work!!

```

apt-get build-dep xcompmgr 
apt-get install git-core
git clone git://anongit.freedesktop.org/git/xorg/app/xcompmgr
cd xcompmgr
./autogen.sh
make
sudo fakeroot checkinstall # to have a debian package installed :D

```

btw I'm attaching the checkinstall package (I wasn't able to do the package the right way)

more info on the bug page

---

### Post by Neo4 on 2007-12-23
i've done all but when I try: sudo fakeroot checkinstall

i have this error:

/usr/bin/fakeroot: 166: checkinstall: not found

but it worked :D

thanks a lot! :D

---

### Post by NoWhereMan on 2007-12-24
sudo apt-get install fakeroot checkinstall

---

