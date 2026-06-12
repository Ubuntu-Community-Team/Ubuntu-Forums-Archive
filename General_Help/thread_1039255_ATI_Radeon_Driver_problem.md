---
title: "ATI Radeon Driver problem"
date: 2009-01-14
forum: General Help
---

### Post by cartesian on 2009-01-14
I have installed the ATI Proprietary Linux x86 Display Driver after I researched the forums because I couldn't get any of the desktop effects on my laptop even though I have ATI Mobility 24000 installed.

After installing the driver when I restarted the laptop, ubuntu won't boot up. It just hangs at an Asus laptops 'splash' screen.

I need some help to get my destop back!!

Thanks.

---

### Post by Titan8990 on 2009-01-14
If it is hanging on the Asus laptop splash screen (and not the Ubuntu splash screen), then that typically means that there is a hardware issue with your BIOS (because those never drivers, and the entire OS have not even began to load).

---

### Post by cartesian on 2009-01-14
It's definitely hanging on the Asus splash screen.

I doesn't get as far as the ubuntu login screen.

Any help would be appreciated.

---

### Post by Titan8990 on 2009-01-14
Can you get in to the BIOS to restore the factory defaults?

---

### Post by redilyn on 2009-01-14
Can you press esc when the splash screen first shows to see if there are any errors being displayed during post?

---

### Post by Titan8990 on 2009-01-14
redilyn, he is not getting that far.

---

### Post by redilyn on 2009-01-14
LoL, If he isn't getting to post he better pull the cmos battery!

POST = Power On Self Test which occurs when the power button is pressed

The post messages are hidden by the spash screen when the laptop is turned on. If he presses esc he should see the messages as they scroll by and possibly any errors. :)

---

### Post by Titan8990 on 2009-01-14
Do laptops usually have accessible CMOS batteries or does the BIOS run of the power supply battery?

---

### Post by redilyn on 2009-01-14
While I have never actually tryed to access a laptop cmos battery I think they have one (not 100% sure).

Searching on google seems to indicate that it should have a cmos battery that is accessible although I don't know how difficult that would be.

After thinking for a bit I did change a laptop cmos battery once. It was under the main battery covered by a little plastic cover. This was a long time ago (P3 era) but it might be a good place to start looking,

---

### Post by cartesian on 2009-01-14
Nothing happens if I press esc when the splash screen appears.

My laptop is a dual boot with Vista so I am reluctant to restore factory defaults in the BIOS. Will this affect my Windows installation?

Could I use a Live CD to boot ubuntu and then uninstall the ati driver?

I am new to linux so POST and cmos batteries is all going over my head.

Thanks

---

### Post by Titan8990 on 2009-01-14
POST and CMOS have absolutely nothing to do with Linux, Windows or any operating system.


Every computer has what is know as a BIOS (Basic input output system). The BIOS is essential for a computer to function.

The BIOS contains settings such as:

device boot order
hardware configurations
and many other things that your pre-built machine hides from you

Those configurations for the BIOS are stored in what is known as the CMOS. Clearing the CMOS restores the BIOS to factory defaults.


What is going on with your computer is it is failing the POST, which stands for Power On Self Test.


Basically what most likely has occurred is that your board or some other piece of hardware in your laptop has kicked the bucket.


How old is the laptop? Is it still under warrenty?

---

### Post by cartesian on 2009-01-14
The laptop is less than 12 months old.

I would be surprised if something has kicked the bucket as before I installed this ati driver the laptop worked with no problems. When I restarted it after the driver installation the problems began.

It boots into vista with no prblems at all, indeed I'm writing this on the laptop using the vista partition. 

Would I be able to use the vista partition if something on the laptop had kicked it?

Thanks for your help.

---

### Post by redilyn on 2009-01-14
Hold on now!

You described the problem as the system hanging on the ASUS splash screen. If this was truely the problem you would not be able boot into vista or any other operating system.

To clarify, you **do** get the grub menu but can not get the ubuntu splash screen??

If so try booting into recovery mode and select the option to repair x server (i think thats what it says)

---

### Post by cartesian on 2009-01-15
I can get to the grub menu to choose ubuntu or linux.

Yes I do see the Asus splash screen before the grub menu loads and then I always used to see another Asus splash screen after I chose ubuntu from the menu. (It was'nt ever displayed correctly though)

Anyway, I need to choose recovery mode in the grub menu?

I have commented out the lines I don't normally want displayed from the menu.lst file. How can I edit that now if it won't boot into ubuntu?

Thanks for your help. I understand it's very difficult diagnosing problems remotely.

---

### Post by redilyn on 2009-01-15
Yep you want recovery mode.

If you do not have that line in your grub menu just press the button to edit the line (its "e" i believe), then select the kernel line.

At the end of the kernel line it will say "ro quiet splash" change that to "ro single"

Example below

```

kernel	/vmlinuz-2.6.27-9-generic root=UUID=b3e79875-0842-45ee-9936-2f0bf4f3fae3 ro quiet splash 

```

Too

```

kernel	/vmlinuz-2.6.27-9-generic root=UUID=b3e79875-0842-45ee-9936-2f0bf4f3fae3 ro  single

```

If you can boot into recovery mode, try choosing the option to repair X server.

Hopefully this will help

---

### Post by cartesian on 2009-01-15
Class!

That worked! I was able to pick the option "try to fix x server' and then 'boot as normal' and happy days, we're in.

I've been able to shut down and restart normally too.

What does fix x server do if you've got time to explain?

Thanks for all your help, much appreciated.

---

### Post by mlrivera on 2009-01-17
I think I might have the same problem described by cartesian.
I have not been able to get the ATi driver to work, because it says it needs restarting the computer and after choosing on Grub "Ubuntu" it just goes blackscreen. I have been able to boot the computer in recovery mode and fixing x server, but it does not reboot properly thereafter, the Ati driver is installed but still not enabled, and so my screen resolution is pretty messed up.
I can boot to windows without problems -I've got it on another partition-, resolution works there fine, as everything else, but I don't want to be obligated to use windows because I can't get ubuntu to boot normally or work well.
Any idea what the problem is or how to fix it?

---

