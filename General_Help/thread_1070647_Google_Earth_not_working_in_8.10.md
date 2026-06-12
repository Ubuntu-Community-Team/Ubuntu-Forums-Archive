---
title: "Google Earth not working in 8.10"
date: 2009-02-15
forum: General Help
---

### Post by woknam66 on 2009-02-15
I have Ubuntu 8.10, and I can't get Google Earth to work. I have tried doing [this]("http://n01getsout.com/blog/2006/11/26/google-earth-for-linux-freezing-with-ati/"), and I think I have an ATI graphics card, but I just can't get it to work.

P.S. I have a Dell Inspiron 6000.

---

### Post by mikewhatever on 2009-02-15
The fix you tried is quite old, 11/2006, and I am not sure it's still relevant, since both GE and Ubuntu have evolved. What exactly is the problem in your case? Try typing **googleearth** in Terminal and post the output here.

---

### Post by woknam66 on 2009-02-15
Google Earth starts and then crashes immediately, and terminal gives me this:```
Warning: Unable to create prefs directory '/home/woknam66/.googleearth'. File exists.
./googleearth-bin: relocation error: /usr/lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference

```

---

### Post by M!SF!TS on 2009-02-15
okay, i dont know if this will help but you can try it...
it worked for me... flawless maybe you to ?


for google earth 5.0 (the new one)

