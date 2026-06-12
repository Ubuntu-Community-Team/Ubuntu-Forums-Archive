---
title: "Cannot print to printer, but to PostScript"
date: 2005-03-25
forum: Desktop Environments
---

### Post by beeldings on 2005-03-25
I don't know how to describe this other than by stating that I cannot print any documents or web pages. I was having trouble printing web pages from Firefox, but nothing would print. My printer used to initialize as it would normally do when it would prepare itself for printing, but it doesn't even do that. I thought the problem was related to Firefox itself, so I chose to print the page to a PostScript file. While I was able to create the PostScript file and load it using Gnome Ghostview, I was unable to print it using my printer. I received an error stating that it was unable to load the print command.

My printer is detected properly in the gnome-cups-manager (System -> Administration -> Printing) and the power supply and printer cable are properly connected and secured. I am using an older HP DeskJet 600C and I have been able to print using that device previously under Windows and as recently as under Warty Warthog and under the Hoary Hedgehog Preview prior to upgrading my system last night with "sudo apt-get upgrade". Also, the printer itself is connected to the system via the LPT or parallel port and I am using the DeskJet-600/600C driver.

Any help will be appreciated as I have a few very important documents that I need to print this afternoon.




EDIT: After a visit to LinuxPrinting.org, I removed the printer from my system and reinstalled it using the driver suggested by this page. Everything works again.

---

### Post by wernst on 2005-03-25
This will really help.

Use Synaptic to install "gtklp"

Then set the print command in Firefox (or Opera, or Acrobat, or whatever isn't printing right) and change the print command from "/usr/bin/lp" to "gtklp" instead.

Now when you print, you'll get a friendly dialog box that has ALL the CUPs printing options. It works great for everything.

-Warr

---

### Post by ploosh on 2005-03-25
Warr,
Does this solution allow for network printing administration tasks via CUPS ([http://localhost:](http://localhost:) )? I get a message across the top of my menu that says:
[indent]Administrative tasks have been disabled for security reasons. Please use Menu System > Administration > Printing.
[/indent] Even if I create a root user/pass, the admin dialogue doesn't accept it.
Any thoughts?

---

### Post by wernst on 2005-03-25
gtklp doesn't let you do password stuff for network printing. Check the Warty Howto forum, in the Unofficial Guide thread for how to set network printing with passwords. I wrote about it a few weeks ago, and it can be done.

You can also manually edit /etc/cups/printers.conf to add names and passwords (which work after rebooting). Note that in Hoary, you need to have the same workgroup name set in the Sharing applet. It wasn't necessary in Warty.

-warr

---

