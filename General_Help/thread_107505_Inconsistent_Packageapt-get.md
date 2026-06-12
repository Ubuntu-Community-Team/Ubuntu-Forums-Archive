---
title: "Inconsistent Package/apt-get"
date: 2005-12-23
forum: General Help
---

### Post by linuxbtdsc on 2005-12-23
All,

I am having an issue with one of our Ubuntu 5.10 desktops and apt-get. A
recently installed program, Rosegarden 4, was removed from the computer.
However, it left a damaged package, lilypond-data, behind and I can't
uninstall it. It keeps saying it is damaged, inconsistent and that I
need run dpkg --configure -a which I do and still it doesn't fix the
inconsistency. I then try apt-get remove lilypond-data and that doesn't
seem to work either. I've used the -f and -m switches with apt-get also
to try and remove the package with no luck. I've tried --purge with dpkg which didn't solve anything either. I've even gone through Synaptic without any luck. Because of this problem package I am unable to do any updates on the computer and I can't install/remove anymore programs. Anyone have any ideas? Thanks in advance.

-linuxbtdsc

---

### Post by darth_vector on 2005-12-23
have you tried

sudo apt-get remove --purge packagename

??

---

### Post by linuxbtdsc on 2005-12-23
I just tried apt-get remove --purge lilypond-data and received the following:

dpkg: error processing lilypond-data (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
root@ubuntu:/home/paul# Errors were encountered while processing:
 lilypond-data

And yes, I have tried to reinstall the package and it won't let me. I get the following error when I try to reinstall the package:

Unpacking replacement lilypond-data ...
/var/lib/dpkg/info/lilypond-data.postrm: line 23: /usr/bin/kpsewhich: is a directory
dpkg: warning - old post-removal script returned error exit status 126
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 23: /usr/bin/kpsewhich: is a directory
dpkg: error processing /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 126
/var/lib/dpkg/tmp.ci/postrm: line 23: /usr/bin/kpsewhich: is a directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 126
Errors were encountered while processing:
 /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by linuxbtdsc on 2005-12-23
Found the fix:

[http://www.ubuntuforums.org/showthread.php?t=95656&highlight=lilypond-data](http://www.ubuntuforums.org/showthread.php?t=95656&highlight=lilypond-data)

Thanks

---

