---
title: "Openoffice 3.1 to 3.0.1 in 8.04 LTS"
date: 2009-05-20
forum: General Help
---

### Post by homersbrain on 2009-05-20
I upgraded my OpenOffice suite from 3.0.1 to 3.1 in 8.04 LTS, and because it keeps losing my work, I want to downgrade it again to 3.0.1. I cannot force version because the official version in 8.04 in OO2.4. (I used the launchpad repos for OO3.0) I don't want to upgrade to U9.04 but I was wondering if I could use the jaunty repos to get OO3.0 back? I cannot believe this can be so difficult! Any help appreciated to get me back to OO 3.0.1!

---

### Post by scouser73 on 2009-05-20
As far as I'm aware in the Jaunty repos it's 3.1.0 now.

---

### Post by homersbrain on 2009-05-22
Oh. Well does anyone know if there are still any repos which hold OO3.0.1? Or even deb files? This is very annoying.

---

### Post by chriskin on 2009-05-22
go here
[http://distribution.openoffice.org/p2p/](http://distribution.openoffice.org/p2p/)

you can get all 3.x from openoffice via torrent , not just the latest one
so , download the .deb for 3.0.1 and install it, after removing the 3.1 one

---

### Post by homersbrain on 2009-05-23
I removed the old OOo and downloaded all the linux x86 deb files (48 of them) and installed them using sudo dpkg -i openoffice*. The new installation appeared to succeed but on execution it would crash every time I opened a document or made a new one making it useless. I think I need the OO tailored to hardy. I wonder if openoffice.org keep an archive of their OS specific versions? If not, why not? Because 3.1 is not stable yet! I'm using 3.0.1 on windows at the moment to get my work done :(. Help!

---

### Post by chriskin on 2009-05-23
you keep on saying that open office 3.1 is not stable enough, did you even think that there might be something wrong with your installation?

i can't think of any other idea, you might find this helpful though
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=openoffice.org](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=openoffice.org)

it is from the ubuntu site, where all packages are.

---

### Post by Kareeser on 2009-05-23
> **homersbrain said:**
> I removed the old OOo and downloaded all the linux x86 deb files (48 of them) and installed them using sudo dpkg -i openoffice*. The new installation appeared to succeed but on execution it would crash every time I opened a document or made a new one making it useless. I think I need the OO tailored to hardy. I wonder if openoffice.org keep an archive of their OS specific versions? If not, why not? Because 3.1 is not stable yet! I'm using 3.0.1 on windows at the moment to get my work done :(. Help!

Remove the old versions:
sudo apt-get purge openoffice*

Remove your settings
rm -rf ~/.openoffice

Reinstall 3.0

It's crashing because of conflicting settings.

---

### Post by homersbrain on 2009-05-23
I tried sudo apt-get purge openoffice* and rm -rf ~/.openoffice and then reinstalling the deb files. However I could no longer get them to reinstall because of dependency problems. I think there must be a special order to installing the 48 deb files. Any ideas?

---

### Post by homersbrain on 2009-05-24
I think I have found a possible solution - to install the windows version of openoffice 3.0.1 in wine. It seems ironic that this is the easiest solution! I just need to find out how to associate odt documents with the wine version.

---

### Post by davarino on 2009-05-27
I am having the same problems with 3.1.0 as homersbrain is.

It seems that some of the answers given here are from people who are missing the comment that the 3.1 is on a **Hardy** installation, not an Intrepid or Jaunty.

**Hardy's latest *official* OO.o is 2.4.1.** Because of this, we Hardy-ites have to grab our upgrades from Launchpad, which seems to have trash-canned the 3.0.1 build they used to host until this month.

It is especially annoying that the 3.1 build on Launchpad has no Help menu. I teach others to use OO.o ... and now I have no help screen. Hell of a way to look user-friendly, eh? 

The suggestion about using the deb files also brings up problems. I've "dpkg -i"'d the 3.0.1 on the OpenOffice.org site (after completely uninstalling the Ubuntu 3.1) and it behaves very poorly. (After all, that's why people have made special Ubuntu builds.)

So, if anyone has a way to get back to 3.0.1, please let us know! Thanks.

---

### Post by davarino on 2009-05-27
This discussion brings up another thought:

The "locking" of releases to certain versions of programs (for example, Hardy is locked to OO.o 2.4.1), altho understandable from at least two points of view, is (IMHO) not realistic for big-gun software like OO.o or Firefox.

Microslop will patch up Windows occasionally for better compatibility (not just security) with popular programs.

I believe it would be reasonable that LTS releases should not be left as orphans 6 months into their life by advances in software. (This happened with Hardy when OO.o went to 3.0) It vitiates the whole concept of long-term-support.

And long term support is supposedly one of the big attractions of Ubuntu.

---

### Post by armageddon08 on 2009-05-27
You can install .debs from Open-office site. I think they keep older versions there.

---

### Post by davarino on 2009-06-02
> **armageddon08 said:**
> You can install .debs from Open-office site. I think they keep older versions there.

True, but they don't really work well on Ubuntu Hardy. (That's why there was a special Ubuntu build.) So we're stuck until someone reposts a Hardy-specific 3.0.1 - which I would think wouldn't be such a big request, but it seems that no one cares to.

---

### Post by prconnor@gmail.com on 2009-06-02
> **Kareeser said:**
> Remove the old versions:
sudo apt-get purge openoffice*

Remove your settings
rm -rf ~/.openoffice

Reinstall 3.0

It's crashing because of conflicting settings.

This fixed my issues.  I was surprised that did not have to reinstall all of my extentions after I did this.  Oh well OpenOffice stopped crashing.

Thanks for your help

---

### Post by fooman on 2009-06-02
> **davarino said:**
> It is especially annoying that the 3.1 build on Launchpad has no Help menu. I teach others to use OO.o ... and now I have no help screen. Hell of a way to look user-friendly, eh? 


i believe this issue has been fixed...have you tried updating recently?  have a look here:

[http://ubuntuforums.org/showthread.php?t=987181](http://ubuntuforums.org/showthread.php?t=987181)

hope it helps.

---

### Post by davarino on 2009-06-08
The issues have been fixed as far as I can tell. Updates now **do** work.

Many thanks to all who helped make it happen.

---

### Post by homersbrain on 2009-06-18
I have applied the updates. Not all the issues have been fixed. The colours in Word tables are still not generated correctly. Metafile objects are still frequently vanishing too! I write a lot of technical documents and use graphs imported from sigmaplot etc - when I save documents in 3.1 as odt I often find that all my graphs have gone! This never happened in 3.0.1. I am therefore currently using 3.0.1 in wine as I cannot find a version of 3.0 that works properly in ubuntu 8.04. Version 3.0 in wine works great and has none of the above problems! Until these bugs have been ironed out, I recommend sticking to 3.0.1 for those users who have to use OLE objects or require copies in Word format. If anyone can point me to a repo which still has 3.0.1 customised for hardy I would be grateful.

---

### Post by LaurenLR on 2010-03-04
Hello Homersbrain
I just wondered if you'd managed to solve your issue of disappearing OLE objects? I moved to 3.1 at the end of Jan (to enable me to open Windows7 docs) and only just realised today that my graphs pasted from Calc to Impress to not appear when opened in a windows environment. Nightmare - unhappy customer. Now trying to revert back to 3.0 but just wondered (before I go thru that) if you'd found any work around or knew anything? Your help would be VERY much appreciated.
Thanks
Lauren

---

