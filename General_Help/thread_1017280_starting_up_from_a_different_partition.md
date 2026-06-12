---
title: "starting up from a different partition"
date: 2008-12-20
forum: General Help
---

### Post by sausages on 2008-12-20
Recently I've been having wireless problems under 8.10, so I tried to fix it, but apparently only made things worse! I decided to install 8.10 from the ISO (previously I upgraded from 8.04) in the hopes that any settings I may have buggered would be set back to normal. This didn't happen, and now in the new 8.10 install I can't use the wireless, when I tried to use the nvidia drivers under hardware drivers it won't stay activated, so things went from bad to worse considering I am using Blender on this machine. I read somewhere that Paldo Linux is a good choice for wireless, installed that, it doesn't work either.
       I thought initially that I was completely wiping out my drive to install the new OSes, but this isn't the case. Their partitions still exist on my drive, but grub isn't offering to let me start up from them. Is there any way to start from these partitions so that I can revert back to my original mess? And, can I clean up the other 2 partitions so that I can reclaim that disk space for projects? Thanks

---

### Post by SPr on 2008-12-21
When installing select the "manual" option and pick the partitions your self.

If the partitions are still intact follow the advice here: [How to install Grub from a live Ubuntu cd](http://ubuntuforums.org/showthread.php?t=224351).

To "clean up" the other partitions just reformat them.

---

