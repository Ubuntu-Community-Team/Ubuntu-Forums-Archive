---
title: "Problems with Ubuntu 8.10 as a Virtual Box guest"
date: 2009-02-16
forum: General Help
---

### Post by Will Pittenger on 2009-02-16
I have a Virtual Box guest running Ubuntu 8.10.  It has problems with the Virtual Box Guest Additions.  Those are installed, but fail to initialize during boot.  I know that because I have it set to display messages during boot.  It lists the guest additions as having failed.

More recently, that VM has started doing some more odd behaviour just after I log in.  I see the wallpaper come up, but when I would expect the panels to appear, all I get is a cursor.  Right clicking on the desktop does nothing and I see no icons.  The Zip file attached contains my VM setup.

I have attempted to ask many, many times on IRC #ubuntu, but that channel has over one thousand users and everyone is too busy to even notice me.

---

### Post by rothalem on 2009-03-02
I have the same problem.

I am running a newly installed Ubuntu 8.10 guest on an XP home 32bit host.

Using a newly installed (installed over a previouse version) Virtual Box 2.1.4

I tried installing the guest additions using the ISO that comes with virtual box. I noticed it was not working so I looked on synaptic for virtualbox guest additions. When I install those the output contains the following (I have tried to reinstall it a number of times, each time it fails)

"
Setting up Virtual box-ose-guest-utils (2.0.4-dfsg-0ubuntu1)...
*Starting Virtual Additions
Error opening Kernal Mudule! r c = 2
  ...Fail!
"

I installed the Ubuntu 8.10 over an 8.4 installation (not updated, reformat) without recreating the virtual machine. I had virtualbox additions installed and working on the 8.4 guest. Not sure if that could cause a problem. 

Thanks for any help in advance,
Rothalem

---

### Post by rothalem on 2009-03-06
I solved my Problem, hope it helps with yours.

After installing everything that is related to virtualbox in the synaptics manager (still failing) I gave installing the guest additions from virtual box another go.

I mounted the iso, tried the VBoxLinuxAdditions-x86.run again, and noticed it needed root privileges to run. I used the command line and ran the file as sudo. VBoxadditions installed and Im all sweet.

Hope this helps with your problem.

Edit: I feel like such an idiot for missing it the first time round.

---

