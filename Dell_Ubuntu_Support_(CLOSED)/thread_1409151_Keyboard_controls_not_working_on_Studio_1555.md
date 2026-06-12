---
title: "Keyboard controls not working on Studio 1555"
date: 2010-02-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by MrNatewood on 2010-02-17
I have recently purchased a Dell Studio 1555 and installed Ubuntu Karmic 9.10 64-bit on it.

The multimedia buttons(F7+) work as expected.
But the more important F1-F5 don't work.

That means for instance I can't toggle wireless on/off, which made me restart and boot into windows just to turn on wireless!

Same problem with the brightness controls. They might work at boot but about a minute after using the system they stop working.

Another problem is that the battery status applet does not load if the laptop is booted with AC power connected(even after disconnecting AC it doesn't load, have to reboot without AC connected for it to load)

Also, detection of closed lid doesn't work properly. Screen does not turn off ever. And if it is forced to turn off via command line it turns itself back on within seconds without external input.

Any ideas on how to solve any of these issues?

---

### Post by lz1dsb on 2010-02-18
Interesting. I have absolutely the same setup (hardware and software). So far I've never used the function buttons you mention (as I bought this machine not long ago), but when I read this thread I tried them.. And indeed they don't work! The functional buttons that control the sound work out of the box... So this issue is reproducible... I'm wondering whether there is a support at all for this. 

Regards,
Boyan

---

### Post by anantshri on 2010-02-19
+1 from my side.

also as far as i ca see i keep my brightness at the lowest in my windows session but on my linux session it goes to the max.

and all the key till f5 are indeed not working.

---

### Post by mbickell on 2010-02-20
Same problems here. Got my Dell Studio 1555 about a month ago, its got win7 on, and just trying out ubuntu using wubi before doing a dual-boot. 

One more problem to add to the list above is that the multi-touch on the touchpad doesn't really work, but I have seen forums elsewhere that discuss this issue.

These seem to be a common problems.

---

### Post by garok89 on 2010-02-21
you need to disable apic (yes that is apic, not acpi)in grub
this also fixes the eject button, the backlight 'switch' and the battery not detected issues

```
sudo gedit /etc/default/grub
```
then edit this line
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to this
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic"
```
then update grub (i dont know if you need to use update-grub2 or update-grub so do both)
```
sudo update-grub && sudo update-grub2
```
reboot and all shall be good

---

### Post by lz1dsb on 2010-02-21
Wow, that's amazing. I just tried it, and it works as you have written! Thank you! You rock mate. Where did you get this info from? And what is apic anyway? I'm just curious...

Cheers,
Boyan

---

### Post by garok89 on 2010-02-21
hours of trawling the forums for a cure to my backlight blues and my battery woes....and my eject button (cant think of anything to put after that)
it solves lots of issues with laptops such as unplugging freezing the laptop or triggering a suspend
may come in handy for any future laptops you might have ;)

---

### Post by garok89 on 2010-02-21
as far as i am aware apic is pretty much like acpi...i read about it months ago but cant remember it exactly

---

### Post by lz1dsb on 2010-02-22
Because you mentioned battery... Did you have an issue with the battery indicator after Suspend or Hibernate? On my laptop it works fine before I suspend or hibernate it. After that it doesn't detect when the power jack is no longer connected. So it always shows an indicator showing a connected power jack and it acts as if the power jack is still connected. I haven't had the time yet to test it yet in more detail. So this is just a though, it would be great if this incredible config change also solves this ;) 

Cheers,
Boyan

---

### Post by MrNatewood on 2010-02-22
> **garok89 said:**
> you need to disable apic (yes that is apic, not acpi)in grub
this also fixes the eject button, the backlight 'switch' and the battery not detected issues

```
sudo gedit /etc/default/grub
```
then edit this line
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to this
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic"
```
then update grub (i dont know if you need to use update-grub2 or update-grub so do both)
```
sudo update-grub && sudo update-grub2
```
reboot and all shall be good

Thanks, that does fix the keyboard controls, but is causes another bug:
[http://ubuntuforums.org/showthread.php?t=1407860](http://ubuntuforums.org/showthread.php?t=1407860)

---

### Post by garok89 on 2010-02-22
strange...this rarely happens to mine....about 1 in 20 boot-ups i have that issue, but thats about it.
personally i dont find that is a major issue as i am rarely away from a charger
i suppose it is a compromise

---

### Post by lz1dsb on 2010-02-24
Did anybody of you guys noticed that the function keys F1 through F5 stop working after a Hybernate, Suspent or after taking of and on the power plug? F2 (battery state) and F6 (keyboard lighting) seem not to be affected, they always work. Strange. I just noticed it, but I need to study this behavior in more detail...

Regards,
Boyan

---

### Post by garok89 on 2010-02-24
nope, i dont use standby or hibernate...and it doesnt happen after unplugging and replugging....
also...keyboard light? now im jealous...lol

---

### Post by lz1dsb on 2010-02-28
Well the keyboard light isn't something special though (it was interesting for me that it was working from the first time I installed Ubuntu on the laptop, without the need for additional configuration change what so ever). I guess it's something pretty standard though. But its strange that this only happened once. I just tried to specifically reproduce it (suspending the laptop and than starting it again), but wasn't able to. The special keys are working. Anyway. It could have been something intermittent. 
I was just wondering something else. Do you have problems accessing the VTY lines? I see in the processes that I have them running, but I can't access them! The key combination Ctrl+Alt+F1 for example isn't working. So I guess it's something to do with the additional functions assigned to the functional keys.

Cheers,
Boyan

---

