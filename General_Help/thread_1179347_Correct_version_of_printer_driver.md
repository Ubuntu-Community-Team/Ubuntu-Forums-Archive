---
title: "Correct version of printer driver"
date: 2009-06-05
forum: General Help
---

### Post by jbarjoy on 2009-06-05
I recently purchased HP Officejet Pro K5400 printer. Driver recommended by linuxprinting.org and HP is HPLIP (Linux Imaging and Printing system).  So far, nothing but trouble.  Before I throw in the towel, I want to try latest version of driver.  Version supplied with Ubuntu 8.04 (LTS) is 2.8.2, released July 2007. HP's own version is up to 3.9.4, released May 2009.  I don't know what release is available for later Ubuntu releases, but in any case I want to stick with the LTS for now.
    Among other considerations, HPLIP 2.8.2 uses python-qt3 display interface, but Ubuntu 8.04 supplies python-qt4, which is used by later HPLIP.  So although the interface is installed, HPLIP does not recognize it.
    I would like to delete existing HPLIP from Ubuntu and download recent version directly from HP, but I question going outside repositories for new version.  Why have Ubuntu maintainers kept to 2-year-old HPLIP instead of updating repository?  Do they know something that I should know?  Is it unstable?
    I would appreciate any insights you can supply.

---

### Post by ajgreeny on 2009-06-05
I have certainly done what you are enquiring about in the past when a new printer I had was not supported by the ubuntu version of hplip.  There was no difficulty in either getting the hplip from HP direct, nor in using it, and it completely solved my problem.  I seem to remember that the HP site even had .deb versions available, but it was a long time ago and I can't really remember for certain if that was so.

I've just looked and they use a .run file, but it should install automatically in ubuntu using the terminal, and full instructions are given on the site [http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)

---

### Post by jbarjoy on 2009-06-05
Many thanks to ajgreeny for quick response. You emboldened me to download hplip.  All went well.  Testing the new driver has been mostly great!  The printer now works wi):Pth a couple of very odd quirks (e.g. it removes titles from text documents) but at least it is mostly working, so I have a platform to stand on, at least, as I investigate further.  Love your hat!

---

### Post by rcayea on 2009-06-05
I, too, after stumbling upon this thread thank you for the response and info. You solved my printer issue.

---

