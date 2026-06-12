---
title: "Crazy AMD Issue"
date: 2006-02-19
forum: Desktop Environments
---

### Post by somuchfortheafter on 2006-02-19
Well I have been putting off asking this question because I had planned to install XP Professional back onto my main desktop  workstation but now that I have office 2003 working I guess I shall keep Ubuntu on it. The problem is after I boot the system the clock is set perfectly as it syncs to ntp.ubuntulinux.org at startup. As the day progresses the clocks time seems to go faster and faster until the desktop clock can be as much as 3 hours off. How can I fix this. I am using and amd athalon 2800+ and some asus motherboard.

---

### Post by Ramses de Norre on 2006-02-19
I'm having the same problem, my clock is just running twice as fast as it should..
A while ago I thought I found the solution by adding "acpi=noirq noapic no_timer_check=0" as boot parameters but it made my X crash a lot.. I have tried only adding the "no_timer_check=0" but that didn't do anything, I haven't tried any other combinations yet but I'm going to when I've got enough time.
You could try to play a bit with these options (let me know if you found something! I've been searching a lot for this issue but didn't find any solution yet..). It's a known bug in the 2.6 kernels combined with amd64 processors.

---

### Post by Mustard on 2006-02-19
This problem has been covered pretty well, by this thread...

[http://www.ubuntuforums.org/showthread.php?t=75281&highlight=clock+fast](http://www.ubuntuforums.org/showthread.php?t=75281&highlight=clock+fast)

---

### Post by Ramses de Norre on 2006-02-19
I'm not having really the same problem he's discribing, I haven't got the high cpu rates nor the fast mp3 playing. Just the clock going too fast.. 
But I will try those boot options when I've got a day off.

---

### Post by somuchfortheafter on 2006-02-19
and that approach only works for the 64bit platform which i dont run. on a side note the first time i saw that thread a while back i thought that it would help me.

---

### Post by v79 on 2006-02-20
[QUOTE=somuchfortheafter]Well I have been putting off asking this question because I had planned to install XP Professional back onto my main desktop  workstation but now that I have office 2003 working I guess I shall keep Ubuntu on it. The problem is after I boot the system the clock is set perfectly as it syncs to ntp.ubuntulinux.org at startup. As the day progresses the clocks time seems to go faster and faster until the desktop clock can be as much as 3 hours off. How can I fix this. I am using and amd athalon 2800+ and some asus motherboard.[/QUOTE]

I've been having a similar problem, except that is most notable in Windows. Linux seems to be behaving itself...

---

### Post by Ramses de Norre on 2006-02-20
I haven't checked it in windows yet. And there is a 32bit version also I saw.

But I have a problem: I wanted to try the boot options this afternoon and I started with the first, noapic nolapic. I booted but he freezed at 'setting drive parameters' and I had to reboot.. 
After the reboot the bios took pretty long to check the smart and dma status of my hard drives and dvd drive and after he managed to do that nothing happened nomore.. just a little cursor in the upper left hand corner. Normally he says something about realtek.. never really looked at it.

However I started troubleshooting and I found out it was my dvd burner who blocked everything, I've got a grub 12 error message and after another reboot everything works fine now. But I haven't turned the dvd back on.. 
I will check whether he's also working again tomorow (don't want to reboot now).

Is this all normal? I'm a bit afraid to try the other options now.. this was the first and so I hoped the less dangerous, most probably to work option but instead it seems like it did something pretty wrong.
I wouldn't think they'd affect my bios loading the mbr.. because I think that's what the realtek thing should do..

Should I try the other options? I think I wont but maybe if you've got a neat reason why the others might be a little nicer I will.

---

### Post by wargames on 2006-02-20
[QUOTE=somuchfortheafter]Well I have been putting off asking this question because I had planned to install XP Professional back onto my main desktop  workstation but now that I have office 2003 working I guess I shall keep Ubuntu on it. The problem is after I boot the system the clock is set perfectly as it syncs to ntp.ubuntulinux.org at startup. As the day progresses the clocks time seems to go faster and faster until the desktop clock can be as much as 3 hours off. How can I fix this. I am using and amd athalon 2800+ and some asus motherboard.[/QUOTE]

I had this same problem with my AMD system with the clock running out of control but I fixed it by putting just "noapic" into the kernel options in the menu.lst grub file. So gedit menu.lst, insert "noapic", then reboot system, set the clock and it should work.

Here is what my line looks like from menu.lst:
## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro noapic quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

Hope this helps.

---

### Post by Swiss on 2006-02-20
I have a AMD Athlon 2400+ and have no problems

---

### Post by Ramses de Norre on 2006-02-20
Guess your one lucky guy;)

---

### Post by tseliot on 2006-02-20
[QUOTE=Ramses de Norre]Is this all normal? I'm a bit afraid to try the other options now.. this was the first and so I hoped the less dangerous, most probably to work option but instead it seems like it did something pretty wrong.
I wouldn't think they'd affect my bios loading the mbr.. because I think that's what the realtek thing should do..

Should I try the other options? I think I wont but maybe if you've got a neat reason why the others might be a little nicer I will.[/QUOTE]
The problem you had is not normal. Nontheless that boot option doesn't work for everybody. The boot options suggested in my guide don't damage your hardware.

You can try the other options then if one of them works you can set it permanently (it's all written in my guide)

---

### Post by tseliot on 2006-02-20
[QUOTE=somuchfortheafter]and that approach only works for the 64bit platform which i dont run. on a side note the first time i saw that thread a while back i thought that it would help me.[/QUOTE]
You might try the boot options in the 32bit section of my guide

---

### Post by Ramses de Norre on 2006-02-20
I'll try them when I've got time, but this boot problem really scared me a bit. I've still got to test it with the dvd burner plugged in..

---

