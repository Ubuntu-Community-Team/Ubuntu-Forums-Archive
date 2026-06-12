---
title: "mldonkey error"
date: 2006-07-26
forum: Desktop Environments
---

### Post by publius25 on 2006-07-26
Removing mldonkey-server ...
Stopping MLDonkey: mlnetNo process in pidfile `/var/run/mlnet.pid' found running; none killed.
invoke-rc.d: initscript mldonkey-server, action "stop" failed.
dpkg: error processing mldonkey-server (--purge):
 subprocess pre-removal script returned error exit status 1
Starting MLDonkey: mlnetinstall: invalid option -- f
Try `install --help' for more information.
invoke-rc.d: initscript mldonkey-server, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mldonkey-server

I get this error both whenever I run apt/synaptic/dpkg can anyone help me. I would like to get mldonkey running. I had the previous version running on breezy but this one seems to be givng me trouble. This happened after i run apt-get install mldonkey-server 

I have tried deleting the config-temp and pid file and managed to get it to run but it self termianted. 
Does anyone know what the problem is?

publius

---

### Post by rodrigochinaski on 2006-09-26
I have this problem too. Did you solve it?

---

### Post by invisibastard on 2006-09-28
The last post on this page worked for me.

[http://www.ubuntuforums.org/showthread.php?t=232680&highlight=mldonkey-server](http://www.ubuntuforums.org/showthread.php?t=232680&highlight=mldonkey-server)

I have had this problem for months, and have been annoyed by it. I am glad it is finally gone!

Thanks,
Rich

---

