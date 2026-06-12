---
title: "apt-get keeps trying to install a failed E17 installation"
date: 2009-04-02
forum: General Help
---

### Post by ste.richards on 2009-04-02
I tried to install E17 a few days ago but it was trying to reach a URL which was returning an error of > svn: Server sent unexpected return value (400 Bad Request) in response to REPORT request for '/svn/e/!svn/vcc/default'

And still it can't reach that URL. This now affects trying to install anything because as soon as I run 'apt-get install <package>' it tries to first install E17. I've removed the source from /etc/apt/sources.list and ran 'apt-get update' but it still wants to install E17, even if I run 'apt-get remove e17'.

Can somebody give me a pointer please.

Thanks in advance, Ste

---

### Post by VCoolio on 2009-04-02
Maybe stupid because you already thought of that and it's too simple, but do you have (e17) packages marked for installation in synaptic and can you remove these markings? Btw, if you want to install enlightenment I recommend [this]("http://ubuntuforums.org/showthread.php?t=916690&highlight=howto+install+enlightenment") howto.

---

### Post by ste.richards on 2009-04-02
That's worked, thanks.

I haven't used the GUI for synaptic before so I was unaware about marking packages.

Thanks again,

---

