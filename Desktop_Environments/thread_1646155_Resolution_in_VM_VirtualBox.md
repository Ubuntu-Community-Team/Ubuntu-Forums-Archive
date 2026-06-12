---
title: "Resolution in VM VirtualBox"
date: 2010-12-15
forum: Desktop Environments
---

### Post by immabamboo on 2010-12-15
I'm new to Ubuntu. So, go easy on me, okay? :D
My problem is I can't set resolution higher than 800x600.
And I found out that my xorg.conf is missing, is that normal?
I'm using Ubuntu 10.10 on VM VirtualBox.
Hope you guys can solve my problem.
Thanks!

---

### Post by sikander3786 on 2010-12-15
Welcome to the forums :-)

Vmware and Virtualbox are 2 different things.

Install Guest Additions if you've got Virtualbox.

[http://www.virtualbox.org/manual/ch04.html](http://www.virtualbox.org/manual/ch04.html)

Or VMware Tools if it is VMware.

[http://www.vmware.com/support/ws55/doc/new_guest_tools_ws.html](http://www.vmware.com/support/ws55/doc/new_guest_tools_ws.html)

And modern X deals directly with the graphics stuff. You might not have an xorg.conf by default unless you create it yourself. But you need not to...

---

### Post by immabamboo on 2010-12-16
I've install the Guest Additions. But I still cannot set the resolution higher than 800x600.

---

### Post by ivicks on 2010-12-16
When I installed BackTrack 4 in Virtual Box I had to raise my video memory to 32MB. Once you do this you should be able to change the screen resolution.

---

### Post by gmargo on 2010-12-16
I have the same 800x600 situation with VirtualBox but fixed it just now by installing a few packages.

Host: 64-bit 10.10 Maverick (kubuntu)
Guest: 64-bit 10.10 Maverick (xubuntu)

On the Guest machine (with default 12M memory for the display adapter), all I did was install these packages: dkms, virtualbox-ose-guest-dkms, virtualbox-ose-guest-x11.  I did not use the VBoxGuestAdditions.iso file.

After rebooting the Guest, it's X display matched the size of the window.  And resizing the window just works - it trickles down to the Guest X display somehow.

---

### Post by immabamboo on 2010-12-16
I've raised my video memory to 128mb which is the max and my ram to 1000mb.
I still can't raise the resolution.

---

### Post by mikkatterina on 2010-12-17
look in /root, run it again and read the instructions!And check for other errors in it.

---

