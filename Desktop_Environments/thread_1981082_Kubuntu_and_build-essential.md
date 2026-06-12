---
title: "Kubuntu and build-essential"
date: 2012-05-16
forum: Desktop Environments
---

### Post by MrBean355 on 2012-05-16
Hi guys,

I am trying to install *build-essential* on my computer (dual-boot with Windows 7 and Kubuntu) _**from the DVD ISO**_ (I don't have an internet connection) so I can use the G++ compiler. However, it doesn't work. It says "[COLOR=Red]Unable to satisfy dependencies[/COLOR]".

The strange thing is that when I "Try Kubuntu" (running the Live version from USB), it [COLOR=Lime]**can and does**[/COLOR] install *build-essential* and then the G++ compiler works fine!

What is going on here?! :???:

Thanks for any help.

***Mr_Bean***

---

### Post by SeijiSensei on 2012-05-16
Have you ever installed anything on this computer over the Internet, in particular more recent kernels?  It's possible that the installation on your hard drive has more recent versions of some libraries than the DVD, so the installer cannot find the compatible versions it expects on the hard drive.

If you run "sudo apt-get install build-essential" from the command line, you should see the dependencies that it is complaining about.

---

### Post by MrBean355 on 2012-05-16
I downloaded the Kubuntu 12-04 64bit DVD ISO. I haven't installed anything from the internet because I can't connect to the internet.

How can I fix the kernel thing?

---

### Post by SeijiSensei on 2012-05-16
> **MrBean355 said:**
> I downloaded the Kubuntu 12-04 64bit DVD ISO. I haven't installed anything from the internet because I can't connect to the internet.

How can I fix the kernel thing?

If all you have is the DVD software and nothing else, then it's not a "kernel thing."  What happens when you do this?

> If you run "sudo apt-get install build-essential" from the command line, you should see the dependencies that it is complaining about.

What are they?

---

### Post by MrBean355 on 2012-05-17
> **SeijiSensei said:**
> If all you have is the DVD software and nothing else, then it's not a "kernel thing."  What happens when you do this?

You mean I must type "sudo apt-get install build-essential"? If I remember correctly, it says something like unable to find package build-essential, but I will try again when I get the chance.

---

### Post by Erik1984 on 2012-05-17
So if I understand correctly: You can install a certain package from a Live session w/o internet but not from your installed Kubuntu?

Maybe the live session has the DVD itself listed as a package source and the installed Kubuntu hasn't. You could try to add the DVD to the sources in Muon Package Manager. See settings > configure software sources and then the tab "Other Software". For me the CD (I installed from CD) is *un*checked there by default.

---

### Post by MrBean355 on 2012-05-17
Yes, when I run a live session, I can simply install build-essential without having an issues or having to install other packages.

Thanks for the suggestion, I will try it out and let you know!

---

### Post by sabersong on 2012-06-23
This is a mistake I've made in the past. Make sure you've updated the reposiotories before trying to install build-essential. At the command line, type:

```
sudo apt-get update
```

---

