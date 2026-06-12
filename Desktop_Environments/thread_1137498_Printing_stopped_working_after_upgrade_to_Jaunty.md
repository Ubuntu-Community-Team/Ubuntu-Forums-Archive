---
title: "Printing stopped working after upgrade to Jaunty"
date: 2009-04-25
forum: Desktop Environments
---

### Post by Tilex on 2009-04-25
Hi guys,

I upgraded to Jaunty yesterday (from Intrepid 64-bit), and there have been quite a few headaches since then.

The one I'm reporting now is about printing.  I have a Dell color laser printer 1320c that was working nicely but has stopped to.

I tried to go to System -> Printer Configuration and I got this message that appears instead of shoing me the KDE app to configure my printing environment :

> Configure local and remote Printers
The shared library was not found.Librabry "kpythonpluginfactory" not found

Possible reasons :
[LIST]
[*]An error occured during your last KDE upgrade leaving an orphaned control module
[*]You have old third party modules lying around
[/LIST]

Check trhese points carefully and try to remove the module mentined in the error message.  If this fails, consider contacting your distributor or packager.

Any thought guys ?

---

### Post by Tilex on 2009-04-27
*achoo*

Sorry guys I sneezed ;o)

---

### Post by Tilex on 2009-04-27
My whole system broke after the upgrade to Jaunty so I just decided to re-format to 9.04. 

Now printing is good.

---

