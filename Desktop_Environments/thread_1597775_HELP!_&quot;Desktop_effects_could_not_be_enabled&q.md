---
title: "HELP! &quot;Desktop effects could not be enabled&quot; after upgrade to Ubuntu 10.10"
date: 2010-10-15
forum: Desktop Environments
---

### Post by HQiu on 2010-10-15
The desktop visual effect cannot be activated  after I upgraded my Ubuntu 10.04 to 10.10. No matter "Normal", "Extra" or "Custom" option I selected in Visual Effects tab of the Appearance Preferences dialog box, the "can not be enabled" warning shows up. But I can enabled the Extra desktop visual effect under Ubuntu 10.04.
My video card is nVidia m105, and my laptop is Thinkpad SL400. I tried to add my user account to the "gdm", "video" etc, but I got the same error message.
So I came here to ask for your help.

---

### Post by HQiu on 2010-10-15
Also, I think I've updated the video driver to the latest version ("nvidia-current") using command "sudo apt-get update & sudo apt-get upgrade". I also installed the compiz using "sudo apt-get install compiz-*". But it seemed that was not working.

---

### Post by 3Miro on 2010-10-15
Try going to the hardware center (Sys -> Admin -> Hardware), then remove the Nvidia driver, reboot and activate the driver again.

---

### Post by HQiu on 2010-10-15
> **3Miro said:**
> Try going to the hardware center (Sys -> Admin -> Hardware), then remove the Nvidia driver, reboot and activate the driver again.
Thanks for your reply. I already did this before I went here, but that didn't help.

---

### Post by Bluebearbevis on 2010-10-15
Hello,

I too reached this point.  Then I went to Ubuntu Tweak and enabled x Updates stable.  It gave me 5 nVidiia driver updates which I installed.  Alas, to not avail.  In a related issue, even though additional drivers tells me it is installed and activated, extras won't work in visual effects.  Is this one of those just waits?
Thanks,  Richard

---

### Post by HQiu on 2010-10-15
> **Bluebearbevis said:**
> Hello,

I too reached this point.  Then I went to Ubuntu Tweak and enabled x Updates stable.  It gave me 5 nVidiia driver updates which I installed.  Alas, to not avail.  In a related issue, even though additional drivers tells me it is installed and activated, extras won't work in visual effects.  Is this one of those just waits?
Thanks,  Richard

Yes, I also enabled the x-updates source list in Ubuntu Tweak, but it gave me nothing new when I click Sync or Refresh button.

---

### Post by HQiu on 2010-10-19
SOLVED!

