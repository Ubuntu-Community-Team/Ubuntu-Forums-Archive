---
title: "Unable to start the Citrix VDA services in my Ubuntu Master Image"
date: 2019-03-15
forum: Desktop Environments
---

### Post by tumumsc on 2019-03-15
I'm getting below error when I start the VDA services in my master ubuntu desktop.

Gsdfsd\rsdumu@gsdfsdsfasd01:~$ service ctxvda status
&#9679; ctxvda.service - Citrix VDA Service
   Loaded: loaded (/etc/systemd/system/ctxvda.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Fri 2019-03-15 16:30:25 EDT; 3s ago
  Process: 14205 ExecStart=/opt/Citrix/VDA/sbin/ctxvda (code=exited, status=1/FAILURE)
 Main PID: 14205 (code=exited, status=1/FAILURE)

VDA log says,

2019-03-15 16:30:25.468 [INFO ] [1] - ******************** Citrix Broker Agent - Start ********************
2019-03-15 16:30:25.470 [INFO ] [1] - Java version "10.0.2". OpenJDK Runtime Environment. OpenJDK 64-Bit Server VM (build 10.0.2+13-Ubuntu-1ubuntu0.18.04.4, mixed mode)
2019-03-15 16:30:25.470 [INFO ] [1] - The Citrix Desktop Service specification version is '7.5' and implementation version is '18.11.0.7'.
2019-03-15 16:30:25.477 [INFO ] [1] - The Citrix Desktop Service is starting.
2019-03-15 16:30:25.607 [INFO ] [11] - The Citrix Desktop Service is shutting down.
2019-03-15 16:30:25.613 [INFO ] [11] - The Citrix Desktop Service shut down successfully.


---

Thanks
Ravindra

---

### Post by TheFu on 2019-03-17
I haven't any clue about citrix, but normally, services must be started with **sudo**.

---

### Post by dieler on 2019-03-19
Currently, I am also trying to setup a Ubuntu 18.04 LTS Citrix VDA machine. It took me a few hours to get it up and running.

I cant say if this is the correct way, but it was the only solution for me that worked.

Your vda.log shows, that you are running Java version "10.0.2", which is not compatible with Citrix VDA. Therefore downgrade to the following version:

```
# java -version
openjdk version "1.8.0_191"
OpenJDK Runtime Environment (build 1.8.0_191-8u191-b12-2ubuntu0.18.04.1-b12)
OpenJDK 64-Bit Server VM (build 25.191-b12, mixed mode)
```

To change the java version, just install Java 8 and run the following to set the default java version:

```
update-alternatives --config java
```

From now on, ctxvda.service is running fine.


If you take a closer look at dmesg, you should see the following errors:

[  122.056521] usb_vhci_hcd: version magic '4.4.0-45-generic SMP mod_unload modversions ' should be '4.18.0-16-generic SMP mod_unload '
[  122.058715] usb_vhci_iocifc: version magic '4.4.0-45-generic SMP mod_unload modversions ' should be '4.18.0-16-generic SMP mod_unload '

To fix this problem, you have to compile VHCI-Kernelmodules **usb-vhci-hcd.ko** und [B]usb-vhci-iocif.ko.
[/B]You can follow the official Citrix Guide: [https://docs.citrix.com/de-de/linux-virtual-delivery-agent/current-release/configuration/configure-usb-redirection.html#erstellen-des-vhci-kernelmoduls](https://docs.citrix.com/de-de/linux-virtual-delivery-agent/current-release/configuration/configure-usb-redirection.html#erstellen-des-vhci-kernelmoduls)

While compiling I got one more error, which I had to fix... [B]"error ‘driver_attr_debug_output’ undeclared (first use in this function)"
[/B]The workaround is to disable debugging macro in the following files:

//#define DEBUG
- vhci-hcd-1.15/usb-vhci-iocifc.c
- vhci-hcd-1.15/usb-vhci-hcd.c

Now you are able to compile the kernelmodules. 

Last step is to reboot your machine, and everything should work as expected.
In your vda.log you should see something like "Registration successfull..."


I hope this is helpful and if you need help, just reply to my answer ;)

---

