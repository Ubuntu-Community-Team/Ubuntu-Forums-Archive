---
title: "FreeBSD's advertised binary compatibility vs. Cross-distro incompatibility?"
date: 2009-05-22
forum: General Help
---

### Post by UnrealMiniMe on 2009-05-22
This is a relatively advanced question, since it regards linkers and loaders.  I'm having trouble understanding the reasons for binary incompatibility between various Linux distros on the same hardware platform (i.e. i386, AMD64).  As Mark Shuttleworth mentions [here]("https://wiki.ubuntu.com/MarkShuttleworth#What%20about%20binary%20compatibility%20between%20distributions?"), making different distributions binary compatible is a pretty difficult task, and the Linux Standard Base has had a lot of trouble defining a common binary deployment platform for proprietary ISV's (game developers, etc.).

From what I understand, this is due to difficulties with dynamically linking program code to different versions of the Linux kernel and various library dependencies.  Since the Linux kernel version and any imaginable libraries are all moving targets, and every distro has different combinations of versions packed together, that presumably means that software has to be separately compiled to link with the specific version set [or ranges of versions?] of each distro.

However, the [FreeBSD Handbook talks about FreeBSD's compatibility with native Linux binaries]("http://www.freebsd.org/doc/en/books/handbook/linuxemu.html").  I didn't quite grasp their explanation on the last page, but in general, it seems as though their ELF loader can recognize Linux binaries and redirect system calls accordingly, mapping them with FreeBSD system call functions (actually, I suspect I misunderstood their explanation and just projected my own prior assumptions onto their explanation in order to make sense of it...).  In any case...why is it that FreeBSD is supposedly compatible with most Linux binaries - regardless of what distro they were compiled on - whereas various distros using Linux cannot ensure compatibility using a similar method?  I've read that the Linux kernel doesn't have a standardized ABI, but if the FreeBSD kernel can handle binaries with system calls to arbitrary Linux kernel versions, shouldn't the Linux kernel be able to do the same thing?

I'm guessing that I'm misunderstanding one of two things, but I'm not sure **which** (maybe both?), and I'm hoping someone with more knowledge can help me out:
[LIST=1][*]On one hand, maybe I'm misunderstanding the nature of FreeBSD's binary compatibility.  Is it more hit and miss than the FreeBSD handbook implies?
[*]On the other hand, maybe I'm misunderstanding the cause for binary incompatibility between Linux distros (and therefore overestimating its occurrence), since I'm pretty clueless about linkers and loaders.[/LIST]

Assuming my confusion revolves around #2:
**The issue really comes down to this:  What kinds of version changes actually break compatibility with precompiled software?**  Is compatibility **only** broken when the precompiled binary makes an API call to functionality that is not present in the kernel version or library version on the system?  That would obviously be **sufficient** to break a program (because an old program relying on a deprecated/removed API feature will not work with new kernels/libraries that no longer contain that feature; similarly, a new program relying on new kernel/library API features will not work with old versions of the kernel/library).  However, is a flat-out API change **necessary** for breakage, or can other things cause breakage?  For instance, whenever anything changes in a kernel or library (fixing bugs, adding new features, adding new things to the API, etc.), I imagine the memory offsets of each function call will naturally shift around (is this correct?).  Is this sufficient to cause breakage, even if a precompiled binary application is relying only on functionality that is still present in the new kernel/library?
**To give an example question:**  Assuming no API functionality is removed from the kernel or shared libraries (dependencies) from Jaunty to Karmic, would all Jaunty binaries still work on Karmic, or would the kernel/library version changes potentially cause breakage anyway?
**As another example question:**  If I were to recompile a vanilla Linux kernel from [http://www.kernel.org/](http://www.kernel.org/) today and include the required patches, would my Jaunty binaries still be guaranteed to work, assuming no API functionality has been removed from the kernel since Jaunty's release?

Sorry for the length of this question (and the inclusion of nested questions)...but I'm pretty confused, and I wanted to indicate exactly where I am in terms of comprehension.

Thanks!

---

### Post by UnrealMiniMe on 2009-05-25
Three day bump! :popcorn:

---

