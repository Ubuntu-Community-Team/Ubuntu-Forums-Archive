---
title: "Can't enable Desktop effects"
date: 2011-02-07
forum: Desktop Environments
---

### Post by tekas1234 on 2011-02-07
Hey guys,
I have the following specs:
Processor:   AMD Athlon II X4 620 processor @2.6GHz
Motherboard: GF615M-P33  (MS-7597)
Graphics card: ATI Radeon 5400
With an integrated nVidia graphic card too.

I can't enable my desktop effects. That is when I try to do so I get the error:
> Desktop effects can't be enabled.
by the Change Desktop Background.

lspci| grep VGA
returns:
> 02:00.0 VGA compatible controller: ATI Technologies Inc Device 68f9

What should I do?

---

### Post by sikander3786 on 2011-02-07
Welcome to the forums :-)

Did you install the proper graphics drivers for your card? See under System > Administration > Hardware Drivers/Additional Drivers.

Post the output of this command as well.

```
glxinfo | grep vendor
```

---

### Post by tekas1234 on 2011-02-07
> **sikander3786 said:**
> Welcome to the forums :-)

Thanks :)

> 
Did you install the proper graphics drivers for your card? See under System > Administration > Hardware Drivers/Additional Drivers.


There is no propriety driver installed. There is however an option to active the "ATI/AMD proprietary FGLRX graphics driver."

> 
Post the output of this command as well.

```
glxinfo | grep vendor
```


No output was generated, even used sudo.

---

### Post by wojox on 2011-02-07
> **tekas1234 said:**
> There is however an option to active the "ATI/AMD proprietary FGLRX graphics driver."

Activate it and reboot.

---

### Post by tekas1234 on 2011-02-07
SystemError: installArchives() failed

---

### Post by tekas1234 on 2011-02-07
I forgot to mention...I can run "Compiz Fusion icon" which runs Compiz Fusion.

---

### Post by sikander3786 on 2011-02-08
> **tekas1234 said:**
> SystemError: installArchives() failed
In regard to this post, can you please post the complete output of this command to let us see what is going on with package management.

```
sudo apt-get update && sudo apt-get upgrade
```

Basically, you need to install the ATI drivers from repositories and then you'll be able to use compiz.

---

### Post by stchman on 2011-02-08
Should just be a simple matter of enabling the proprietary ATI driver.

---

### Post by tekas1234 on 2011-02-12
> **stchman said:**
> Should just be a simple matter of enabling the proprietary ATI driver.

Like I said, can't enable it. :(

---

### Post by tekas1234 on 2011-02-12
> **sikander3786 said:**
> In regard to this post, can you please post the complete output of this command to let us see what is going on with package management.

```
sudo apt-get update && sudo apt-get upgrade
```

Basically, you need to install the ATI drivers from repositories and then you'll be able to use compiz.

Its been updating and upgrading for the past two hours. Can't wait for it to finish.:popcorn:

---

### Post by Forlong on 2011-02-12
Two hours? :-k
Are you that low on bandwidth or do you rarely update?

In any case, you can run [Compiz-Check]("http://forlong.blogage.de/article/pages/Compiz-Check") to see what the problem is, once updating is finished.

---

