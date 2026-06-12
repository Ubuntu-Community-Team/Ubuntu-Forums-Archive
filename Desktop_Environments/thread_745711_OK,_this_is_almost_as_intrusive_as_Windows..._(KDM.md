---
title: "OK, this is almost as intrusive as Windows... (KDM on KDE4)"
date: 2008-04-04
forum: Desktop Environments
---

### Post by eternicode on 2008-04-04
Or whatever program insists that you use it over its older versions :rolleyes:

Last night I reinstalled Kubuntu Gutsy, then reinstalled all the various programs I use on a regular basis, including kde4.  I executed "sudo aptitude install kde4", and it installed all sorts of whatever-kde4 programs.  I've figured out that it later added /usr/lib/kde4/bin and /usr/lib/kde4/bin/ to the *beginning* of my PATH variable.  And all the bins in that directory have the same name as the "whatever/kde3" apps in /usr/bin, so it essentially forces me to use the "new and improved" apps. (I've found that moving the kde4 bin from whatever to whatever-kde4 and then symlinking the kde3 app from the kde4 folder lets me launch the old apps normally, however inelegant it may be.  I've only tried this with KMix so far [kmix-kde4 doesn't support the Dell media buttons!!], and it seems to work).

Unfortunately, this includes, to an annoying degree, KDM.  I want to use kdm (the old version), but it insists that I use kdm-kde4.  I tried running "sudo dpkg-reconfigure kdm" and choosing kdm instead of kdm-kde4 as the default, but it seems that the "same name game" tricks the system into loading kdm-kde4 no matter what I want.  I figure I can do the same rename-and-symlink trick, but I'm not sure what unexpected side effects that might have.  I think I could also move the offending Paths to the end of my PATH variable, but, since I'm not perfectly confident on how that whole thing works, I'm not too sure.

Any advice is appreciated :)

---

### Post by sardion on 2008-04-13
So first things first: I would file a bug report on this one using launchpad (there are many threads about how to do that).  If KDE4 really wants to supplant KDE3 then it should not allow to keep 3 installed.  But really what you are trying to do should work fine.

It is almost as bad as windows, but then not really at all...

The best thing to do is to edit the file startkde (there will be one for kde3 and one for kde4), do

locate startkde | grep bin

to find them.  Edit the one for KDE3 and add the following line at the top:

PATH="/path/to/kde3:${PATH}"
export PATH

This will make it so that when you start a kde3 session, the kde3 apps are found first.

---

