---
title: "K3b in Debian won't rip to FLAC"
date: 2008-01-25
forum: Debian
---

### Post by maybeway36 on 2008-01-25
I am using Debian lenny with all packages up-to-date. In K3b I can rip CDs, but it only gives me the options of MP3, Ogg Vorbis, or WAV. I want to rip this particular song to FLAC, however. libflac++6 and libflac8 are both installed.

---

### Post by kellemes on 2008-01-26
Yeah, I heard of some k3b version(s?) not being compiled with Flac-support for some reason..

Maybe you need to install some other flac package to get the support? The package "flac" maybe?
Give it a try, maybe it works..

---

### Post by DMK62 on 2008-01-26
On Kubuntu 7.10 I added 2 packages Flac and k3b2-extracodecs. Not sure on how that would apply to debian but check esp for the extracodecs package for k3b. Before adding those I only had the 3 formats as you have encountered and after that Flac was listed.

hth 

Dale

---

