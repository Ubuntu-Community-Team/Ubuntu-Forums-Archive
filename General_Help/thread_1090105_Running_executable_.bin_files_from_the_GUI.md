---
title: "Running executable .bin files from the GUI?"
date: 2009-03-07
forum: General Help
---

### Post by Silvestro Fantacci on 2009-03-07
Is there a reason for which .bin files should not run when double clicking their icon on the Ubuntu desktop (or in Nautilus)?

I downloaded a .bin file (from [http://www.qtsoftware.com/downloads](http://www.qtsoftware.com/downloads), for installing Qt SDK) to my Ubuntu desktop.

On double clicking the icon, it complains that the file cannot be displayed because there is no application associated with it.

Changing the file properties to make it executable does not make any difference.

However if the file's extension is changed for instance to .bin2, then the file will execute.

If I select the .bin file Properties --> Open With --> Add --> Use a custom command --> gksudo, then all the .bin files would run when double clicked, so with this I could bypass the issue once and for all.

But then I'm not sure... am I bypassing an intentional restriction that is placed on .bin files for some reason?

The other thing that's a bit strange is that if .bin files are associated with the gksudo command, then they will execute when double clicked even if their properties indicate that they are not allowed to execute.

---

### Post by dcstar on 2009-03-07
> **Silvestro Fantacci said:**
> Is there a reason for which .bin files should not run when double clicking their icon on the Ubuntu desktop (or in Nautilus)?
........

Most things need root privileges to install since they (usually) write to areas that are not available to users. As you found out, using gksudo allows them to install.

If you tried to run the same file in a terminal you would probably see the error message that it terminates with, on the desktop there is no terminal window for you to see this.

PS: Just because something has a ".bin" extension does not mean that it is an install file, the file extension can mean anything and the desktop has a default action for this file type for just one of the many possibilities.

---

### Post by sanus|art on 2009-03-08
It needs to be executable: run 'chmod u+x bin_filen_name.bin' or right click -> properties -> permissions -> mark the 'allow executing file as a program'. Than you can double click.

---

### Post by Gyanos422 on 2010-12-14
> **sanus|art said:**
> It needs to be executable: run 'chmod u+x bin_filen_name.bin' or right click -> properties -> permissions -> mark the 'allow executing file as a program'. Than you can double click.

Why didn't anyone just say that to begin with...

When i tried to do it through terminal it gave me an error. when i went to properties, it worked like i expected it SHOULD

---

