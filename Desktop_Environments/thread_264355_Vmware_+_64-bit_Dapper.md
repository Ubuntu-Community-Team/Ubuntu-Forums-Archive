---
title: "Vmware + 64-bit Dapper"
date: 2006-09-24
forum: Desktop Environments
---

### Post by jonttu_com on 2006-09-24
I keep getting the same error when trying to run vmware in 64-bit Dapper:

```
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib32/libcairo.so.2)

```

Any ideas of what's happening?

---

### Post by tymek666 on 2006-09-24
I installed VM followed that HowTO:

[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

It works great, but i'm using kubuntu amd64.

---

### Post by jonttu_com on 2006-09-24
I found this in the howto:

```
sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/
```

After doing this, vmware doesn't give any errors anymore. It just crashes.

---

### Post by tripleee on 2006-09-29
I get the same error, but it appears to be harmless. I didn't even notice it until I ran vmware from the shell prompt.

I don't think you can copy 64-bit stuff from /usr/lib to the (as I understand it?) 32-bit vmware/lib -- do you have all the prerequisites installed? See [https://help.ubuntu.com/community/VMware_Guide%3a_Installing_VMware_Server_on_Ubuntu_6%2e06_LTS_amd64](https://help.ubuntu.com/community/VMware_Guide%3a_Installing_VMware_Server_on_Ubuntu_6%2e06_LTS_amd64)

I wasn't getting sound but now I figured that out, too -- I'll update the wiki with that.

---

