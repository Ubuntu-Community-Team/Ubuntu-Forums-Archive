---
title: "What is the normal cpu temp for Inspiron 6400"
date: 2007-09-18
forum: Dell  Ubuntu Support
---

### Post by Monkey_Tales on 2007-09-18
What is the normal cpu temp for Inspiron 6400 and can this be changed.
My cpu's temp are around 60 degrees celcius in idle mode.
Is this to high or low or is this normal?

:confused:

---

### Post by nzlee34 on 2007-09-18
That does not sound unreasonable (my desktop averages around 50 degrees and varies by up to 10 depending on load). Are the fans running constantly? does their speed respond to the temperature?

---

### Post by jongkind on 2007-09-19
My 6400 idles at 49 deg.C. As soon as it hits 56 deg.C the fan starts to run faster.

---

### Post by neptho on 2007-09-19
Have you installed and enabled i8k?  With BIOS rev. A12, my fans would not come on automatically.  A14, they worked by themselves.  A15-A17, they're off again.

Quick reminder/Howto.  All lines starting with '%' mean "type this into a terminal" as your normal user.  '#' means you will have root access *be extremely careful when you are running as the root user*:

```
%sudo $SHELL
#echo 'i8k force=1' >> /etc/modules
#modprobe i8k force=1
#apt-get install i8kutils
#printf '#!/bin/sh\nPATH=/bin:/sbin:/usr/bin:/usr/sbin\n/usr/bin/i8kmon -a -d &' >> /tmp/rc
#cat /tmp/rc /etc/rc.local > /tmp/rc.local
#mv /tmp/rc.local /etc/rc.local
#chown root:root /etc/rc.local
#printf "set config(0) {{- 0} -1 35 -1 40}\nset config(1) {{- 1} 30 45 35 50}\nset config(2) {{- 2} 40 128 45 128}" > /etc/i8kmon
#chmod 755 /etc/rc.local
#chmod 644 /etc/i8kmon
#exit
%exit
```

Finally, start the daemon:
```
%sudo /usr/bin/i8kmon -a -d &
```

If you're curious about the information in the /etc/i8kmon file, or want to change the defaults (mine are set fairly low due to prior overheating), type 'man 1 i8kmon' at a terminal prompt after installation if i8kutils.

Edit: My older 6400 (ATI x1300, Core Duo, not Core 2.  1.6Ghz.  Idles at about 90f/23c w/ Kubuntu, normal X11 (not XGL; idles a bit lower with XGL, but I can't sleep my machine with it running.)  It will shoot up to 30c upon occasion, but then i8kmon will kick in my fan.

---

### Post by Linicks on 2007-09-19
You sure this is correct:
> 
#echo '/usr/bin/i8kmon -a -d &' >> /etc/rc.local

as my   /etc/rc.local  contains a 'exit 0'.

So here, >> adding the echo to the end will not work.

```
exit 0
/usr/bin/i8kmon -a -d &
```

Nick

---

### Post by misfitpierce on 2007-09-19
Laptop chips in general have very high heat resistance. 90 degrees celcius is boiling point generally on AMD and around same for Intel. While the laptop can probably handle this temp for a bit of time it's not good to get there. When you hit the 80+ celcius range thats when you shut off the laptop and give her a break. When and IF it happens.

---

### Post by neptho on 2007-09-19
> **Linicks said:**
> You sure this is correct:


as my   /etc/rc.local  contains a 'exit 0'.

So here, >> adding the echo to the end will not work.

```
exit 0
/usr/bin/i8kmon -a -d &
```

Nick

Good catch.  I was being lazy.  :)  

It needs to execute *before* the exit statement.

---

### Post by cheetaux on 2007-09-19
Excuse a dumb question, but how do you monitor the temperature?

---

### Post by jongkind on 2007-09-20
> **cheetaux said:**
> Excuse a dumb question, but how do you monitor the temperature?

You can try this from terminal:

watch acpi -V

---

### Post by Linicks on 2007-09-20
My Inspiron 6400 is 25c at idle.  Loading with glxgears and leaving for a few minutes, this rises to 39/40c.

Nick

---

