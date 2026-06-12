---
title: "XP is quicker than Ubuntu 5.04..."
date: 2005-09-29
forum: Desktop Environments
---

### Post by ngms27 on 2005-09-29
I wrote the following little Java App and ran on both machines with minimal services running:

* Main.java
 *
 * Created on 29 September 2005, 09:16
 *
 * To change this template, choose Tools | Options and locate the template under
 * the Source Creation and Management node. Right-click the template and choose
 * Open. You can then make changes to the template in the Source Editor.
 */

package test;
import java.util.*;

/**
 *
 * @author ngms27
 */
public class Main {
    
    /** Creates a new instance of Main */
    public Main() {
    }
    
    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        // TODO code application logic here
        Date Start = new Date();
        long startime = Start.getTime();
        long endtime;
        long diff;
        long x;
        for (long i=1; i<=500000000; i=i+1)
        {
            
        }    
        Date End = new Date();
        endtime = End.getTime();
        diff = endtime - startime;
        System.out.println("Difference is: " + diff);
    }
    
}

This was then run on both XP and Ubuntu.

XP the scores are around 2200 - 2250 whilst on Ubuntu the scores are around 2500 - 2550

Am I wrong?

---

### Post by rjwood on 2005-09-29
> **ngms27]I wrote the following little Java App and ran on both machines with minimal services running:

* Main.java
*
* Created on 29 September 2005, 09:16
*
* To change this template, choose Tools | Options and locate the template under
* the Source Creation and Management node. Right-click the template and choose
* Open. You can then make changes to the template in the Source Editor.
*/

package test said:**
>  args) {
// TODO code application logic here
Date Start = new Date();
long startime = Start.getTime();
long endtime;
long diff;
long x;
for (long i=1; i<=500000000; i=i+1)
{

}    
Date End = new Date();
endtime = End.getTime();
diff = endtime - startime;
System.out.println("Difference is: " + diff);
}

}

This was then run on both XP and Ubuntu.

XP the scores are around 2200 - 2250 whilst on Ubuntu the scores are around 2500 - 2550

Am I wrong?

I don't intend to be disrespectful but, so what!!!!!!!!!!

---

### Post by Nadir on 2005-09-29
[quote=ngms27]Am I wrong?[/quote]

Very. You only tested a very pointless empty loop running inside a JVM. Whatever you're doing isn't testing anything O/S related (I/O, context switching, etc)
Also, did you use the same JVM on both systems ?

Tristan

---

### Post by Raeth on 2005-09-29
[QUOTE=Nadir]Very. You only tested a very pointless empty loop running inside a JVM. Whatever you're doing isn't testing anything O/S related (I/O, context switching, etc)
Also, did you use the same JVM on both systems ?

Tristan[/QUOTE]
Yup, and another effect would be how well Sun compiled the binaries of the JVM for the two OSes.

---

### Post by wisequark on 2005-09-29
also, were you using the sun compiler or the open J compiler?  that would have some effect as well.


remember - java was never built with insane speed in mind.  thats why most engineering fields still use C primarily.

Additionally, you begin timing before creating variables, etc.  This isn't an effective way of timing as that would be handled differently on every platform (activation record differences).  I'd create a class called timer and instantiate it directly before the loop.  Give it member functions like get_time that would subtract the time now from the time recorded initially and then return it to the main method (or print it out alternatively).  Do this directly before the for loop begins though.  Otherwise you aren't measuring performance, your measuring quirky behavior from one platform to the next.

---

