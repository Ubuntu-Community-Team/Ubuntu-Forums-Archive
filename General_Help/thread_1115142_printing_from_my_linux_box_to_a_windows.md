---
title: "printing from my linux box to a windows"
date: 2009-04-03
forum: General Help
---

### Post by dagarshali on 2009-04-03
Hi all,
I am very new to ubuntu and I have installed 8.10 and I like it a lot. However, I am having issues with printing it to network printer.

Here is how is used to do it on windows..

Start-->Run //print2.eng.test.edu
and i would enter test/vishwa for user id and then the password..

A window would pop an i would double click the printer that i want and that's it.

How do I accomplish the same thing on ubuntu.
Here is what i could get from the printer info...

Computer name: print2.eng.test.edu
computer type: windows server
domain : test (same as the test in computer name)

Also, when i when checked the properties of the printer( after i double click a particular printer as described above in windows box)
Name: sw2126
in the ports tab, i see 10.10.4.25:10.10.4.25

---

### Post by mb_webguy on 2009-04-03
Go to System->Administration->Printing.  Click New.  In the Configuration dialog, select "Windows Printer via SAMBA" in the left pane.  Now on the right, click the Browse button and locate the printer.  Click Forward.

Select the "Select printer from database" radio button if it's not already selected, and choose the printer manufacturer from the list.  Click Forward.

Now in the left pane, select the printer model.  In the right pane, select the driver to use.  Generally, the one marked "(recommended)" is the one you want.  Click Forward.

Give the printer a name, description, and location if you want, then click Apply.

----------------

If you don't see your printer model listed, you could try going back to the screen where you selected "Select printer from database", and selecting "Provide PPD file" instead.  Then you can try to locate the PPD file on the printer driver installation disc for Windows, if you have one.

Otherwise, you may have to select "Generic" from the "Select printer from database" list, and try one of the drivers on the following screen.  Unfortunately, not all manufacturers support Linux as well as others.

You may also see if the manufacturer has a printer driver available for download from their website, but generally if one is available, it will be in the previously mentioned list.

---

