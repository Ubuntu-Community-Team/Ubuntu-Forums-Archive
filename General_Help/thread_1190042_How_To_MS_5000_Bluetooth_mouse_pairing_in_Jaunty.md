---
title: "How To: MS 5000 Bluetooth mouse pairing in Jaunty"
date: 2009-06-17
forum: General Help
---

### Post by justhamade on 2009-06-17
[LIST=1]
[*]Put the mouse into pairing mode
[*]Use the wizard to pair the mouse using 0000 secrect
[*]Finish the wizard but notice that the pairing light is still blinking
[*]Open a terminal and run "sudo apt-get install bluez-compat"
[*]Then run "sudo hidd --search"
[*]The mouse should be found the the blinking light will go out :)
[/LIST]

Reference: [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/343727]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/343727")

---

### Post by Annoying Moose on 2009-06-23
This solution also works in Linux Mint 7 (Gloria).  I would assume that it works in all operating systems based on Ubuntu 9.04.

---

