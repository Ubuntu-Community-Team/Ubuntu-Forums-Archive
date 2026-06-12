---
title: "Vmware Install"
date: 2005-10-27
forum: Desktop Environments
---

### Post by rj686 on 2005-10-27
I downloaded the trial version of vmware, but i cant figure out how to to install it. I keep getting access error when i get to the config section of the install. Could someone help me?

---

### Post by mrtrick on 2005-10-27
What is the exact error that you are getting? What version of vmware are you trying to install? I have successfully installed vmware on my workstation and it appears to be working great. I'd be glad to help if you can provide more info.

---

### Post by rj686 on 2005-10-27
I am trying to installl v. 4.5.2

 "/usr/bin/vmware-config.pl". Do you want thisprogram to invoke the command for you now? [yes] yes


sh: /usr/bin/vmware-config.pl: Permission denied
rj@LOFTNESS:/VMware-workstation-4.5.2-8848/vmware-distrib$ sudo perl /usr/bin/vmware-config.pl
Making sure services for VMware Workstation are stopped.

sh: /etc/init.d/vmware: Permission denied
Unable to stop services for VMware Workstation

Execution aborted.

thats the error i get every time and i cant get past it

---

### Post by mrtrick on 2005-10-27
You did the install sudo'd right?

---

### Post by rj686 on 2005-10-27
yes from the beginning i did but for somereason when i get to the config part it says permission denied?

---

### Post by rj686 on 2005-10-27
ok heres where im at

rj@LOFTNESS:~/VMware-Workstation/VMware-workstation-4.5.2-8848/vmware-distrib$ sh /etc/init.d/vmware start
VMware Workstation is installed, but it has not been (correctly) configured
for the running kernel. To (re-)configure it, invoke the
following command: /usr/bin/vmware-config.pl.

rj@LOFTNESS:~/VMware-Workstation/VMware-workstation-4.5.2-8848/vmware-distrib$ sudo perl /usr/bin/vmware-config.pl
Making sure services for VMware Workstation are stopped.

sh: /etc/init.d/vmware: Permission denied
Unable to stop services for VMware Workstation

---

### Post by rj686 on 2005-10-27
bump

---

### Post by mlomker on 2005-10-27
I doubt that 4.5.2 even supports the 2.6.12 kernel.  Why don't you download a demo of 5.5 Workstation?  It works well.

---

### Post by rj686 on 2005-10-27
thx ill try that

---

### Post by rj686 on 2005-10-27
how do u remove directories? I only know how to remove files.

---

### Post by mlomker on 2005-10-27
[QUOTE=rj686]how do u remove directories? I only know how to remove files.[/QUOTE]

Be careful with this command...linux doesn't have a recycle bin.  ;)

```

sudo rm -fr directory

```

---

### Post by rj686 on 2005-10-27
one more qustion sorry to keep bugging you. I cant find an eval version of 5.5. IS that what yoru running or do u own the program?

Did u get a deb file? I just found source and rpm....

---

### Post by mlomker on 2005-10-27
You have to install it from source.  Grab these:

```

sudo apt-get install linux-headers-$(uname -r)
sudo apt-get install build-essential gcc-3.4

```

Before running the installer do this:

```

export CC=/usr/bin/gcc-3.4

```

[The download page is here.]("http://www.vmware.com/programs/1/wkst5beta.do")

---

### Post by rj686 on 2005-10-27
thx for the help :p :smile:

---

### Post by rj686 on 2005-10-27
anyone know of a tutorial on how to get this running on UBUNTU?

---

### Post by mlomker on 2005-10-27
[QUOTE=rj686]anyone know of a tutorial on how to get this running on UBUNTU?[/QUOTE]

No, because most of the people that install VMWare probably don't need instructions...tends to be the linux power-user types.  What's the problem?

---

### Post by rj686 on 2005-10-27
no problem i got it installed just fine now.......i was just curious if there was an isntall guide lol.....thx for your help though :)......didnt you say something about a 1 year eval?

its amazing how once i use a NEW version the install goes flawlessly....again thx for the help

---

### Post by mlomker on 2005-10-27
>  about a 1 year eval?


No, they aren't insane...they have kids to feed and all that.  ;)

---

