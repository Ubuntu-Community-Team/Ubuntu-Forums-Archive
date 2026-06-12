---
title: "Where did the m4a plugin go?"
date: 2006-01-08
forum: Desktop Environments
---

### Post by shade11 on 2006-01-08
I have downloaded the m4a support for XMMS. I converted it into a deb file and then installed it. I then tried to play an m4a file in XMMS but it didnt work. It just went to the add files to the libary menu. I tried adding m4a files there but it just showed the mp3 files there. I then aftrward looked in the plugins menu for Audio I/O. It wasnt there. I looked in synaptic and it said that it was installed.

So what is going on?

---

### Post by kairu0 on 2006-01-08
The problem is likely one of two things:

1. The plugin got put in the wrong directory. Go in Synaptic, find that plugin, and open its details to find out where it installed the plugin. Then, open the details for the xmms package and find out where its plugin directory is.

2. Version mismatch. The plugin is for a different version of XMMS. Since you converted the package to a deb package, the new deb package has no way of knowing what version of XMMS is required.

---

### Post by shade11 on 2006-01-08
Yes I think it is a wrong version. I looked in the plugins folder. So I will see if there is a newer version.

---

### Post by skralljt on 2007-07-03
Hey I had the problem of not being able to play m4a files in xmms, and my solution was to roll back from libfaad2.5 from some third party repo to the ubuntu repo's libfaad2-0.  It uninstalled aacgain but a small price to pay to here music I paid good money for in Itunes!

---

