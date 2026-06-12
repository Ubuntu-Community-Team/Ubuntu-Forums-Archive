---
title: "Kopete warning from Yahoo?  Fixed version for Hardy from KDE 4.3.1"
date: 2009-09-12
forum: Desktop Environments
---

### Post by Cato2 on 2009-09-12
Quite a few Kopete users have been getting Yahoo Admin warnings like this:

*Yahoo! Admin: You are using an older version of Yahoo! Messenger that is no longer supported. Please upgrade by downloading the newest version by going to: [http://messenger.yahoo.com/download.php](http://messenger.yahoo.com/download.php)*

This is because Yahoo has changed their authentication protocol in June, and the Hardy version of Kopete doesn't work with the new protocol.  Eventually Yahoo will phase out the old authentication servers and Kopete users will have to upgrade to KDE 4.3.0 or higher (current release is 4.3.1), which will only become available in Ubuntu Karmic Koala (aka 9.10).

Since I don't want to have to upgrade a few systems using Hardy that use Kopete, I have built a version of Kopete for Hardy, from the KDE 4.3.1 sources.  It includes the fix for this Yahoo warning, because the changes by the Kopete maintainer (see [http://mattr.info:8080/blog/2009/06/24/kopete-and-yahoo/](http://mattr.info:8080/blog/2009/06/24/kopete-and-yahoo/) ) made it into the 4.3.0 release. 

The download is at [http://easyrepairs.org/download/](http://easyrepairs.org/download/) - it's entirely unsupported by me, but maybe it will be useful to a few people.  **It is only for Hardy**, and won't work on Intrepid or Jaunty, which have better solutions.

I have also uploaded a small shell script, kdefour-user-env, which you can source from your .bashrc to set up your environment - see the [http://easyrepairs.org/download](http://easyrepairs.org/download) page for that as well.

The KDE bug report is at [https://bugs.kde.org/show_bug.cgi?id=197104](https://bugs.kde.org/show_bug.cgi?id=197104)

The Ubuntu bug report is here: [https://bugs.launchpad.net/ubuntu/+source/kdenetwork/+bug/391763](https://bugs.launchpad.net/ubuntu/+source/kdenetwork/+bug/391763) - there is a cleaner fix if you are on Jaunty, by enabling the jaunty-proposed repository.  If you are on Jaunty, use this, and if you are on Intrepid, consider upgrading to Jaunty.  

This build of the KDE 4.3.1 version of Kopete  is not packaged as a .deb, but as a .tar.bz2 file, and is huge (179 MB), but it should not require any dependencies beyond a clean Hardy install, whichever *buntu 8.04 variant you use.  However, it does let you carry on using Yahoo from Kopete, since at some point Yahoo is likely to disable the old authentication method.

To install, simply do this: ```
sudo mkdir -p /opt; cd /opt; sudo tar xzjvf kdefour-kopete-4.3.1.tar.bz2
```
This untar's the files into /opt/kdefour, which should not interfere with anything else.   You need about 179 MB for the download and 269MB to install (on /opt, which is probably in your root filesystem - type "df -h /opt" to find out where it is, and how much space is left).

You should not need to install any dependencies, as it includes its own version of Qt4 (4.5.1) and KDE libraries - I have now tested this on a clean Hardy install, but let me know how you get on.  It should work for Ubuntu, Kubuntu, Xubuntu and other variants, and should not interfere with other KDE programs.  If you do find it interferes, create a shell script called "run-kopete" that uses the /opt/kdefour/kdefour-user-env script to set the environment just for Kopete.

To transfer your existing Kopete configuration you'll need to do some reading and Googling.

If you'd like a cleaner fix, maybe you can comment on the Ubuntu bug page linked above, and request a backport to Hardy.  However, since Hardy only had KDE 4.0 as an option, it would be quite a lot of work for the Kubuntu team to do this.

---

