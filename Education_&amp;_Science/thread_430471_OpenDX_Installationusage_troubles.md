---
title: "OpenDX Installation/usage troubles"
date: 2007-05-02
forum: Education &amp; Science
---

### Post by xwipeoutx on 2007-05-02
Hey all,

I've been trying to work on OpenDX using my ubuntu installation (instead of my windows one with an x server), and I'm having some issues.

Firstly, the dx 4.4.0 package from the repos runs properly and everything, there's just a few bugs that I can't work out:
1) Any annotations I add are replaced by "Double click here to add annotation" on saving.  Existing file annotations are loaded properly, but save as blank
2) The tabs are insanely small

I've attached screenshots for these

I was hoping the 4.4.4 release fixed these bugs but there's no .deb anywhere that i can find for it, so i used alien to convert the RPM. While running alien, I go this warning several times, but ignored it:
warning: dx-4.4.4-2.fc6.i386.rpm: Header V3 DSA signature: NOKEY, key ID 1ac70ce6

When trying to run dx, after installing the .deb (i had to remove a few other packages like libdx4), i get this error:
steve@steve-laptop:~/downloads/dx$ dx
/usr/lib/dx/bin_linux/startupui: error while loading shared libraries: libtiff.so.3: cannot open shared object file: No such file or directory

I gathered that was a problem with the fact that it was an rpm build for FC6, so I've rolled back to 4.4.0 which is still usable, but very very annoying because of those bugs mentioned earlier - mainly the annotation one, being a uni subject, they drill me for commenting...

Anyone have any ideas on either getting 4.4.4 working on ubuntu 7.04, or fixing the annotation issue? I can't find any info anywhere...

---

