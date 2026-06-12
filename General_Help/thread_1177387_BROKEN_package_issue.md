---
title: "BROKEN package issue"
date: 2009-06-03
forum: General Help
---

### Post by nomad421 on 2009-06-03
Hello,

  I tried to update this morning and ran into a fairly unpleasant surprise.  I'd done a sudo-aptitude update and sudo aptitude dist-upgrade.  I was greeted with the following:

> 
The following packages have unmet dependencies:                                                                                                               
  krdc: Depends: libqt4-dbus (>= 4.5.1) but 4.5.0-0ubuntu4.1 is installed.                                                                                    
        Depends: libqt4-network (>= 4.5.1) but 4.5.0-0ubuntu4.1 is installed.                                                                                 
        Depends: libqt4-svg (>= 4.5.1) but 4.5.0-0ubuntu4.1 is installed.                                                                                     
        Depends: libqt4-xml (>= 4.5.1) but 4.5.0-0ubuntu4.1 is installed.                                                                                     
        Depends: libqtcore4 (>= 4.5.1) but 4.5.0-0ubuntu4.1 is installed.                                                                                     
        Depends: libqtgui4 (>= 4.5.1) but 4.5.0-0ubuntu4.1 is installed.                                                                                      
  krfb: Depends: libqt4-dbus (>= 4.5.1) but 4.5.0-0ubuntu4.1 is installed.                                                                                    
        Depends: libqt4-network (>= 4.5.1) but 4.5.0-0ubuntu4.1 is installed.                                                                                 
        Depends: libqtcore4 (>= 4.5.1) but 4.5.0-0ubuntu4.1 is installed.                                                                                     
        Depends: libqtgui4 (>= 4.5.1) but 4.5.0-0ubuntu4.1 is installed.                                                                                      
  kde-zeroconf: Depends: libqt4-dbus (>= 4.5.1) but 4.5.0-0ubuntu4.1 is installed.                                                                            
                Depends: libqt4-network (>= 4.5.1) but 4.5.0-0ubuntu4.1 is installed.                                                                         
                Depends: libqt4-svg (>= 4.5.1) but 4.5.0-0ubuntu4.1 is installed.                                                                             
                Depends: libqt4-xml (>= 4.5.1) but 4.5.0-0ubuntu4.1 is installed.                                                                             
                Depends: libqtcore4 (>= 4.5.1) but 4.5.0-0ubuntu4.1 is installed.                                                                             
                Depends: libqtgui4 (>= 4.5.1) but 4.5.0-0ubuntu4.1 is installed.                                                                              

...
...
...

 


This foolishness goes on for a while.  It seems like the newer packages want Qt-4.5.1, but that the current repo only has Qt-4.5.0.  I'm getting the latest packages from "deb [http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu) jaunty main", if that's of any help.  Any assistance you could send my way would be great!  Thanks for your time.

---

### Post by nomad421 on 2009-06-03
*bump*?

---

