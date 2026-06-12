---
title: "Samsung NP300V5A-S0CIN brightness issue."
date: 2013-06-20
forum: Desktop Environments
---

### Post by ttsdinesh on 2013-06-20
Hi All,

I am using Samsung NP300V5A-S0CIN laptop and Ubuntu 13.04. But when ever I boot my laptop the brightness is set full and it causes severe eye pain. I have to manually set to 30-40%. But after sometime the brightness again goes full by itself. Is there any solution for this?

Thanks in advance.

---

### Post by Toz on 2013-06-20
Can you give the following kernel parameters a try:

**acpi_osi=Linux acpi_backlight=vendor**

Have a look at the "Kernel Boot Parameters" link in my signature for information on how to do this.

---

### Post by ttsdinesh on 2013-06-20
Damn, it works !! Thank you Toz :)

---

### Post by oldfred on 2013-06-21
Let us know what works and to mark your thread as [SOLVED] for new forum vb4:
Temp workaround for [SOLVED]- [http://ubuntuforums.org/showthread.php?t=2121377](http://ubuntuforums.org/showthread.php?t=2121377)
Issues of new plugin:
[http://ubuntuforums.org/showthread.php?t=2151638](http://ubuntuforums.org/showthread.php?t=2151638)

   Screen shots of Solved
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by ttsdinesh on 2013-06-21
Sorry to open this again. When I open the laptop after suspending the brightness again goes full :( Any help?

---

### Post by Toz on 2013-06-21
Do they Fn keys still work after resume, or have they stopped as well?

---

### Post by ttsdinesh on 2013-06-22
Function key to adjust brightness never worked in my laptop. After adding **a****cpi_osi=Linux acpi_backlight=vendor **in grub also function keys are not working. But function keys to adjust volume works as always.

---

### Post by Toz on 2013-06-22
> **ttsdinesh said:**
> Function key to adjust brightness never worked in my laptop. After adding **a****cpi_osi=Linux acpi_backlight=vendor **in grub also function keys are not working. But function keys to adjust volume works as always.

I'm sorry, but I'm confused. In post #3 you stated that adding those kernel parameters fixed the brightness keys and allowed you to change brightness. Then on post #5, you stated that brightness went automatically to full on resume from suspend.

After resume from suspend, when the brightness goes to full, can you still use the function keys to lower brightness?

---

### Post by ttsdinesh on 2013-06-22
Sorry Toz, for confusing :( 

I'll summarize what has happened.

After adding the parameters to kernel, fn keys didn't work (even before adding the parameters the fn keys didn't work). But before adding the parameters the brightness changes automatically. For instance, I use 'Brightness control' in settings to reduce brightness. After sometime the brightness goes to full automatically. But after adding the kernel parameters this behavior got fixed. I mean, the random brightness increase got fixed. But still whenever I resume after suspending or reboot the brightness goes full.

---

### Post by Toz on 2013-06-22
Run the following command:
```
grep . /sys/class/backlight/*/*
```
...and post back the results.

---

### Post by ttsdinesh on 2013-06-22
This is the o/p

```
dinesh@dinesh-lt:~$ grep . /sys/class/backlight/*/*
/sys/class/backlight/acpi_video0/actual_brightness:7
/sys/class/backlight/acpi_video0/bl_power:0
/sys/class/backlight/acpi_video0/brightness:7
grep: /sys/class/backlight/acpi_video0/device: Is a directory
/sys/class/backlight/acpi_video0/max_brightness:7
grep: /sys/class/backlight/acpi_video0/power: Is a directory
grep: /sys/class/backlight/acpi_video0/subsystem: Is a directory
/sys/class/backlight/acpi_video0/type:firmware
/sys/class/backlight/acpi_video1/actual_brightness:7
/sys/class/backlight/acpi_video1/bl_power:0
/sys/class/backlight/acpi_video1/brightness:0
grep: /sys/class/backlight/acpi_video1/device: Is a directory
/sys/class/backlight/acpi_video1/max_brightness:7
grep: /sys/class/backlight/acpi_video1/power: Is a directory
grep: /sys/class/backlight/acpi_video1/subsystem: Is a directory
/sys/class/backlight/acpi_video1/type:firmware
/sys/class/backlight/intel_backlight/actual_brightness:309
/sys/class/backlight/intel_backlight/bl_power:0
/sys/class/backlight/intel_backlight/brightness:4648
grep: /sys/class/backlight/intel_backlight/device: Is a directory
/sys/class/backlight/intel_backlight/max_brightness:4648
grep: /sys/class/backlight/intel_backlight/power: Is a directory
grep: /sys/class/backlight/intel_backlight/subsystem: Is a directory
/sys/class/backlight/intel_backlight/type:raw

```

---

### Post by Toz on 2013-06-22
Can you post back:
```
cat /proc/cmdline
```

Which of the following sets of commands actually change the brightness:
```
echo 3 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 7 | sudo tee /sys/class/backlight/acpi_video0/brightness
```

```
echo 5 | sudo tee /sys/class/backlight/acpi_video1/brightness
echo 0 | sudo tee /sys/class/backlight/acpi_video1/brightness
```

```
echo 2324 | sudo tee /sys/class/backlight/intel_backlight/brightness
echo 4648 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

---

### Post by ttsdinesh on 2013-06-23
O/p for  [COLOR=#000000][FONT=Ubuntu Mono]cat /proc/cmdline is
[/FONT][/COLOR]
```
BOOT_IMAGE=/boot/vmlinuz-3.9.0-030900-generic root=UUID=a526fb85-2653-479a-8aa5-035a2281db46 ro quiet splash
```

Following lines change the brightness.


echo 2324 | sudo tee /sys/class/backlight/intel_backlight/brightnessecho 4648 | sudo tee /sys/class/backlight/intel_backlight/brightness

echo 3 | sudo tee /sys/class/backlight/acpi_video0/brightnessecho 7 | sudo tee /sys/class/backlight/acpi_video0/brightness

---

### Post by Toz on 2013-06-23
> **ttsdinesh said:**
> O/p for  [COLOR=#000000][FONT=Ubuntu Mono]cat /proc/cmdline is
[/FONT][/COLOR]
```
BOOT_IMAGE=/boot/vmlinuz-3.9.0-030900-generic root=UUID=a526fb85-2653-479a-8aa5-035a2281db46 ro quiet splash
```
You are missing the **acpi_iso=Linux acpi_backlight=vendor** kernel parameters from post #2. Can you re-add them, this time follow the "Permanently Add a Kernel Boot Parameter" instructions in the "Kernel Boot Parameters" link in my signature. After you have rebooted, check that the parameters are in effect (should be displayed in the results of "cat /proc/cmdline").

Then, check the brightness again, especially after a resume. If the problem persists, reply back with:
```
cat /proc/cmdline
```
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```
...and try once again to see which of the interfaces allow for brightness adjustements based on my previous post.

---

### Post by ttsdinesh on 2013-06-24
This is the line in my /etc/default/grub

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" acpi_osi=Linux acpi_backlight=vendor

```

Is this correct or should it be 

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"

```


I'm confused in adding the parameter inside the double quote. Please provide me an example.

---

### Post by Toz on 2013-06-24
> **ttsdinesh said:**
> 
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"

```
^^^^^This option is correct. Save the file then run:
```
sudo update-grub
```
...then reboot.

---

### Post by ttsdinesh on 2013-06-25
Now when I reboot the brightness is not set to 100% but around 80%. But it is ok for me. When I suspend and open again the brightness is preserved. 

Thank you Toz !!

---

### Post by ikt on 2013-06-25
Closed at OP request.

---

