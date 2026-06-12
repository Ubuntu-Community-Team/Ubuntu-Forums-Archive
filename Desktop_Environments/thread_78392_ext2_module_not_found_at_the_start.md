---
title: "ext2 module not found at the start"
date: 2005-10-18
forum: Desktop Environments
---

### Post by ekzema on 2005-10-18
Hi all,

Sorry, maybe i'm posting asking for help about an issue that's already been answered, but my search didn't gave me any relevant post about it.

Simply put:

I was using Ubuntu 5.04, then i decided to dist-upgrade to Breezy. All went fine and good BUT... somehow now when i start Ubuntu, just right after seeing the start up text "decompressing Linux", i see the PC hanging for few secs and then the display says "FATAL: Could not find ext2 module".

The rest of the boot process goes on, up to the end, just fine, and i'm able to use the PC as usual (didn't noticed any real problem that could be related to the error message i see at the start... maybe cause i do not work with any ext2 partitioned volume), but maybe someone can give me some hint/clue/help about a way of getting rid of that error message.

For the (really shallow, poor and misused) linux knowledge i have, it could be related to some kernel module not loading properly, but my abovementioned underdeveloped linux skills do not allow me to sort this out all by my self.

Thanks so much in advance for any help and your time if you feel like to answer.

---

### Post by Janek on 2005-10-24
I'm experiencing the same problem.
I'd be very grateful for any wise suggestion...

---

### Post by Janek on 2005-10-24
I'm rather new in this bussiness (I'm using Linux since the release of Breezy Badger), but somehow I've figured out couple of facts which, hopefully, could help you in solving our problem:
[LIST=1]
[*]Certainly, there's no such module as ext2 in kernel version on which Ubuntu 5.10 is based.   
[*]Everything was OK, and then, as far as I understand, our systems were told to search for ext2 module during the boot.   
[*]I have no idea how the point 2. could ever take place.   
[*]There must be (probably) some kind of configuration file in our filesystem which holds an instruction for module-init-tools (or something like that) to search for module ext2. The big question is, where is that file.   
[*]As a total newbie, I might be saying now something *really* stupid. Sorry for that. [/LIST] Anybody?
Please.

---

### Post by missmoondog on 2005-12-22
Same problem here, again, after updating the linux kernel image. same time it happened last time also. i started a thread on this topic here, [http://www.ubuntuforums.org/showthread.php?t=96224&highlight=module+ext2](http://www.ubuntuforums.org/showthread.php?t=96224&highlight=module+ext2), in which the command someone posted to repair image worked perfectly that time. did not do anything this time though. the weirder part is this only happens on this computer and not on any of my other 4.

---

### Post by missmoondog on 2005-12-23
original topic is over 2 months old and haven't gotten any other comments? this has to be a almost fairly common thing as it's the second time it's happened to me just since breezy came out?

---

### Post by schilcha on 2005-12-23
I don't actually have this problem, but will try to help anyways. 

In the other thread, reconfiguration of the kernel image did the job. So, I suggest to look at the files in /etc/mkinitramfs. Probably the ext2-model is listed in /etc/mkinitramfs/modules, although it shouldn't be there...

---

### Post by missmoondog on 2005-12-23
appreciate the help, but i don't see any ext2-model listed in there. this is all that is contained there:

# List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
#
# This might be good choices:
#
# raid1
# sd_mod

---