Anyone having the problem similar with mine, please refer to the Ubuntu Tweak Bug Reporting: [https://bugs.launchpad.net/ubuntu-tweak/+bug/653933](https://bugs.launchpad.net/ubuntu-tweak/+bug/653933). Please read the #16 reply. It helped me out anyway.

Thank you!

---

### Post by TroyDowling on 2010-12-07
Thank you. I was having the exact same problem. I figured it couldn't be the driver but was stumped to what it was. Here is the comment from above that fixes the issue.

[https://bugs.launchpad.net/ubuntu-tweak/+bug/653933/comments/16](https://bugs.launchpad.net/ubuntu-tweak/+bug/653933/comments/16)

---

### Post by hlnguyen21 on 2011-01-17
The post you refer to says the following:

Please go to "Package Cleaner"->"Purge PPAs", purge the "Compiz PPA", it will fix this problem.

Sorry for this newbish question.. but how do I "go to Package Cleaner" ??

Thanks !

---

### Post by roguebuck on 2011-01-17
I had this exact issue moving from 10.04 to 10.10 when it was released. I had tried purging all nvidia packages and re-installing nvidia-current, but what worked in the end was installing the latest driver off the nvidia site, not nvidia-current.

---

### Post by hlnguyen21 on 2011-01-19
Hey, could you walk me through step-by-step how to do this?

(btw, I'm terrible w/ computers)

Thanks :)

---

### Post by roguebuck on 2011-01-19
no, but this site can:

[http://ubuntuguide.net/install-latest-nvidia-graphics-drivers-in-ubuntu-linux]("http://ubuntuguide.net/install-latest-nvidia-graphics-drivers-in-ubuntu-linux")

---

### Post by stupidCloud on 2011-01-20
> **hlnguyen21 said:**
> The post you refer to says the following:

Please go to "Package Cleaner"->"Purge PPAs", purge the "Compiz PPA", it will fix this problem.

Sorry for this newbish question.. but how do I "go to Package Cleaner" ??

Thanks !

You can use

```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:compiz/ppa

```But this seem not work for me:
```

$ sudo ppa-purge ppa:compiz/ppa
PPA to be removed: compiz ppa
Warning:  Could not find package list for PPA: compiz ppa

```Thanks.

---

### Post by TheCadaver on 2011-04-19
> **stupidCloud said:**
> You can use

```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:compiz/ppa

```But this seem not work for me:
```

$ sudo ppa-purge ppa:compiz/ppa
PPA to be removed: compiz ppa
Warning:  Could not find package list for PPA: compiz ppa

```Thanks.

I can't find the package cleaner, and when i do this, i still don't get my visual effects back. is there anything to do after i do all of this? i don't get any error messages either, in the terminal.

---

### Post by TheCadaver on 2011-04-19
> **TheCadaver said:**
> I can't find the package cleaner, and when i do this, i still don't get my visual effects back. is there anything to do after i do all of this? i don't get any error messages either, in the terminal.

...Nevermind, i found it, in ubuntu tweak, but it didn't do anything. should i reboot?

EDIT: Nope, it did nothing. What happens is, when i click one of the visual effects options, it get a screen saying "searching for drivers...". then, i get the message stating i cannot enable desktop effects... what to do :/

---

### Post by growlf on 2011-04-20
Following the instructions (at [http://ubuntuguide.net/install-latest-nvidia-graphics-drivers-in-ubuntu-linux](http://ubuntuguide.net/install-latest-nvidia-graphics-drivers-in-ubuntu-linux)) as advised above, worked for me on multiple machines.  Two were upgraded from 10.04 and had the issue and one was a fresh install to 10.10.

---

### Post by mickeoliver on 2011-04-23
Thank you so much, this helped me out too! I did have some problems at the command line thing (I'm a noob, I know ;) ) put I figured it out eventually! :p

---

### Post by Parikx on 2011-05-27
> **hlnguyen21 said:**
> The post you refer to says the following:

Please go to "Package Cleaner"->"Purge PPAs", purge the "Compiz PPA", it will fix this problem.

Sorry for this newbish question.. but how do I "go to Package Cleaner" ??

Thanks !

haha...u need to install Ubuntu tweak and then inside it u can see the option Package Cleaner

---

### Post by Dimath on 2011-07-16
> **stupidCloud said:**
> You can use

```

$ sudo ppa-purge ppa:compiz/ppa
PPA to be removed: compiz ppa
Warning:  Could not find package list for PPA: compiz ppa

```Thanks.

I had this error and in my case the PPA was simply switched OFF in the repository list. Switching in ON resolved the problem.

---

### Post by profficv on 2012-12-10
Hello there!
Am super new to Ubuntu but i love write developing and solve things with or without help!

Last Weekend i met the "Desktop Effects could not be activated" then spending some hours fighting and surfing for help i decide start analyze the problem then synaptic show me that an action mine did this:

Commit Log for Fri Dec  7 16:44:30 2012

Removed the following packages:
compiz-dev
libcompizconfig0-dev
libgl1-mesa-dev
libgl1-mesa-glx
libglu1-mesa-dev
libqt3-mt-dev
////////////////////////////////////

I came back today and in synaptic, i just installed again "compiz-dev and  
libcompizconfig0-dev" and the problem was gone, it worked smooth, maybe the other libs involved had cause the problem bcouse u don't need dev stuffs to make things work, i guess i don't know.

and the desktop effects is working perfect!

---

### Post by oldos2er on 2012-12-10
Old thread closed.

---

