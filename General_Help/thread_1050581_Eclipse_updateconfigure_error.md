---
title: "Eclipse update/configure error"
date: 2009-01-25
forum: General Help
---

### Post by archeryguru2000 on 2009-01-25
I've been trying to update my eclipse for about week now.  I just installed eclipse for the first time a couple of weeks ago.  Decided to update/configure to add PyDev and C/C++ tools.  Upon updating I'm greeted with the following message.

```

The current configuration contains errors and this operation can have unpredictable results.
  Eclipse BIRT Chart Runtime Feature (2.1.2.v20070205-1728) requires feature "org.apache.commons.codec (1.3.0)", or later version.
  Eclipse BIRT Report Designer Framework (2.1.2.v20070205-1728) requires plug-in "org.eclipse.draw2d (3.2.0)", or compatible.
  Eclipse BIRT Chart Framework (2.1.2.v20070205-1728) requires feature "org.apache.commons.codec (1.3.0)", or later version.
  Data Tools Platform SQL Development Tools (0.9.1.200609201) requires feature "org.eclipse.gef (3.2.0)", or compatible.
  Data Tools Platform Model Base (0.9.1.200609201) requires feature "org.eclipse.emf (2.1.0)", or later version.
  Eclipse BIRT Report Designer Feature (2.1.2.v20070205-1728) requires plug-in "org.eclipse.tomcat (4.1.130)", or compatible.
  Eclipse BIRT Report Runtime Feature (2.1.2.v20070205-1728) requires plug-in "org.eclipse.tomcat (4.1.130)", or compatible.
  Eclipse BIRT Example (2.1.2.v20070205-1728) requires plug-in "org.eclipse.tomcat (4.1.130)", or compatible.
  Data Tools Platform Open Data Access Designer (0.9.1.200609201) requires feature "org.eclipse.emf (2.1.0)", or later version.

```

I'm not quite sure what to make of this.  :-k  Is there somewhere I can go to acquire these prereq's?  There's actually a button one can click after receiving this message that states <select required>, but that does absolutely nothing.  I would assume that this option should... hmmm, select the required packages.  But obviously I'm mistaken.  Anyway, if anybody has dealt with this before, I'd greatly appreciate a step in the right direction.

FYI, I'm using Ubuntu 8.10, Eclipse 3.2

Thanks,
~~archery~~

---

### Post by prachueb on 2009-11-01
Go to Help => Install New Software
At the new pop up window click Add button
At another new pop up window fill
Name: Galileo
Location: [http://download.eclipse.org/releases/galileo](http://download.eclipse.org/releases/galileo)
Click OK

After eclipse retrieve all the available features, you can select it and install as you wants.

Then your check for updates via Help => Check for Updates 

cheers

---

### Post by archeryguru2000 on 2009-11-29
Sorry, I didn't report on my own thread.  I had eventually removed all eclipse software and reinstalled.  This actually cleared up everything.  I assume something must not have installed correctly... or something similar to that.  But thanks for the suggestion.

~~archery~~

---