go here [http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

it will be saved as a .bin file


okay next... do this
look where you saved GoogleEarthLinux.bin

goto terminal and type this

$ chmod +x /home/user/Downloads/GoogleEarthLinux.bin
(obviously you dont have   /home/user/Downloads   so type where YOU saved it  i.e.  /home/you/Downloads/GoogleEarthLinux.bin )

then type this in terminal

./GoogleEarthLinux.bin

now you should have had a window pop up and you installed it

and it tried to run but failed... THATS OKAY!!! it failed !!! hey its linux... everything take a little more work!!!


okay now go here

Places>Home Folder>google-earth>

and look for this file ...    "libcrypto.so.0.9.8"

once you find this file ...   "libcrypto.so.0.9.8"

change the name to this ...   "libcrypto.so.0.9.8.bak"

and NOW try to run it... 

it will work...
(hopefully)

---

### Post by M!SF!TS on 2009-02-15
the beggining of my last post said something like...


i dont know if this will work... or something

FORGET IT

with your issue ... woknam66

IT WILL WORK!!!

i read your terminal output and yes... same issue i had...



just goto    Places>Home Folder>google-earth


and rename this file .... "libcrypto.so.0.9.8"
to this              .... "libcrypto.so.0.9.8.bak"


and it will work

---

### Post by M!SF!TS on 2009-02-15
(providing its the new google earth 5.0)

...it has a flight simulator you know ...

---

### Post by woknam66 on 2009-02-15
I tried renaming "libcrypto.so.0.9.8" to "libcrypto.so.0.9.8.bak", but it still doesn't work....

---

### Post by M!SF!TS on 2009-02-15
hmm... i see

well man, i know of a solution, it works like 98.9987654321% of the time
[http://www.google.com](http://www.google.com)

---

### Post by woknam66 on 2009-02-15
I've tried that already....

---

### Post by Mario5000 on 2009-02-15
I have the same problem.  But cant rename libcrypto file because I don't know how to find the googleearth directory.  I know this is trivial, but ...

Mario

---

### Post by cl333r on 2009-02-15
The google earth directory is actually ".googleearth" (starts with a dot) so it's hidden, to display hidden folders press Ctrl+H in your (Nautilus) file manager.

Perhaps a bit offtopic, can anyone comment on why the Linux version doesn't (seem to) support the under the sea feature??

---

### Post by mikewhatever on 2009-02-16
> **Mario5000 said:**
> I have the same problem.  But cant rename libcrypto file because I don't know how to find the googleearth directory.  I know this is trivial, but ...

Mario

It's the directory you installed it to. Unless the installer's default was changed, it's /opt/google-earth.


> **cl333r said:**
> The google earth directory is actually ".googleearth" (starts with a dot) so it's hidden, to display hidden folders press Ctrl+H in your (Nautilus) file manager.


That's the settings directory, and there is no libcrypto file there.

---

### Post by sondosia on 2009-02-16
I've managed to get Google Earth to stop crashing on startup, but I'm having a problem that might be graphics card-related...[Here's a screenshot]("http://img87.imageshack.us/img87/1483/screenshotgoogleearthri0.png")

Basically, the main window doesn't actually show anything...any ideas?

---

### Post by mikewhatever on 2009-02-16
Post some info on your graphics card. If not sure, just post the output of the following:
sudo lshw -C display

It might also provide some insights if you start the program from Terminal by typing <googleearth> and then posting the output.

---

### Post by sondosia on 2009-02-16
Here's the output:

  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

---

### Post by woknam66 on 2009-02-17
Is there any way to install Google Earth via the synaptic package manager?

---

### Post by oldos2er on 2009-02-17
> **woknam66 said:**
> Is there any way to install Google Earth via the synaptic package manager?

 Enable the Medibuntu repository: [http://medibuntu.org/](http://medibuntu.org/)

---

### Post by Slim Odds on 2009-02-17
We need a "Google Earth 5.0" sticky!!!!

---

### Post by woknam66 on 2009-02-17
I've tried to find how to add repositories online, but there doesn't seem to be any simple solutions, how do I add the Medibuntu repository?

---

### Post by mikewhatever on 2009-02-17
> **woknam66 said:**
> I've tried to find how to add repositories online, but there doesn't seem to be any simple solutions, how do I add the Medibuntu repository?

Actually, there is.
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)

---

### Post by woknam66 on 2009-02-18
Wait, is what you type into terminal all one command

---

### Post by fluizp on 2009-02-18
I am having the same problem, but I don`t think it is a graphic card problem or driver. When I start Google Earth appears two windows that says (free translation since the windows pop-up in my native language that is portuguese):

First says:
Was not possible make the folder: /root/.googleearth/Cache

I click OK and then appears the second window that says:
Google Earth could not write in the current cache nor in the local file myplaces. Values will be defined as follows:
My places path: "/home/fluizp/.googleearth"
Cache path: "/home/fluizp/.googleearth/Cache"

Then Google Earth starts loading and when it finally opens, it instantly closes.

One guy told me that this happens because the program doesn`t achieve to create the cache, and this because the user doesn`t have writting and reading permission in /root. He told me to run the program as root in the first time (sudo googleearth), but the problem persists.

---

### Post by woknam66 on 2009-02-18
After typing that stuff into terminal, when Synaptic tried to update the repositories, it gave me this error:
```
GPG error: http://packages.medibuntu.org intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by oldos2er on 2009-02-18
> **woknam66 said:**
> After typing that stuff into terminal, when Synaptic tried to update the repositories, it gave me this error:
```
GPG error: http://packages.medibuntu.org intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.
```

 You can ignore the public key warning. Disable the CD-ROM via menus System, Administration, Software Sources, and make sure the box under 'Installable from CD-ROM/ DVD' is not checked.

---

### Post by woknam66 on 2009-02-18
Never mind, I just restarted the computer, followed a guide on how to do it from the command line, and it worked. I haven't tried it yet, but I will soon.

---

### Post by woknam66 on 2009-02-18
Ok, now I've tried actually using Google Earth (which I installed from the medibuntu repository), but I'm having the same problem that sondosia is having. Here's what I get when I type "sudo lshw -C display" into terminal:```
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

```

And when I type "googleearth" into terminal, it opens up Google Earth with the same problems, but I get no info from the Terminal.

---

### Post by mikewhatever on 2009-02-19
I think you should try booting the recovery mode and choosing the fix X option. The UNCLAIMED status shown in the above output is not a good sign.

---

### Post by woknam66 on 2009-02-19
Actually, the main reason that I switched from Windows to Linux was because Windows was too slow. But can I run the Windows version of Google Earth with Wine alright? And if so, will it slow down my computer a lot?

---

### Post by woknam66 on 2009-02-22
Hello? Anyone?

---

### Post by mmace1 on 2009-03-05
Just want to say - I had three different model laptops with this problem - and all 3 were solved by following M!SF!ITS directions...once I figured out how to actually follow them (I know nothing about terminal, or, anything in Ubuntu really).  

The only other problem, was that 2 of the laptops also experienced screen flicker (though no longer crashed) - to fix the screen flickr, I just downloaed Compiz Fusion Icon' - and turn off Compiz Fusion before running Google Earth, then turn it back on when finished.  Quite a pain, but at least it works.

---

### Post by mmace1 on 2009-03-05
> **woknam66 said:**
> Hello? Anyone?

I tried WINE (before the solution in this thread worked for *my* computers),  but it wouldn't even run.  No harm in you trying as well though I suppose.

---

