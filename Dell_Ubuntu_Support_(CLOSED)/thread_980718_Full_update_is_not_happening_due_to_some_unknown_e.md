---
title: "Full update is not happening due to some unknown error"
date: 2008-11-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mkmansur on 2008-11-13
My one is Dell's Latitude D820. After I installed it's update manager is showing something as following after some successful updates:

> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2)  Hash Sum mismatch

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.bz2)  Hash Sum mismatch

W: Some index files failed to download, they have been ignored, or old ones used instead.

Even I can't update gstreamer to run mp3s as it is saying hardware error and this is not right for my i386 type hardware. I actually don't know what to do. Do you have any help in this regard.

---

### Post by iaskedalice09 on 2008-11-13
Did you update your software before actually updating Ubuntu OS? I have heard that is a best practise type thing, and it made it a lot smoother for me at least.

```

sudo apt-get update
sudo apt-get upgrade

```

THEN
```

sudo apt-get dist-upgrade

```

Or if you're in the GUI, hit the second Upgrade button. If you have problems finding it, just ask and I'll get a screencap! :-)

I hope this helps!
bobby

---

### Post by infinitejones on 2008-11-13
Just an idea but try using different repositories:

System -> Administration -> Software Sources then choose Other from the drop-down box next to "Download from:"

(BTW I'm assuming you're using Ubuntu. If you're on Kubuntu, I don't know how to change repositories - sorry!)

For the purposes of seeing if it'll fix this problem it doesn't really matter which one you choose, although it's good practice longer term to choose one geographically close to where you live (if only to make sure certain servers don't get overused).

Try that, then let it reload, or open a terminal window (alt+F2) and type sudo apt-get update.

If the errors are no longer appearing, just do a full upgrade as normal. If they still appear - come back and let us know!

---

