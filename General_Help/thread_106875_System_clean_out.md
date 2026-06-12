---
title: "System clean out"
date: 2005-12-21
forum: General Help
---

### Post by welsh_spud on 2005-12-21
My hard disk drive on my laptop is starting to get a bit on the full side. Is there a way I can remove all the libs that get installed with programs, but are not used anymore?

And are there any log files that tend to get large over time that could do with being deleted?

---

### Post by matthew on 2005-12-21
Look at /home/username/.thumbnails -- you can safely delete all the images in this directory.

/var/cache/apt/archives holds the deb files for things you have installed. I seem to recall an easy command line way to remove these as well...I think it's "sudo apt-get clean" but you had best wait until that is confirmed by another source.

---

