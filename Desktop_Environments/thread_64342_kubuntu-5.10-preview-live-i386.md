---
title: "kubuntu-5.10-preview-live-i386"
date: 2005-09-10
forum: Desktop Environments
---

### Post by arjaybe on 2005-09-10
I burned this and it's fine except my mouse doesn't work.  It should be easy to fix but I don't know the root password to reconfigure xorg.

---

### Post by mlomker on 2005-09-10
I think you can just preface your commands with **sudo** instead of su-ing to root.

---

### Post by popuman on 2005-09-10
Well, actually this is the first time Kubuntu actually works with my machines. It recognized the wireless card immediately and works like a charm. Thank you guys! Keep up the good work!

---

### Post by arjaybe on 2005-09-11
I was able to sudo dpkg-reconfigure xserver-xorg but the mouse section wasn't very complete.  I need to be able to select ttyS0 for my serial mouse.  Oh well, it's just a live cd and it's on a rewriteable, so no loss.

---

### Post by mlomker on 2005-09-12
Have you tried editing the /etc/X11/xorg.conf file and then restarting the desktop (Ctrl-Alt Backspace)?

---

### Post by arjaybe on 2005-09-12
[QUOTE=mlomker]Have you tried editing the /etc/X11/xorg.conf file and then restarting the desktop (Ctrl-Alt Backspace)?[/QUOTE]
 I was able to sudo kwrite /etc/X11/xorg.conf and edit the mouse section for Protocol and Device.  I used Microsoft and /dev/ttyS0, since I have a serial mouse.  I'm happily posting now from the live CD.

I see from your signature that you're running an AMD64.  I'll be getting some new hardware soon and I'm wondering I should get a 64 bit processor.  Do you have any problems or advice?

---

### Post by benson on 2005-09-12
is KBFX included in kubuntu-5.10? :)

---

### Post by mlomker on 2005-09-12
[QUOTE=arjaybe]I'll be getting some new hardware soon and I'm wondering I should get a 64 bit processor.  Do you have any problems or advice?[/QUOTE]

I like the idea of the 64-bit machines because you can always run the 32-bit version of Ubuntu on it if you want to.  I'm running the 64-bit, but there isn't a modem driver (for the card in my laptop), no Realplayer, no Macromedia Flash.

I'd definitely say YES to AMD, but you have to decide if you can deal with the more limited driver support when running the amd64 version of linux.

---

### Post by eneanito on 2005-10-05
if you can deal with the more limited driver support when running the amd64 version of linux.

mlonker:
If 32 bit software woeks fine w/ 64 HW Why don't drivers do?

I am trying w/ AMD64 live CD
My Machine is 

Board MSI R480 939
Atlon64 3.0 GH
mem DDR 2X256 /400 Markvision
HD IBM Histachi 8060 (I believe it is SATA - I don´t know what it means)
LCD 17" ACER monitor, a truly jewel!

Upload goes very well as far displaying a central rectangle near 15cm long X 6 cm tall with UBUNTU name, logo and down text "for human beings"

Cursor has movility while that rectangle is drawing and stay cool in the too moment it is lfinished?

What happens?

Thanks for read and guide me

---

### Post by mlomker on 2005-10-05
> If 32 bit software woeks fine w/ 64 HW Why don't drivers do?


Drivers have to be 64-bit because they tie into the kernel.  chroot is kind of like running a virtual 32-bit machine inside your 64-bit machine...if you think of it as a ladder then the 32-bit programs are at the 3rd rung.

---

### Post by eneanito on 2005-10-06
mlomker:

Thank you. Have you an idea about the prob. I'd asked? LiveCD in AMD 64

---

### Post by eneanito on 2005-10-06
mlomker:

Thank you. Have you an idea about the prob. I'd asked?:
  "LiveCD in AMD 64"

---

### Post by mlomker on 2005-10-06
>  "LiveCD in AMD 64"

I didn't understand the problem.  Are you saying that gnome is trying to load but it stops somewhere along the way?  Have you tried the i386 liveCD?  You might want to ask your question as a new post in the liveCD forum.

---

### Post by eneanito on 2005-10-08
About 64, it puts all text displays an a graph red display with a central rectangle whit logo and word "UBUNTU" ...soft for human beings. When that rectangle just finish to be drew, all life signal is lost. The image remains stupidly unmobil and cursor too.

About 32, it puts very much text displays but stops
after it says:

ohci _hcd 0000:00:13.1: unlink after no - IRQ? Different ACPI or APIC settings may help [/font]

I don´t know what ACPI , APIC mean

---

### Post by mlomker on 2005-10-09
> I don&#180;t know what ACPI , APIC mean

They are for power management.  You could try either updating your BIOS or disabling them.

---

### Post by Velox Letum on 2005-10-09
Or booting with the option acpi=off

---

