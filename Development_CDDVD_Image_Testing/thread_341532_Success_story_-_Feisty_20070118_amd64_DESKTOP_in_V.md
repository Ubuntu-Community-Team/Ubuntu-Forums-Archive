---
title: "Success story - Feisty 20070118 amd64 DESKTOP in VMware"
date: 2007-01-18
forum: Development CD/DVD Image Testing
---

### Post by UBfusion on 2007-01-18
Bare with me, I just want to express how satisfying is to manage installing Feisty Desktop (alternate installs ok) **for the first time ever** from an iso!

I can proudly report that at least in VMware the python script bugs that I and several  testers were experiencing in Herd2 and later builds gone in build 20071118. However  there's a small formatting error that needs to be addressed. Instructions follow:

1. Create a new VM guest with the usual settings. Set the iso as boot CD.

2. When feisty boots, the installer will pass all the screens and ask to partition the disk.

3. Choose to partition the whole disk and proceed. The process will hang at 15% and the the VM will freeze totally. Shutdown the VM.

4. Reboot the VM and in Bios setup choose to boot first from the CD (i.e. the iso). Save settings and reboot.

5. Feisty live will start again. If at this point you try to reinstall, try the manual partitioning. You will see that the correct partitions were created indeed but they were not formatted properly. This is why the installation hangs. (I have seen many similar bugs in launchpad)

6. Now open a terminal and format the partitions manually using *sudo mkfs.ext3 /dev/sda1* and  *sudo mkswap /dev/sda5*

7. Go to the installer screen and press "back" to restart the partitioning process and choose manual partitioning. You will then see that the installer correctly identifies the mount points.

8. Proceed with the installation, installation will successfully complete!!!

9. Press "Restart now". (In case Feisty has frozen, just power down the VM). When the Bios screen appears, power the VM down and in the VM menu change the settings to replace the feisty iso with a normal cd drive (so that the VM won't boot from the CD again). 

10. Feisty will boot gloriously with "crash report" and "available updates" notifications.

FEISTY IS UP and running :D 

Clicking the crash report notification icon will lead to the reporter's crashing. My feeling is that this does not need a bug report (see below).

There will be ~18 updates available. Install them and restart feisty. No more crash report icon! Apparently the gtk libs included in the updates did their magic.

Conclusion: In previous builds I had tried manual formatting but it didn't work. In my opinion 20070118 is a major step forward in the development of feisty daily builds. When the partitioning process is fully debugged my feeling is that the desktop x64 will be ready for thorough testing, possibly leading to Herd3.

Well done development team! Tomorrow I'll install on a real new HDD.

---

### Post by pochu on 2007-01-19
Hi UBfusion.

If after update the system it won't open the bug report anymore, installing with a newer image shouldn't give you those problems.

So please try with the 20070119 image (or newer).

Regards
Pochu

---

### Post by Henrik on 2007-01-19
The python transition (2.4 to 2.5) probably caused a lot of breakage. We can still expect some breakage in Feisty as we continue to upload new versions of Gnome, Firefox, etc. 

But we'll get there :) Thanks for testing!

---

### Post by domcio on 2007-01-19
> **pochu said:**
> Hi UBfusion.

If after update the system it won't open the bug report anymore, installing with a newer image shouldn't give you those problems.

So please try with the 20070119 image (or newer).

Regards
Pochu

I've tried alternate iso 20070119 i386, unfortunately it doesn't even boot :(

---

### Post by pochu on 2007-01-19
> **domcio said:**
> I've tried alternate iso 20070119 i386, unfortunately it doesn't even boot :(
But that doesn't mean it won't boot to everybody. It depends on your hardware, for example.

---

### Post by domcio on 2007-01-19
Well it's not that bad - it boots on my second machine, so maybe DVD drive in my laptop is just too demanding or CD-RW I've used is too cracked. I'll try to record it on new one and report how it works.

---

### Post by UBfusion on 2007-01-20
I am happy to report that Feisty 20070120 amd64 desktop

- has fixed all partitioning and formatting problems (on blank VM disk that is)

- still has a crash report on first boot

- after installing the available updates, on second reboot there is one crash report regarding "the program **evolution-alarm-notify** closed unexpectedly"

I opted to submit a bug and the process collected data successfully. I did not submit it because it's a well-known one (#66860) and currently being fixed.

---

### Post by pochu on 2007-01-20
Hi UBfusion
Nice to hear that!

And now, let's keep our work.

Regards
Pochu

---

### Post by pochu on 2007-01-20
UBfusion: Can you confirm the bug report? [#80589]("https://launchpad.net/ubuntu/+bug/80589")

Regards
Pochu

---

### Post by UBfusion on 2007-01-20
pochu: Yes I did. The new gnome-app-install 0.3.6 should fix it.

---

