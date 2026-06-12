---
title: "Cannot Remove Printer"
date: 2006-09-22
forum: Desktop Environments
---

### Post by Monkus on 2006-09-22
Hello. I have been back and forth trying to get my ubuntu laptops to print to the printer attached to my Mac. No problem. They print now. My problem is that I cannot remove the improperly configured printers from previous tries. I have an icon in the upper right near the clock showing one of the misconfigured printers and says ready. When I use the gnome-cups-manager I click remove printer and it just stays there. Any suggestions?

---

### Post by windwalker78 on 2006-10-24
> **Monkus said:**
> Hello. I have been back and forth trying to get my ubuntu laptops to print to the printer attached to my Mac. No problem. They print now. My problem is that I cannot remove the improperly configured printers from previous tries. I have an icon in the upper right near the clock showing one of the misconfigured printers and says ready. When I use the gnome-cups-manager I click remove printer and it just stays there. Any suggestions?

I have the same problem. I installed KDE in order to try removing it from there. Now I got a message client-error-not-found. ](*,) . Tried from localhost:631. When I press delete I get "Forbidden"

---

### Post by purity control on 2006-12-16
open up a terminal and simply type :[INDENT]```
 sudo lpadmin -x [COLOR=Red]printername[/COLOR]
```[/INDENT]where [COLOR=Red]printername[/COLOR] is the name of the printer that you want to remove

---

### Post by Kossilar on 2008-03-16
> open up a terminal and simply type :

    Code:

     sudo lpadmin -x printername

where printername is the name of the printer that you want to remove

This is why the terminal is awesome. No messing around when it comes to getting things done. Gnome-cups-manager was refusing to accept my password. This got the job done in a hurry. 

Thanks Purity Control.

---

