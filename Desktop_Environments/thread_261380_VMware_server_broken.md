---
title: "VMware server broken"
date: 2006-09-20
forum: Desktop Environments
---

### Post by heffo_j on 2006-09-20
G'day folks,

I have reinstalled Server since the recent Linux kernel upgrade and it now won't run my .vmx files, even though it boots up okay. I get the following messages:

[B]Unable to change virtual machine power state: The process exited with an error:
End of error message.[/B]

I also get the following message when I boot:

**/usr/lib/vmware/bin vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)**

Help with this would be greatly appreciated. I've no help on the vmware site over this matter.

Regards
John

---

### Post by pod25 on 2006-09-20
Try this :

```
sudo /usr/bin/vmware-config.pl
```
If you see this error :
```
It cannot find /usr/src/kernel/include
```
Then do this :
```
sudo apt-get install linux-headers-`uname -r`
```
Then you can try this again :
```
sudo /usr/bin/vmware-config.pl
```

Good luck

---

### Post by austway on 2006-09-20
I too had the same problem. Your instructions worked perfectly and solved the issue for me, as well as prevented a lot of potential hair-tearing.

Thank you very much for your help.

Ken

---

### Post by reacocard on 2006-09-20
I'm having the same problem. Unfortunately, that fix doesn't work for me. Any ideas?

EDIT: found a fix [here.]("http://www.vmware.com/community/thread.jspa?messageID=477309&tstart=0")

Add to /usr/lib/vmware/lib/wrapper-gtk24.sh in vm_run()

# Fix for pulling in libdbus-1.so.2 instead of .3
export LD_PRELOAD=/usr/lib/libdbus-1.so.3:$LD_PRELOAD

---

### Post by heffo_j on 2006-09-21
Thanks people for your suggestions. 

The headers are not the problem: I fixed that perviously. I had a poke at the suggstion from Reacocard; still get the same inital error message. I seems like a permission issue but I can't find the offending file. 

Any other clues?

John

---

