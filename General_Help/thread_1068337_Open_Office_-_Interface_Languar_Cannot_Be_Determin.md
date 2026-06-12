---
title: "Open Office - Interface Languar Cannot Be Determined"
date: 2009-02-12
forum: General Help
---

### Post by RobSoko315 on 2009-02-12
Hey,

My Open Office 3.0 suddenly just stopped working.  It was fine earlier today.  When I start up Open Office I get the following message:

"The application cannot be started.  The user interface language cannot be determined"

This is Open Office 3.0 from the Ubuntu repository.  I tried uninstalling and reinstalling, but I get the same message.

I have viewed similar threads, but have not found a solution.

Thanks for any help

Rob.

---

### Post by RobSoko315 on 2009-02-12
I figured it out.  If anyone has the same problem here's the solution.

Do

sudo nautilus

then, go to /home/<user name>/

right click ".openoffice"  make sure you can view hidden files

my permissions were set to root, so I set them accordingly.  

Make sure to click the button that applies those setting to enclosed folders as well.


Rob.

---

