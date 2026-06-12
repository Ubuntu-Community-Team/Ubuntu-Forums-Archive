---
title: "compiz disabled after upgrade"
date: 2009-06-28
forum: Desktop Environments
---

### Post by Mia1990 on 2009-06-28
Hello all,

upgraded my laptop last night and when i logged in this morning compiz was not working i did a upgrade so the setting should have carried over.i have check and compiz and the setting manager is installed  the hardware nvidia driver 173 is installed and working. 
help

---

### Post by overdrank on 2009-06-28
> **Mia1990 said:**
> Hello all,

upgraded my laptop last night and when i logged in this morning compiz was not working i did a upgrade so the setting should have carried over.i have check and compiz and the setting manager is installed  the hardware nvidia driver 173 is installed and working. 
help

Hi and do you mean updated or upgraded? Upgraded meaning from Intrepid 8.10 to Jaunty 9.04?
Have you tried starting compiz from the terminal?

---

### Post by Mia1990 on 2009-06-28
> **overdrank said:**
> Hi and do you mean updated or upgraded? Upgraded meaning from Intrepid 8.10 to Jaunty 9.04?
Have you tried starting compiz from the terminal?
I'm sorry upgraded  i do not know how to do it from the terminal

---

### Post by overdrank on 2009-06-28
> **Mia1990 said:**
> I'm sorry upgraded  i do not know how to do it from the terminal

Ok just open up a terminal, located under applications, accessories. Then enter the command compiz. If you receive any errors this may help.

---

### Post by Mia1990 on 2009-06-28
ok thanks that was easy here is what i got

mia@mia-laptop:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2562' found 
aborting and using fallback: /usr/bin/metacity

---

### Post by overdrank on 2009-06-28
Ok are you sure that the nvidia driver is working? You may try and use the nvidia settings and also have a look at [compiz-check]("http://ubuntuforums.org/showthread.php?t=799070").

---

### Post by Mia1990 on 2009-06-28
under hardware drivers it says it is i did some checking and this pc doesn't come with a nvidia card that has really got me confused as to why the driver is installed.

---

### Post by Mia1990 on 2009-06-28
ok compiz is working now this is how i fixed it

i took this line in bold

# blacklist based on the pci ids 
# See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
#T="$T 8086:2e02 " # Intel Eaglelake
**T="$T 8086:3577 8086:2562 " # Intel 830MG, 845G (LP: #259385)**
BLACKLIST_PCIIDS="$T"

and made this

# blacklist based on the pci ids 
# See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
#T="$T 8086:2e02 " # Intel Eaglelake
**#T="$T 8086:3577 8086:2562 " # Intel 830MG, 845G (LP: #259385)**
BLACKLIST_PCIIDS="$T"


Thank you all
Mia
xoxo

---

### Post by Mia1990 on 2009-06-28
oh i forgot i have seen forums marked solved but i don't see anywere to do that how is it done

---

