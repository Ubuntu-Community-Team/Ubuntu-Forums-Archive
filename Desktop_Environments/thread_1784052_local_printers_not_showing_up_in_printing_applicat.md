---
title: "local printers not showing up in printing application"
date: 2011-06-16
forum: Desktop Environments
---

### Post by Z.K. on 2011-06-16
I was trying to add a virtual PDF printer and show I installed cups-pdf.  Supposedly it is supposed to list the virtual pdf printer in the System->Administration->Printing dialog when I choose Add printer.  But it does not do that.  All it shows is the remote printers on my file server.  

So, opened up a web browser and when to localhost:631 and used the cups interface to add a virtual pdf printer, but still it does not show up in the printing dialog.  Anyone have any ideas as to why?

:confused:

---

### Post by Z.K. on 2011-06-16
> **Z.K. said:**
> I was trying to add a virtual PDF printer and show I installed cups-pdf.  Supposedly it is supposed to list the virtual pdf printer in the System->Administration->Printing dialog when I choose Add printer.  But it does not do that.  All it shows is the remote printers on my file server.  

So, opened up a web browser and when to localhost:631 and used the cups interface to add a virtual pdf printer, but still it does not show up in the printing dialog.  Anyone have any ideas as to why?

:confused:

Well, I figured it out.  Under Server there is a connect item.  Then instead of the remote machine I typed in localhost and the PDF printers are there now.  Any ideas how to show both remote and local printers at the same time.

:?:

---

### Post by Z.K. on 2011-06-16
> **Z.K. said:**
> Well, I figured it out.  Under Server there is a connect item.  Then instead of the remote machine I typed in localhost and the PDF printers are there now.  Any ideas how to show both remote and local printers at the same time.

:?:

Well, maybe not.  While it does display the PDF printers when going to server and typing in localhost, the PDF printers are not available to any of my applications.

:?

---

