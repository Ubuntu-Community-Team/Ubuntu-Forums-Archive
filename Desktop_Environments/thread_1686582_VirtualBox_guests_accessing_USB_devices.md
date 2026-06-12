---
title: "VirtualBox guests accessing USB devices"
date: 2011-02-12
forum: Desktop Environments
---

### Post by CTBuckweed on 2011-02-12
I present this fix in case others have the same problem. It's a VirtualBox 4.0.2 defect and a ticket at virtualbox.org has already been opened for it.

I upgraded from VirtualBox 3.2.12 to 4.0.2. I am running ubuntu Lucid (10.04), 64 bit and I host a Windows XP guest OS for things that must have Windows. Since the upgrade, I have been having a problem restoring a guest OS saved state back to the running state.

I get the error in a pop-up that states:
[INDENT][B]################################
Failed to open a session for the virtual machine XP-1.

Implementation of the USB 2.0 controller not found!

Because the USB 2.0 controller state is part of the saved VM state, the VM cannot be #started. To fix this problem, either install the 'Oracle VM VirtualBox Extension Pack' #or disable USB 2.0 support in the VM settings (VERR_NOT_FOUND).

Unknown error creating VM (VERR_NOT_FOUND).
################################[/B][/INDENT]

This happens consistently whenever I attempt to restore the saved state of the guest OS when it's configured to use USB 2.0 devices.

I was about to back off to vbox 3.2.12, then I found a fix at the VirtualBox web site. There's already a ticket open for the defect - ticket #8182. [http://www.virtualbox.org/ticket/8182](http://www.virtualbox.org/ticket/8182)

There is a work-around as specified in the ticket details. I am fixed!!! I followed the details described in the work-around; The fix has to do with editing the .xml file for the virtual machine. See the ticket URL for more details.

---

### Post by pdc124 on 2011-05-03
I had the same error message after removing VB  3-2 and  installing VB 4. I closed the machine, went into 'settings' for that machine , it told me somthing was wrong adn that it had corrected it. The machine started after that.

---

### Post by CTBuckweed on 2011-05-04
I upgraded my Vbox from 4.0.4 to 4.0.6... Now the USB support doesn't work at all. I can't even see my USB printer -- I can't see any USBs at all now. When I get time, I'll just downgrade it to 4.0.4. and report it as a defect to virtualbox.org

---

### Post by CTBuckweed on 2011-05-20
> **CTBuckweed said:**
> I upgraded my Vbox from 4.0.4 to 4.0.6... Now the USB support doesn't work at all. I can't even see my USB printer -- I can't see any USBs at all now. When I get time, I'll just downgrade it to 4.0.4. and report it as a defect to virtualbox.org

I upgraded to 4.0.8 just a couple of days ago.... Now it works :P

---

