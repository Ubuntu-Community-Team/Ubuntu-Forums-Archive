---
title: "Fuse not working"
date: 2009-01-17
forum: General Help
---

### Post by iler on 2009-01-17
Hi,

I'm successfully backing up my files on my Mac with jungledisk to Amazon but I haven't got it working on my Ubuntu server. I have a virtual xen server running 64bit Ubuntu 8.04.1 that I have bought from my operator as a service and I have installed versio 2.50 of jungledisk to get it working in 64bit system. When I'm trying to run jungledisk on my server I get this error:
```
[WARNING]: [Failed to mount volume] [Code: xDriveMapFailed] [Time: Sat Jan 17 17:56:19 2009] [Message: fuse_mount(/mnt/jungledisk) failed: fuse: device not found, try 'modprobe fuse' first] [Location: JungleFuse.cpp:1460 |JungleFuse.cpp:1543 |]
```

And when I try to run modprobe fuse I get this error:
```
FATAL: Module fuse not found.
FATAL: Error running install command for fuse

```

I have installed fuse-utils libfuse-dev libfuse2 and there is a line fuse in /etc/modules but still the /dev/fuse is missing. Am I doing something really wrong or is there some kind of an issue with fuse and xen?

---

### Post by Yellow Pasque on 2009-01-17
Search for the fuse.ko file. You should have it at /lib/modules/`uname -r`/kernel/fs/fuse/

I think you could technically build your own fuse kernel module, but the linux-image package should really provide this file.

---

### Post by albinootje on 2009-01-17
> **iler said:**
> Am I doing something really wrong or is there some kind of an issue with fuse and xen?

From 2006, please read this whole thread, could be helpful for you.

[http://developer.amazonwebservices.com/connect/thread.jspa;jsessionid=FD4909365330B5135816A16EE3848E1F?messageID=42472&#42472](http://developer.amazonwebservices.com/connect/thread.jspa;jsessionid=FD4909365330B5135816A16EE3848E1F?messageID=42472&#42472)
> 
   Re: fuse and Xen?
Posted: Aug 25, 2006 11:21 AM PDT   in response to: Daniel Drucker 	  	
  	Click to reply to this thread 	Reply

Unfortunately we have not compiled FUSE into our kernel.

You will need to compile your own module under Xen in order for the module to be compatible with our kernel. Start off at Xen virtual machine monitor for information on Xen.

Meanwhile I will see what I can do this side...
Message was edited by: RolandPJ@AWS 


---

