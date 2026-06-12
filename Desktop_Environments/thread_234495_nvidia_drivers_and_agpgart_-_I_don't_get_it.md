---
title: "nvidia drivers and agpgart - I don't get it"
date: 2006-08-11
forum: Desktop Environments
---

### Post by louis_nichols on 2006-08-11
Ok, folks, here is this situation I really don't understand.

I followed [this howto]("http://gentoo-wiki.com/HARDWARE_Nvidia_Driver_AGP_FastWrite_and_Side_Band_Addressing") to enable agpfastwrites and SBA for my nvidia GeForce fx5200. It all seems ok:

```
myself@home:~$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          NVIDIA
AGP Rate:        8x
Fast Writes:     Enabled
SBA:             Enabled
```

Now, an important thing in this process is that one should disable agpgart. So, I followed the instructions [here]("http://ubuntuforums.org/showpost.php?p=1356239&postcount=9") to do this and, considering the output above, it seems to have worked.
 
Plus dmesg | grep NVAGP doesn't output anything, so, according to the original gentoo howto, this is an indication I'm using nvagp, not agpgart.

Still, when I try lsmod...
```
myself@home:~$ lsmod | grep agp
agpgart                37072  1 nvidia

```

so it seems agpgart is still there.

Now, I don't know what to believe anymore. Did I disable agpgart or not? Or does it not matter, in fact?

Does anybody understand what's the deal here? I'd really like to know.

---

