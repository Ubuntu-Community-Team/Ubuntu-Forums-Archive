---
title: "Resume after suspend 13.10"
date: 2014-01-01
forum: Desktop Environments
---

### Post by devine.steve on 2014-01-01
Samsung Laptop  When I close the lid it goes to suspend real nice.
When I open the lid it does not resume. It will resume when I push the power button, but I'd really like it to resume when the lid opens. It worked that way with Win 8.1

cat /proc/acpi/wakeup 
Device    S-state      Status   Sysfs node
P0P1      S4    *disabled
USB1      S3    *disabled
USB2      S3    *disabled
USB3      S3    *disabled
USB4      S3    *disabled
USB5      S3    *disabled
USB6      S3    *disabled
USB7      S3    *disabled
RP01      S4    *enabled   pci:0000:00:1c.0
RP04      S4    *enabled   pci:0000:00:1c.3
PEG0      S4    *disabled
PEGP      S4    *disabled
PEG1      S4    *disabled
PEG2      S4    *disabled
PEG3      S4    *disabled
PWRB      S5    *enabled 

I think PWRB is the Power button. I tried this
echo LID0 >/proc/acpi/wakeup

But no joy.
I tried looking for the list of what the variiables stand for but nothing real helpful.

---

### Post by Toz on 2014-01-01
My laptop wakes on lid open and I don't have a lid entry in /proc/acpi/wakeup either. I do have a setting in my bios to resume on lid open and that seems to work. I believe that in my case this is handled by the bios.

Is there a setting in your bios to control LID behaviour?

---

### Post by devine.steve on 2014-01-01
Nope -- nothing specific in the BIOS.

---

### Post by jjmarc on 2014-01-01
Try searching around in your system settings. I believe somewhere there is a submenu where you can select the action that happens when you open/close the lid.

---

### Post by raphael-platte on 2014-01-01
I think it's under "Brightness and Lock"

---

### Post by devine.steve on 2014-01-01
No nothing under Brightness and Lock. I did find some settings under Power that reference what to do when the lid is closed, but not what to do when the lid is opened.

---

### Post by Toz on 2014-01-02
Consider that when your laptop is asleep, userspace is unavailable. Therefore, there is nothing that you can do/configure in userspace to get your system to resume based on an action like lid open because userspace is not "listening". Acpi allows for some triggers/hooks to return your system from suspended states and these are defined in /proc/acpi/wakeup (you can also use rtc to wake up systems, but this is basically via a time-based trigger, not an action-based one like you are looking for). Unfortunately, in your case the LID event is not made available as a action to return your system from suspend. There are a few things you can try:

1. Look to see if there is a setting in the bios that manages lid actions (this you have already checked)
2. Ensure that your lid is being properly recognized. Run this command in a terminal:
```
dmesg | grep -i lid
```
...and see what it says.
3. Look to see if there is a bios update for your system. Maybe this functionality is added later.
4. Create a bug report to see if a developer will add this functionality to acpi for your model of laptop. It will probably involve the creation of some sort of model-specific quirk.

> I tried looking for the list of what the variiables stand for but nothing real helpful. 
The USB devices are usb devices connected to your system - it appears that none currently are. 
The RP0 devices are linked to PCI devices - to find out which ones they are, run "lspci" and match the sysfs node values.
PWRB is your power button, and as you can see, it is enabled.
The PEG devices I believe are related to your video card (not sure).



One other thing that you can try, and I'm not sure of the mileage you'll get out of this, is to try different acpi kernel parameters. In some cases, for some laptops, different sets of acpi tables are loaded when different sets of acpi parameters are specified. What is the model # of your Samsung? You can try:
- acpi_osi=
- acpi_osi=Linux
- acpi_osi=\"!Windows 2012\"
...and after each attempt, check the contents of /proc/acpi/wakeup to see if the LID is recognized. Follow the "Temporarily Add a Kernel Boot Parameter for Testing" instructions from the [Kernel Boot Parameters]("https://wiki.ubuntu.com/Kernel/KernelBootParameters") Wiki to test them.

---

### Post by devine.steve on 2014-01-02
Heres the results of "dmesg | grep -i lid"

[    0.914673] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.914684] ACPI: Lid Switch [LID0]

Am going to try the Kernel parameter switches next

---

### Post by devine.steve on 2014-01-02
No luck with the Kernel switches. Whats odd is that this was working with Windows 8.1

---

### Post by Toz on 2014-01-02
> **devine.steve said:**
> No luck with the Kernel switches. Whats odd is that this was working with Windows 8.1
In that case, can you try **acpi_osi="!Windows 2012"** again. When you boot with it, post back:
```
cat /proc/cmdline
```
...and
```
cat /proc/acpi/wakeup
```

The way you format the "!Windows 2012" string differs based on how you are testing the parameter (temporary vs permanent). Try it temporarily like this:
```
acpi_osi="!Windows 2012"
```

---

### Post by devine.steve on 2014-01-03
cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.11.0-14-generic.efi.signed root=UUID=d296139c-d92a-443e-b565-b0ab89bead68 ro "acpi_osi=!Windows 2012" vt.handoff=7

cat /proc/acpi/wakeup 
Device    S-state      Status   Sysfs node
P0P1      S4    *disabled
USB1      S3    *disabled
USB2      S3    *disabled
USB3      S3    *disabled
USB4      S3    *disabled
USB5      S3    *disabled
USB6      S3    *disabled
USB7      S3    *disabled
RP01      S4    *disabled  pci:0000:00:1c.0
RP04      S4    *disabled  pci:0000:00:1c.3
PEG0      S4    *disabled
PEGP      S4    *disabled
PEG1      S4    *disabled
PEG2      S4    *disabled
PEG3      S4    *disabled
EHC1      S3    *enabled   pci:0000:00:1d.0
EHC2      S3    *enabled   pci:0000:00:1a.0
XHC      S4    *enabled   pci:0000:00:14.0
PWRB      S5    *enabled 

Whats odd (to me) when you look at /proc/cmdline the part with   
"acpi_osi=!Windows 2012"
has the first quote in front of acpi_osi even though I double checked my work and I did it as you suggested.

---

### Post by Toz on 2014-01-03
No, that's correct. I don't know exactly why its parsed like that. However, that didn't change the list of wakeup devices for you. Sorry. It was a long shot.

---

### Post by devine.steve on 2014-01-04
So am to understand that the file /proc/acpi/wakeup is created dynamically by the kernel on bootup? IE - adding the LID or LID0 entry to /proc/acpi/wakeup is not possible. I am going to go into the bios and see if there is an option to set it back to 'default'

---

### Post by devine.steve on 2014-01-04
Found the "return to default' switch in the bios and activated it. No change.

---

