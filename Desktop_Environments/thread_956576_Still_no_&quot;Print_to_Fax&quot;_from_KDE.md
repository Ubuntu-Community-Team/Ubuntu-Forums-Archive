---
title: "Still no &quot;Print to Fax&quot; from KDE"
date: 2008-10-23
forum: Desktop Environments
---

### Post by eurgain on 2008-10-23
I noted some time ago that the "print to fax" was not present in KDE4,1 and was sent rather rudely with the comment that it served me right for using a development version.

However, I now find that this option is still missing from Kubuntu 8.10 beta, which is supposedly feature-complete.

Has anyone any idea whether this option will re-appear, or whether there is another way to communicate with a Hylafax server from KDE 4.1.2 in a convenient and integrated manner?

Regards
A

---

### Post by JohnMoore on 2009-01-30
I can't specifically speak to Hylafax, but after installing efax and efax-gtk from Synaptic, I had to do a bit of research.

First, my modem is connected using a USB adaptor.  This showed up as /dev/ttyUSB0.  I found that by looking at the /dev directory before and after I plugged the device into the PC.

From Efax-gtk File->Settings menu, I configured the program, putting in the device address, setting it to "Run socket server", and setting the server to accept faxes from any computer on my subnet (10.1.*)

I created a /var/log/efax directory and set the permissions so that the program would be allowed to create files there.  All of these steps can be found in various documents found by Googling linux+"print-to-fax".

There was some stumbling around, because the documents I found regarding ubuntu were for earlier versions and Kubuntu 8.10 did not exactly match those descriptions.  Go to Applications->System->Printing.  Click "New Printer" and press the "New Printer" button.

In the next dialog, choose "App Socket/JetDirect" and fill out the dialog.  Host is localhost and Port number is 9900 (or whatever you assigned in the Efax settings).  Press the "Forward" button.  Select Generic for the driver and press "Forward."  On the next screen, select Raw Queue and press "Forward."

The final configuration screen allows you to name the printer (I called mine "Fax") and enter a description.  You're now done.  

When you attempt to send a fax, Efax pops up a dialog asking for the number to use.  It will be helpful to have the Efax-gtk frontend open as well, because of the ease in reading log messages.
  
I opened OpenOffice and printed a letter I had written to the Fax printer.  When the "number" dialog popped up, I put in the same number I was using for sending.  This might seem dumb, but it allows me to see all the log messages.  What you are hoping for is that you see no errors _until_ the modem says the line is already in use.  After you verify that everything else is OK, you can try faxing to a _real_ number where somebody can tell you how well it worked.

I'm still hunting for a way to automatically generate and place a "cover" sheet in the fax queue before the document, but just being able to get my fax setup working has made my day!

---

### Post by eurgain on 2009-03-09
Hi, John

I have just seen your reply.

The problem is that I need Hylafax because I have one telephone line with one modem but lots of computers on the network that need to send faxes.

Even with KDE 4.2.1, this is *still* a regression from 3.5.* .  I think that the KDE developers have just lost interest in faxing, and that it will not be implemented.

Meanwhile, I still assemble PDFs for faxing using pdftk, but I now use yajhfc to dispatch them to Hylafax.  This is still clunky compared with 3.5, but is quite usable.

Regards
A

---

