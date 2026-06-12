---
title: "Feisty Test 3 not playing AAC files"
date: 2007-02-03
forum: Development CD/DVD Image Testing
---

### Post by emoore625 on 2007-02-03
No I didn't buy the song from iTunes.

When I click on an m4a file, movie player opens, checks for programs to use, but never plays the file.  I have both gstreamer extras and ffmpeg installed.  I get an error message that the plugin is not installed.

This all worked fine under 6.10 with automatix.

Anyone have a workaround?

---

### Post by emoore625 on 2007-02-03
I fixed it but it's still a bug...

I had to use the old Dapper method of installing the gstreamer0.10-plugins-bad-multiverse file.  This set doesn't come up when I initially double click the file.

---

### Post by pochu on 2007-02-04
A developer has implemented a feature to auto-install codecs when needed. It's in beta in Feisty, so if you have any problem with that, please, report it to [Launchpad]("https://bugs.launchpad.net/ubuntu/+filebug").

Thanks
Pochu

---

### Post by Henrik on 2007-02-04
Here is [the message]("https://lists.ubuntu.com/archives/ubuntu-devel/2007-January/023211.html") introducing the new feature easy codec installation. It seems you should file bugs under gnome-app-install with the tag *easy-codec-installation*.

---

