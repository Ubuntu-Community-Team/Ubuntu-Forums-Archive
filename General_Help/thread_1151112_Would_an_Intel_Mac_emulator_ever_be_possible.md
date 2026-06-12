---
title: "Would an Intel Mac emulator ever be possible?"
date: 2009-05-06
forum: General Help
---

### Post by rmausser on 2009-05-06
Hi, I just have a question that I've been thinking about. 

I know in the past the issues related to ever running Mac applications in an emulator= they ran on the PowerPC platform. 

But, now Mac's use Intel based chips. Theres entire communities running OSX on PC computers. 

Now that it uses this x86 arch, is it not more possible to emulate Mac programs to run in Linux? Similar to the WINE application layer? 

What else is preventing this. I'm sure its a) politics and b) the closed source nature of Apples products. 

Does anyone have a good answer for this? I'd love to hear the exact specifics of why this would be so hard, considering now OSX apps run on Intel's Arch. 

Thanks

---

### Post by mb_webguy on 2009-05-06
Well, first of all a minor correction:  Wine isn't an emulator, it's an application interface.  It remaps Windows system calls to the Linux equivalents.  This is why Windows apps running under Wine will occasionally run *faster* than on Windows.

As for running OS X apps on Linux, you'd think it would be simple, since both Linux and OS X are Unix-based systems.  The problem is that Mac applications use some proprietary graphics libraries (Cocoa and Carbon) to create the windows and controls.  I believe there is at least one project in development to run OS X apps on Linux in a similar manner to Wine, but it's not likely to reach a usable state any time soon.  Wine has taken many years to get to its current state, and there's simply not as much demand for OS X-specific apps.

---

### Post by rmausser on 2009-05-10
Thanks. I appreciate the reply, but I am aware that Wine Is Not an Emulator, hence why I stated it is an Application Interface/Layer. 

Just wasn't sure if the same could be done for OSX, or a whole emulation would be required...but from the sounds of what you are saying, there are similarities. 

Still, it would be sweet to be able to have the potential to run basically any OS app in linux. 

Thanks for the reply.

---

### Post by Alterax on 2009-05-10
Well, it's not exactly emulation per se, but maybe the mol (mac-on-Linux) project is close to what you're looking for?

---

### Post by rmausser on 2009-05-25
yeah I'm aware of MOL... but MOL operates a virtualization of the PowerPC mac OSX within the PowerPC linux distribution. 

This is about as useful as trying to run PowerPC apps on an Intel Mac! If you can't run PowerPC apps on an Intel Mac, I doubt this project would have any relevance to every running Intel Mac apps on an Intel i386 arch linux distribution.

---

