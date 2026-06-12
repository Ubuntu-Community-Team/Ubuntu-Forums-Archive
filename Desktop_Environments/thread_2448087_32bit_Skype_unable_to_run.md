---
title: "32bit Skype unable to run"
date: 2020-08-01
forum: Desktop Environments
---

### Post by jankohrasko142 on 2020-08-01
Hello team, 
please advise.

There are some old info 2017/2018 about no 32bit skype version. Also, software center or snap is recommended for skype installation.

However, software center does offer skype 32bit, installation successful. See attached screenshots.
Even the official skype page redirects you to snapcraft.io where you can select skype 32bit and install.
Also, when installing from cli, the installation is successful.

However, I am unable to run the skype.
When running from cli, there is no output.
There is no skype process.

I am newbie, could anyone advise please ?

*xubuntu 18.04, 32bit, Intel atom, an older netbook.*

---

### Post by grahammechanical on 2020-08-01
From your screen shots I see that you have installed the snap version of Skype. The advantage of a snap application is that all the necessary libraries are installed and confined with the application. They do not conflict with the libraries used by the operating system.

Some times when a snap application is installed additional settings become available when we look at the application in the software centre/app store. Snap applications are usually confined having limited access to personal files and system resources. But this Skype snap is unconfined. It can access the personal files and all system resources.

You may need to find a setting and give permission for what the application can access. You may also need to access the sound settings and select this application as both a input source and an output source.

Regards.

---

### Post by monkeybrain20122 on 2020-08-01
What Ubuntu version is that? The repository (Canonical-partners) stopped providing skype for many years, now the easiest way is to get the .deb from its own [website]("https://www.skype.com/en/get-skype/") and skype has stopped supporting 32 bit for many years.

---

