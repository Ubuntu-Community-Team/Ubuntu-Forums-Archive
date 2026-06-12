---
title: "HP Laserjet P1006 8.10 Support - Stopped Working"
date: 2008-12-04
forum: General Help
---

### Post by jcsteele on 2008-12-04
Hello all,

  I have a Laserjet P1006 laser printer (not color laser) - this use to work fine in 8.04 after I executed the "hp-setup" command.  Upon installing 8.10 it has worked without any extra work - just plug it in and go.  Suddenly it has stopped working now - I have tried issuing the "hp-setup" script again, but to no avail.  I have also rebooted, removed the printer and reinstalled it (removed the print queue), etc. but nothing...no printing as of right now.  This is strange because like I said it suddenly stopped working - it use to work fine!  Attached is a snippet of my /var/log/messages - hopefully someone can help out...need to print out lots of material, and this is holding me back.

tail -f /var/log/messages output while printing an ubuntu printer test page:
Dec  4 01:18:49 neuron kernel: [41162.751033] type=1503 audit(1228371529.286:15): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=7 name="/dev/tty" pid=6592 profile="/usr/sbin/cupsd"
Dec  4 01:18:49 neuron kernel: [41163.258317] type=1503 audit(1228371529.793:16): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=7 name="/dev/tty" pid=6597 profile="/usr/sbin/cupsd"
Dec  4 01:18:49 neuron foo2xqx-wrapper: foo2xqx-wrapper -t -r1200x600 -p1 -m1 -s7 -d1
Dec  4 01:18:51 neuron foo2xqx-wrapper: gs -sPAPERSIZE=letter -g10200x6600 -r1200x600 -sDEVICE=pbmraw -dCOLORSCREEN -dMaxBitmap=500000000  
Dec  4 01:18:51 neuron foo2xqx-wrapper: foo2xqx -r1200x600 -g10200x6600 -p1 -m1 -n1 -d1 -s7  -u 177x84 -l 177x84  -t     
Dec  4 01:21:41 neuron kernel: [41334.864126] type=1503 audit(1228371701.401:17): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=7 name="/dev/tty" pid=6838 profile="/usr/sbin/cupsd"
Dec  4 01:21:41 neuron kernel: [41335.347718] type=1503 audit(1228371701.881:18): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=7 name="/dev/tty" pid=6843 profile="/usr/sbin/cupsd"
Dec  4 01:21:41 neuron foo2xqx-wrapper: foo2xqx-wrapper -t -r1200x600 -p1 -m1 -s7 -d1
Dec  4 01:21:43 neuron foo2xqx-wrapper: gs -sPAPERSIZE=letter -g10200x6600 -r1200x600 -sDEVICE=pbmraw -dCOLORSCREEN -dMaxBitmap=500000000  
Dec  4 01:21:43 neuron foo2xqx-wrapper: foo2xqx -r1200x600 -g10200x6600 -p1 -m1 -n1 -d1 -s7  -u 177x84 -l 177x84  -t

P.S. cups is working fine I am assuming because I can still print to PDF files which I setup when upgrading to 8.10.  Thanks and any help is much appreciated.

---

