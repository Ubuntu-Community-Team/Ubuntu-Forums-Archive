---
title: "Download .deb's via packages.ubuntu.com?"
date: 2009-03-11
forum: General Help
---

### Post by wubrgamer on 2009-03-11
Is it possible to only download a .deb via packages.ubuntu.com?

I would like to download something available in jaunty for installation in an intrepid system. But do not want to place the jaunty repo's in my sources.list file.

(I'm not quite THAT bleeding edge) but I would prefer to run the ubuntu version of unetbootin rather than the one from their website, and it appears that that package is only available in the jaunty repo's, not the intrepid ones.

Thank you,

wubrgamer

---

### Post by lindsay7 on 2009-03-11
Here is another place.

[http://www.getdeb.net/about.php](http://www.getdeb.net/about.php)

---

### Post by aeiah on 2009-03-11
yes you can, but .deb files have dependencies. usually, the deb is clever enough to fetch what it needs but if it requires a version that's only available in the jaunty repos for example, it wont find it and you'll have to install that manually too. this can lead to ages spent getting all the .deb files you need only to discover a dead-end when one of them doesnt install to your older release.

so yea. its possible but doesnt always work. its not really good practice.

ive only used unetbootin once, to install crunchbang linux on my acer aspire one. i got it from sf.net and everything went fine.

```


wget http://unetbootin.sourceforge.net/unetbootin-linux-latest

sudo apt-get install p7zip-full

chmod +x unetbootin-linux-*

./unetbootin-linux-*


```

---

### Post by wubrgamer on 2009-03-12
Thank you both!

I am well aware of the risks associated with u

I was hoping for more detailed instructions concerning how to go about downloading them from packages.ubuntu.com though.

Thank you for your replies!

---

### Post by mb_webguy on 2009-03-12
Search for the package you want.  You'll likely be given a number of versions for which this package is available.  Click on the appropriate version to go to the page for the package.  You'll see a list of related packages, and below that the architectures for which the package is available.  Click the appropriate architecture to download the package.

---

