---
title: "No sessions in GDM"
date: 2010-01-02
forum: Desktop Environments
---

### Post by decomp on 2010-01-02
Hi all, 

GDM has no session options listed when I click on my username. I should have openbox and lxde. I read that GDM finds it's sessions from /usr/share/xsessions so I checked there and I have desktop files for both. currently I'm using WDM and it's working fine.

Any ideas? :confused:

---

### Post by XubuRoxMySox on 2010-01-02
On your Login screen there's a little bitty button (in the lower left corner if I remember it correctly - that's where it was in Jaunty's login screen anyway) labeled "Options." Click on it and select "Session." Both of your sessions should appear and you can select one, and/or choose one as default if you wish.

-Robin

---

### Post by decomp on 2010-01-02
> **dixiedancer said:**
> On your Login screen there's a little bitty button (in the lower left corner if I remember it correctly - that's where it was in Jaunty's login screen anyway) labeled "Options." Click on it and select "Session." Both of your sessions should appear and you can select one, and/or choose one as default if you wish.

-Robin

Right. That's what should happen. But when I click on the 'little bitty button' there are no choices - it's blank. That's my problem. Thanks for making sure it's not user error though! Best place to start troubleshooting. :)

---

### Post by decomp on 2010-01-03
Anyone?

---

### Post by decomp on 2010-01-06
still can't find a solution to this :(

---

### Post by zenbound on 2010-12-08
Sorry to necro-post, but I had this same problem and after some digging figured out a solution. This happened to me after I "removed" gnome from my machine via synaptic and had added xfce/xubuntu as a .desktop. unfortunately, after i restarted gdm, it had an empty session box and just kept looping back to "click your user name to login". dmesg had a cryptic "access denied" error (that I've since fixed so I can't reproduce at this time sorry) about the /usr/share/gdm/guest-session/Xsession

Long story short, installing gnome3 back on my machine as a desktop session fixed my session box and automatic login via gdm. hope this helps someone!

---

