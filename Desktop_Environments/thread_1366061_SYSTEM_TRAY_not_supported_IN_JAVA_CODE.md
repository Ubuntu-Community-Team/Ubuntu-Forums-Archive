---
title: "SYSTEM TRAY not supported IN JAVA CODE"
date: 2009-12-28
forum: Desktop Environments
---

### Post by anirudhtomer on 2009-12-28
Please help me out....

I am working on UBUNTU 9.10 GNOME version
& I am making a java project in netbeans 6.7.
The following code snippet gives me the result that the SYSTEM TRAY IS NOT SUPPORTED

import java.awt.*;

public class trayicon{
    
     public static void main(String args[]){  
         if(SystemTray.isSupported())
              System.out.println(" SYSTEM TRAY IS SUPPORTED");
         else
              System.out.println("SYSTEM TRAY IS NOT SUPPORTED");
     }
    
}

though I have added the "Notification Area" in the top & bottom panels of my system the problem persists.

Please Please help me out ....THANKS IN ADVANCE

---

### Post by wheadom on 2010-04-23
Hello,

I assume you have solved the problem by now. Anyway, I have just had this and found (from reading some other posts) that it is not happpy with desktop effects. I am using 9.04 and found that it only works if I set my desktop effects (System | Preferences | Appearance | Visual Effects) to None. I originally had it on Extra and so tried Normal, but that was no good (think I even rebooted), but then tried None and that worked.

Mark.

---

