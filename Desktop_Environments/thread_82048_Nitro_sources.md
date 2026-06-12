---
title: "Nitro sources"
date: 2005-10-25
forum: Desktop Environments
---

### Post by RubenGonc on 2005-10-25
Hi everybody,

Can someone tell me what I got to do to compile a new kernel with the nitro sources and the patches apllied by ubuntu (usplash for example I think)?

Thank you!

---

### Post by HermanAB on 2005-10-25
In general, what you need to do to compile a kernel is the following:

# cd /usr/src/linux
# make oldconfig
# make bzImage
# make modules
# make install

In ages past, you had to do 'make dep' as well, but that is now deprecated.

The important things are:
a. First compile your existing kernel and make sure it works, before changing *anything*.
b. The step that accomplishes that is the 'make oldconfig'.

Here is a guide that goes into some more detail about patching and compiling:
[http://www.aerospacesoftware.com/kernel-compile-howto.html](http://www.aerospacesoftware.com/kernel-compile-howto.html)

---

### Post by LorenzoD on 2005-10-25
I don't know if you've had any experience with Nitro sources before, but if you haven't you may want to make sure you don't have any critical data on your system before you try it. I used Nitro sources a few years ago and funny things happened frequently. I even had it fry my file system on one occasion.

But if you do know what you're up for, by all means go ahead.

---

### Post by RubenGonc on 2005-10-25
Thank you for reply but I want to compile the kernel with the nitro patches and with the ubuntu patches too!!! And I want to know how to do this! :S

---

