---
title: "Apt-get Sources"
date: 2006-09-24
forum: Desktop Environments
---

### Post by simon360 on 2006-09-24
I've been having huge problems with the speed of downloads via apt-get. I'm just wondering: are the sources organized based on location, and is there a way to change them to a fast mirror? Thanks!

simon360

---

### Post by croak77 on 2006-09-24
You can specify the mirror in your /etc/apt/sources.list.

---

### Post by simon360 on 2006-09-24
Ok, thanks, but is there a list of mirrors somewhere?

---

### Post by chris_andrew on 2006-09-24
You may find good results if you Google "apt-spy".  This tool compares all download sites, and writes your /etc/apt/sources.list, using the fastest mirrors.  This works brilliantly with Debian, so hopefully it does for Ubuntu, by now.

Thanks,

Chris.

---

### Post by carney1979 on 2007-01-07
As far as I know, apt-spy only parses Debian sources, not Ubuntu.

David

---

