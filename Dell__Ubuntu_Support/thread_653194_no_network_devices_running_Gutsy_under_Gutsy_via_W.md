---
title: "no network devices running Gutsy under Gutsy via WMware Workstation 6.02"
date: 2007-12-29
forum: Dell  Ubuntu Support
---

### Post by RobertGloverJr on 2007-12-29
I have a Dell 1420n that came factory installed with Feisty.  I used the DELL ISO to replace with Gutsy, which works fine-- I also installed all the Gusy updates and it still worked fine with the networking okay.

  Then I installed VMWorkstation 6.02 and installed Gutsy as a guest os.   

  The network connection of the guest Gutsy worked okay-- Firefox worked.  Then I did the ubuntu option to install all the Gutsy updates to the Guest.  All the updates downloaded via the network fine and it said the updates applied okay and I had to reboot.

    Since I rebooted the guest Gutsy I lost my networking.  I'm using the "NAT" network option of VMWARE as of course I should.

   The host Gutsy uses a wireless connection and Firefox continues to work fine.
   However in the guest Gutsy when I put the mouse over the network icon it says, "No network devices have been found".

    On the host Gutsy the connection info is:
interface:  Wireless Ethernet (eth1)
... snip
Drive:  ipw3945
etc. etc.


   I have no idea how to proceed.  Please, all suggestions welcomed.

---

### Post by RobertGloverJr on 2007-12-29
(additional info)

  In the Guest Gutsy when I type "ifconfig" it only shows info for "lo", i.e., 127.0.0.1,  and nothing else.

 In the Host Gutsy when I type "ifconfig" it shows "eth0", "eth1", "lo", "vmnet1", and vmnet8" and everything looks good.

   Also I forgot to mention that I installed VMWARE tools into the Guest Gutsy. That install went fine, and I could still use Firefox to access the internet after that install.  It was only after I applied the Gutsy updates and rebooted that the guest network disappeared.

    Also, I used the DELL ISO of Gutsy for the Host Gutsy, but I used a plain vanilla Gutsy CD (or is it a DVD) for the Guest Gutsy install that I bought for $1.00 on the internet-- it's the official Gutsy install CD (or is it a DVD).

---

### Post by mayankk on 2008-02-19
were you able to solve the problem?

---

