---
title: "Problems with ScanMaker 4800 Need to Replace Backend"
date: 2009-02-21
forum: General Help
---

### Post by DocEsq on 2009-02-21
I have the Microtek ScanMaker 4800 scanner that does not seem to work correctly in Ubuntu or Kubuntu.  The scanner is supported by the SANE project using libsane-sm3840 backend.

My research has turned up that there is a bug in the libsane-sm3840.so.1.0.19 which comes with Ubuntu 8.04.  It seems that the last stable version was libsane-sm3840.so.1.0.15.

I have downloaded libsane-sm3840.so.1.0.15 and plan of following these directions I found:
delete from /usr/lib/sane:

libsane-sm3840.so.1.0.19
libsane-sm3840.so
libsane-sm3840.so.1 

Then I will copy libsane-sm3840.so.1.0.15 into /usr/lib/sane

The instructions I found then say to create a symbolic link as shown:

cd /usr/lib/sane
ln -s libsane-sm3840.so.1.0.15 libsane-sm3840.so
ln -s libsane-sm3840.so.1.0.15 libsane-sm3840.so.1 

From what I can tell I will need to log in as Root so as to do the deleting and inserting.  

I have found  libsane-sm3840.so.1.0.19,
libsane-sm3840.so and libsane-sm3840.so.1a on my system (I am thinking that the libsane-sm3840.so.1a is the correct file).  Since I only seem to be adding  libsane-sm3840.so.1.0.15 I am assuming that the other files will be created by Ubuntu once I run the SANE Utility.

Is there anything that I am missing here before I attempt to do this?

Thanks for any help you can give.

DocEsq

---

### Post by grashdur on 2009-02-21
I have the same problem, ever since (I think) Gutsy Gibbon. I've been advised not to revert to the old driver or backend -- I have an ongoing thread about this, still ongoing: 

[http://ubuntuforums.org/showthread.php?t=1064489]("http://http://ubuntuforums.org/showthread.php?t=1064489")

I invite you to join the discussion. By the way, if you did revert to the older version, wouldn't regular updates automatically replace it with the new one again? Is there some way to tell it "Don't update this one package"?

---

### Post by DocEsq on 2009-02-21
The error message I am getting is the same that you had "Error Failed to open device 'sm3840:libusb:001:005': Access to resource has been denied."

I have not reverted to the old backend and was just looking to see if it was something to do.  I will check out your thread and will post into it later after I do some more digging in my system.

---

