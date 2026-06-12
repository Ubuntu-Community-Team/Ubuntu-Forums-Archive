---
title: "Help: Waydroid"
date: 2024-10-19
forum: Desktop Environments
---

### Post by BeachNerd on 2024-10-19
I installed waydroid on Ubuntu 24.04.1 LTS, using: the instructions here: [https://docs.waydro.id/usage/install-on-desktops]("https://docs.waydro.id/usage/install-on-desktops")
.

Install appears to go OK, however, the inialization process fails due to a security certificat failure (see below):

[IMG]https://i.imgur.com/cvOV0gM.png[/IMG]

Waiting for waydroid container service...
Downloading [https://sourceforge.net/projects/waydroid/files/images/system/lineage/waydroid_x86_64/lineage-18.1-20241019-VANILLA-waydroid_x86_64-system.zip/download](https://sourceforge.net/projects/waydroid/files/images/system/lineage/waydroid_x86_64/lineage-18.1-20241019-VANILLA-waydroid_x86_64-system.zip/download)
<urlopen error [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed: self-signed certificate in certificate chain (_ssl.c:1000)>

Anyone have suggestions on how to resolve?

---

### Post by grahammechanical on 2024-10-19
What version of Ubuntu do you have? The documentation only lists Ubuntu up to 24.04 (noble). I have installed Waydroid following the instructions under "Ubuntu/Debian and Derivatives." It should put an icon in what I call the Grid. (on 24.04 the Grid icon is now the circle of friends icon).

Clicking on the Waydroid icon should start the loading of the Android phone operating system. We now have several Android phone apps in the grid. To install additional Android apps open the terminal and CD into the directory/folder you have the apk file in and run

```
waydroid app install xyz.apk
```

That should put an icon for the app in the grid. My method of working is to open the Android phone OS and then load the special app that I have installed. If you find that the app does not load or Android crashes then reboot and start again. That seems to fix things.

By the way, did you install the pre-requisites? And the official repository?

Regards

---

### Post by BeachNerd on 2024-10-19
Ubuntu 24.04.1 LTS. Yes, I installed everything as per the Ubuntu install instructions at; [https://docs.waydro.id/usage/install-on-desktops]("https://docs.waydro.id/usage/install-on-desktops")

The app installed and I see it but it needs to be initialized first and that where things break down.

---

### Post by grahammechanical on 2024-10-20
I am not sure what to say. Sorry. I have recently installed Ubuntu 24.04 LTS on an external SATA drive. I intend to install WayDroid. I have been trying to get Wine working effectively. But I will do that install of WayDroid and take note of what I am doing and see what the results are.

Regards

---

### Post by grahammechanical on 2024-10-20
Well, I am back. I had no problems installing WayDroid on Ubuntu 24.04 LTS. I followed the instructions and clicked the WayDroid icon and authorised the download to initialize WayDroid. It was able to connect to sourceforge.net and download a 788.74 MB zip file and extract it. Then it downloaded a 181.82 MB  zip file. I then rebooted and on clicking the WayDroid icon the Android phone OS loaded.

You are unable to connect to sourceforge.net. I suggest that you try installing again the ca-certificates.

> sudo apt install curl ca-certificates -y

See what happens. Regards

---

### Post by BeachNerd on 2024-10-21
> **grahammechanical said:**
> Well, I am back. I had no problems installing WayDroid on Ubuntu 24.04 LTS. I followed the instructions and clicked the WayDroid icon and authorised the download to initialize WayDroid. It was able to connect to sourceforge.net and download a 788.74 MB zip file and extract it. Then it downloaded a 181.82 MB  zip file. I then rebooted and on clicking the WayDroid icon the Android phone OS loaded.

You are unable to connect to sourceforge.net. I suggest that you try installing again the ca-certificates.



See what happens. Regards

OK.  I think I know what's going on.  When I posted this help question yesterday, I was in a coffee shop and I think something in the coffee shop firewall was preventing the download.  I'm now at home and I did try reinstalling the certificats and got a message tha the most recent certificats are already installed.  In any case, I re-ran the initialization program and it downloaded the two files and is extracting.  There's no indication if the extraction is still in progress or if it's finished.  I'll give it a while and reboot.  Thanks for your help with this.

---

### Post by BeachNerd on 2024-10-21
Well.  That didn't work.  I rebooted and whenI opened waydroid the initialization dialog came up again.  When I select 'Download' I get:

Waiting for waydroid contaner service...
The waydroid contaner service is not listening.   

When I try to start the container service I get:

Error: Waydroid container service is slready running.

---

### Post by BeachNerd on 2024-10-21
I uninstalled waydroid, then reinstalled and reinitialized, and now it seems to be working.  Thanks again for your help with this.

---

