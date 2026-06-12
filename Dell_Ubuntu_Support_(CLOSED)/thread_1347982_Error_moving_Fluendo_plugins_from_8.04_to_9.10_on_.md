---
title: "Error moving Fluendo plugins from 8.04 to 9.10 on mini 9"
date: 2009-12-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mirach on 2009-12-06
On my mini 9 and I want to move the Fluendo gstreamer plugins from the factory installed dellbuntu 8.04 lpia to my 9.10 lpia install.

To do this I put the image I made of 8.04 back on my mini temporarily and tried to repack the Fluendo plugins into a deb using:

sudo dpkg-repack gstreamer0.10-fluendo-plugins

I got the following errors:

```
$ sudo dpkg-repack gstreamer0.10-fluendo-plugins
cp: failed to preserve ownership for `./dpkg-repack-8636//usr/share/doc/gstreamer0.10-fluendo-plugins/copyright': Operation not permitted
dpkg-repack: Error running: cp -pd /usr/share/doc/gstreamer0.10-fluendo-plugins/copyright ./dpkg-repack-8636//usr/share/doc/gstreamer0.10-fluendo-plugins/copyright
cp: failed to preserve ownership for `./dpkg-repack-8636//usr/share/doc/gstreamer0.10-fluendo-plugins/EULA.gz': Operation not permitted
dpkg-repack: Error running: cp -pd /usr/share/doc/gstreamer0.10-fluendo-plugins/EULA.gz ./dpkg-repack-8636//usr/share/doc/gstreamer0.10-fluendo-plugins/EULA.gz
cp: failed to preserve ownership for `./dpkg-repack-8636//usr/share/doc/gstreamer0.10-fluendo-plugins/changelog.Debian.gz': Operation not permitted
dpkg-repack: Error running: cp -pd /usr/share/doc/gstreamer0.10-fluendo-plugins/changelog.Debian.gz ./dpkg-repack-8636//usr/share/doc/gstreamer0.10-fluendo-plugins/changelog.Debian.gz
cp: failed to preserve ownership for `./dpkg-repack-8636//usr/lib/gstreamer-0.10/libgstflumpeg4videodec.so': Operation not permitted
dpkg-repack: Error running: cp -pd /usr/lib/gstreamer-0.10/libgstflumpeg4videodec.so ./dpkg-repack-8636//usr/lib/gstreamer-0.10/libgstflumpeg4videodec.so
cp: failed to preserve ownership for `./dpkg-repack-8636//usr/lib/gstreamer-0.10/libgstflumpegdemux.so': Operation not permitted
dpkg-repack: Error running: cp -pd /usr/lib/gstreamer-0.10/libgstflumpegdemux.so ./dpkg-repack-8636//usr/lib/gstreamer-0.10/libgstflumpegdemux.so
cp: failed to preserve ownership for `./dpkg-repack-8636//usr/lib/gstreamer-0.10/libgstfluasfdemux.so': Operation not permitted
dpkg-repack: Error running: cp -pd /usr/lib/gstreamer-0.10/libgstfluasfdemux.so ./dpkg-repack-8636//usr/lib/gstreamer-0.10/libgstfluasfdemux.so
cp: failed to preserve ownership for `./dpkg-repack-8636//usr/lib/gstreamer-0.10/libgstflurtp.so': Operation not permitted
dpkg-repack: Error running: cp -pd /usr/lib/gstreamer-0.10/libgstflurtp.so ./dpkg-repack-8636//usr/lib/gstreamer-0.10/libgstflurtp.so
cp: failed to preserve ownership for `./dpkg-repack-8636//usr/lib/gstreamer-0.10/libgstfluwmvdec.so': Operation not permitted
dpkg-repack: Error running: cp -pd /usr/lib/gstreamer-0.10/libgstfluwmvdec.so ./dpkg-repack-8636//usr/lib/gstreamer-0.10/libgstfluwmvdec.so
cp: failed to preserve ownership for `./dpkg-repack-8636//usr/lib/gstreamer-0.10/libgstflumcaacadec.so': Operation not permitted
dpkg-repack: Error running: cp -pd /usr/lib/gstreamer-0.10/libgstflumcaacadec.so ./dpkg-repack-8636//usr/lib/gstreamer-0.10/libgstflumcaacadec.so
cp: failed to preserve ownership for `./dpkg-repack-8636//usr/lib/gstreamer-0.10/libgstflumms.so': Operation not permitted
dpkg-repack: Error running: cp -pd /usr/lib/gstreamer-0.10/libgstflumms.so ./dpkg-repack-8636//usr/lib/gstreamer-0.10/libgstflumms.so
cp: failed to preserve ownership for `./dpkg-repack-8636//usr/lib/gstreamer-0.10/libgstfluwmadec_stereo.so': Operation not permitted
dpkg-repack: Error running: cp -pd /usr/lib/gstreamer-0.10/libgstfluwmadec_stereo.so ./dpkg-repack-8636//usr/lib/gstreamer-0.10/libgstfluwmadec_stereo.so
cp: failed to preserve ownership for `./dpkg-repack-8636//usr/lib/gstreamer-0.10/libgstflump3dec.so': Operation not permitted
dpkg-repack: Error running: cp -pd /usr/lib/gstreamer-0.10/libgstflump3dec.so ./dpkg-repack-8636//usr/lib/gstreamer-0.10/libgstflump3dec.so
cp: failed to preserve ownership for `./dpkg-repack-8636//usr/lib/gstreamer-0.10/libmch264dec_i386.so': Operation not permitted
dpkg-repack: Error running: cp -pd /usr/lib/gstreamer-0.10/libmch264dec_i386.so ./dpkg-repack-8636//usr/lib/gstreamer-0.10/libmch264dec_i386.so
cp: failed to preserve ownership for `./dpkg-repack-8636//usr/lib/gstreamer-0.10/libgstfluh264dec.so': Operation not permitted
dpkg-repack: Error running: cp -pd /usr/lib/gstreamer-0.10/libgstfluh264dec.so ./dpkg-repack-8636//usr/lib/gstreamer-0.10/libgstfluh264dec.so
cp: failed to preserve ownership for `./dpkg-repack-8636//usr/lib/gstreamer-0.10/libmcaacadec_i386.so': Operation not permitted
dpkg-repack: Error running: cp -pd /usr/lib/gstreamer-0.10/libmcaacadec_i386.so ./dpkg-repack-8636//usr/lib/gstreamer-0.10/libmcaacadec_i386.so
cp: failed to preserve ownership for `./dpkg-repack-8636//usr/lib/gstreamer-0.10/libgstflumpeg2vdec.so': Operation not permitted
dpkg-repack: Error running: cp -pd /usr/lib/gstreamer-0.10/libgstflumpeg2vdec.so ./dpkg-repack-8636//usr/lib/gstreamer-0.10/libgstflumpeg2vdec.so
cp: failed to preserve ownership for `./dpkg-repack-8636/DEBIAN/md5sums': Operation not permitted
dpkg-repack: Error running: cp -p /var/lib/dpkg/info/gstreamer0.10-fluendo-plugins.md5sums ./dpkg-repack-8636/DEBIAN/md5sums
chown: changing ownership of `./dpkg-repack-8636/DEBIAN/control': Operation not permitted
dpkg-repack: Error running: chown 0:0 ./dpkg-repack-8636/DEBIAN/control
dpkg-deb: building package `gstreamer0.10-fluendo-plugins' in `./gstreamer0.10-fluendo-plugins_0.10.6+belmont-0netbook0belmont3_lpia.deb'.
dpkg-deb: control directory has bad permissions 700 (must be >=0755 and <=0775)
dpkg-repack: Error running: dpkg --build ./dpkg-repack-8636 .
dpkg-repack: Problems were encountered in processing.
dpkg-repack: The package may be broken.
```

Is there any way around this?

Thanks

---

### Post by coffeeaddict22 on 2009-12-08
Hi, 
It's probably a bad move.  The package is in Synaptic, and given the way Linux continues to change, you're probably better installing the version known to work with the current version of your OS.

---

