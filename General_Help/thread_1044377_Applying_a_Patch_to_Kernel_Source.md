---
title: "Applying a Patch to Kernel Source"
date: 2009-01-19
forum: General Help
---

### Post by beastrace91 on 2009-01-19
So to sum it up quickly I need to recompile a custom kernel to get my 4 gigs of ram working in my laptop, I found the following patch posted by someone on the NVNews board:

```
diff -Naur linux-2.6.27.orig/arch/x86/pci/i386.c linux-2.6.27/arch/x86/pci/i386.c
--- linux-2.6.27.orig/arch/x86/pci/i386.c	2008-06-03 20:24:26.000000000 -0400
+++ linux-2.6.27/arch/x86/pci/i386.c	2008-06-03 20:25:40.000000000 -0400
@@ -122,6 +122,10 @@
 				r = &dev->resource[idx];
 				if (!r->flags)
 					continue;
+				if ((r->start == 0xbdf00000) && (r->end == 0xddefffff)) {
+					r->start = 0xc0000000;
+					r->end = 0xe0000000;
+				}
 				pr = pci_find_parent_resource(dev, r);
 				if (!r->start || !pr ||
 				    request_resource(pr, r) < 0) {

```

I have the Kernel sources downloaded... now I am unsure how do I apply this patch? Help?

~Jeff

---

### Post by Titan8990 on 2009-01-19
You don't need to use a "patch".

All 2.6 kernels have the ability to enable PAE to use more than 4GB of RAM, although the ideal way is to use a 64bit kernel.


Ubuntu kernel compilation is very different that other distros. They highly recommend that you don't change anything.


From the kernel config (make menuconfig) it should be something like:


General Setting -> PAE


or you can use / to search the kernel config menu.

---

### Post by beastrace91 on 2009-01-19
Searching for "PAE" found me this in the menuconfig: ```
  &#9474; Symbol: X86_PAE [=n]                                                                                                                                         &#9474;  
  &#9474; Prompt: PAE (Physical Address Extension) Support                                                                                                             &#9474;  
  &#9474;   Defined at arch/x86/Kconfig:924                                                                                                                            &#9474;  
  &#9474;   Depends on: X86_32 && !HIGHMEM4G                                                                                                                           &#9474;  
  &#9474;   Location:                                                                                                                                                  &#9474;  
  &#9474;     -> Processor type and features                                                                                                                           &#9474;  
  &#9474;   Selects: RESOURCES_64BIT                                                                                                                                   &#9474;  
  &#9474;   Selected by: HIGHMEM64G && <choice> && !M386 && !M486   
``` How would I apply the above patch to where it needs to go? I am rather new at this but really need my ram working... it is not an issue with more than 4 gigs of ram it is an issue with more than 2 gigs... it is a known issue with the Asus G1Sn...

Check [here](http://www.nvnews.net/vbulletin/showthread.php?t=113682) for the larger picture... if you have another suggestion how to get the ram working other than patching the kernel and recompiling I am more than willing to try things.

Thanks,
~Jeff

---

### Post by Titan8990 on 2009-01-19
Like I said, you don't need the patch. You just need to enable PAE in the kernel and there may also be a specific option, in the same section, about > 4GB of memory.

---

### Post by beastrace91 on 2009-01-19
> **Titan8990 said:**
> Like I said, you don't need the patch. You just need to enable PAE in the kernel and there may also be a specific option, in the same section, about > 4GB of memory.

How do I enable PAE in the kernel? Searching like you said yields what I posted above.

~Jeff

---

### Post by beastrace91 on 2009-01-19
Ok Titian... I have been crawling the web and I am decently sure you are incorrect... PAE appears (at least to me) to be a method of getting 4+ gigs of ram working on a 32bit os... I am running a 64bit OS but there is a known issue with the Nvidia driver and having more than 2 gigs of ram in some Asus models (which they could fix with a simple bios update but they refuse to release it!) so I need to apply the above posted patch to my linux kernel source before I try to compile it... Anyone help? I am beginning to think there is no one useful online that can fix this issue, I have joined at least 6 other linux help forums in the last 48 hours and have gotten nothing useful thus far towards solving the issue. Guess it is a good thing Windows 7 is coming out :(

~Jeff

---

