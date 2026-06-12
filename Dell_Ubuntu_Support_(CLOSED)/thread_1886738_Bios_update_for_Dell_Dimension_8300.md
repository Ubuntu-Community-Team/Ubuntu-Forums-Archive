---
title: "Bios update for Dell Dimension 8300"
date: 2011-11-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Randymanme on 2011-11-25
Hello, 

How might I enable hardware virtualization on a Dell Dimension 8300?  Would a bios update do that for me?

Any direction here sure would be appreciated. Thanks.

---

### Post by Randymanme on 2011-11-28
From Linux Mint Forums::

                                                                     **[Re: Hardware virtualization?]("http://forums.linuxmint.com/viewtopic.php?f=49&t=86650#p500602")**

             [[IMG]http://forums.linuxmint.com/styles/linux-mint/imageset/icon_post_target.gif[/IMG]]("http://forums.linuxmint.com/viewtopic.php?p=500602#p500602")by **[Vincent Vermeulen]("http://forums.linuxmint.com/memberlist.php?mode=viewprofile&u=62313")** on Fri Nov 25, 2011 12:25 pm 
                            Do you mean Intel VT-x? It is only needed for  some specific virtualization solutions, notably Hyper-V. Things like  KVM, VirtualBox or Xen don't need it to run. You can check out if your  virtualization solutions needs it [here]("https://en.wikipedia.org/wiki/Comparison_of_platform_virtual_machines"). Check in the table if it only works with x86 VT-x or x86-64 VT-x.

More details on [hardware virtualization]("https://en.wikipedia.org/wiki/X86_virtualization").

Check [here]("http://ark.intel.com/VTList.aspx")  if your processor model has VT-x support or not. You may also be able  to find this in the flags section if you go to Menu > Control Center  > System Profiler and Benchmark > Processor.
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
And the answer is "No, your processor don't have that capability."

---

