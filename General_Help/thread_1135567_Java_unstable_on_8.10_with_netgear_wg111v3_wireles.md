---
title: "Java unstable on 8.10 with netgear wg111v3 wireless usb"
date: 2009-04-24
forum: General Help
---

### Post by Mark Porter on 2009-04-24
Hi,

I installed a driver (compact-wireless-2.6) for my netgear wg111v3 wireless usb card. My wireless now works fine, however, Java makes my computer unstable. I am running sun Java 6 and everytime I run an application that uses Java or go to a website that uses Java, my computer freezes. It is extremely difficult to browse the web with this problem. Does anyone have any solutions to this instability?

Thanks,
M

---

### Post by paradigm2 on 2009-04-24
> **Mark Porter said:**
> Hi,

I installed a driver (compact-wireless-2.6) for my netgear wg111v3 wireless usb card. My wireless now works fine, however, Java makes my computer unstable. I am running sun Java 6 and everytime I run an application that uses Java or go to a website that uses Java, my computer freezes. It is extremely difficult to browse the web with this problem. Does anyone have any solutions to this instability?

Thanks,
M

Are you sure Sun Java is actually being useed by default in the system and also within Firefox?

In a terminal:

```

java -v

```

and

```

sudo update-java-alternatives -s java-6-sun

```

Ought to ensure that sun java is being used by your system as well as Firefox I believe.  (The second command will alter things, the first one will only display the java version)

---

### Post by Mark Porter on 2009-04-25
Hi,

Thanks for your response! I tried the two commands:

$java -showversion
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Client VM (build 11.0-b15, mixed mode, sharing)

The second command runs with a bunch of messages (I can post those if you want). 

Synaptic shows that I have sun-java6-bin and sun-java6-jre installed.

After running the commands I find that Java is still unstable on my machine as long as I am using the wireless usb card. Any suggestions?

Thanks!

---

