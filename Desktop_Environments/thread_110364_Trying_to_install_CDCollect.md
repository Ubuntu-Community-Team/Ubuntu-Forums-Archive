---
title: "Trying to install CDCollect"
date: 2005-12-30
forum: Desktop Environments
---

### Post by Maelgwyn on 2005-12-30
I've downloaded the .deb for CDCollect, and then I went

```
 sudo dpkg --install cdcollect_0.5.1_i386.deb
``` 
and I get this error:

```

(Reading database ... 108196 files and directories currently installed.)
Preparing to replace cdcollect 0.5.1 (using cdcollect_0.5.1_i386.deb) ...
/var/lib/dpkg/info/cdcollect.prerm: line 5: /usr/sbin/gconf-schemas: No such file or directory
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
dpkg: ... it looks like that went OK.
Unpacking replacement cdcollect ...
Setting up cdcollect (0.5.1) ...
/var/lib/dpkg/info/cdcollect.postinst: line 10: /usr/sbin/gconf-schemas: No such file or directory
dpkg: error processing cdcollect (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cdcollect

```

The weird thing is that it appears to have been installed and I can open it through the Applications->Other menu!

---

### Post by timfrost on 2005-12-30
I would guess that the package was built for debian, not Ubuntu.  The fact that it installed indicates that the library versions and dependencies are met successfully.

Where did you get the .deb from?

---

### Post by Zwack on 2005-12-30
It was trying to modify a file /usr/sbin/gconf-schemas that doesn't exist on your system.  It apparently doesn't need that file, so you're safe enough using it.

Z.

---

### Post by Maelgwyn on 2005-12-30
it came from [Softpedia](http://linux.softpedia.com/progDownload/CDCollect-Download-3889.html)

---

### Post by MetalMusicAddict on 2005-12-30
I installed the .5.1 deb just fine from [Sourceforge]("http://sourceforge.net/project/showfiles.php?group_id=119228").

I use the script from [HERE]("http://www.ubuntuforums.org/showthread.php?t=33584&highlight=install+.debs").

---

### Post by ryu kun on 2006-10-20
I tried to compile CdCollect but after many hours couldn't success..

Then I tried to install the debian package but Package Installer gives me an error:

```
Error: Dependency is not satisfiable: libgconf2.0-cil
```

I've checked in Synaptic that it is installed. I've reinstalled but no avail.

Any ideas?

---

### Post by MyNameUhBorat on 2006-11-03
Ya I got the same error as you ryu kun and still haven't been able to fix it. Hopefully bumping it up will get us some much needed help.

---

### Post by jrh on 2006-11-24
There is a new version 0.6.0 that just has been released. There is also an ubuntu edgy package for it. You can try to download it [here]("http://sourceforge.net/project/showfiles.php?group_id=119228&package_id=130496&release_id=466268")

Hope it works for you.

---

### Post by Julz_ET on 2006-12-03
Hmm, I'm also trying to install this program, to no avail, are there any similar alternatives out there?

Thanks

---

### Post by jrh on 2006-12-03
> **Julz_ET said:**
> Hmm, I'm also trying to install this program, to no avail, are there any similar alternatives out there?

Thanks

Have you tried the 0.6.0 version? what kind of problems are you experiencing?

---

### Post by Julz_ET on 2006-12-03
Thanks for the quick reply, I tried 0.60 deb from sourceforge, but it was complaining about missing dependency (mono-runtime). I have got F-spot and Banshee installed on this system, thought they would have installed mono requirements, but anyway found **gwhere** in synaptic, does exactly what I wanted.

Thanks

---

### Post by jrh on 2006-12-03
> **Julz_ET said:**
> Thanks for the quick reply, I tried 0.60 deb from sourceforge, but it was complaining about missing dependency (mono-runtime). I have got F-spot and Banshee installed on this system, thought they would have installed mono requirements, but anyway found **gwhere** in synaptic, does exactly what I wanted.

Thanks

Glad you found something useful, and yep, cdcollect requires the package mono-runtime (you can find it in synaptic) to run.

later,

---

