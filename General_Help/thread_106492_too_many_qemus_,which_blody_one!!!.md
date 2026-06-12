---
title: "too many qemus ,which blody one!!!"
date: 2005-12-20
forum: General Help
---

### Post by markcaetano@gmail.com on 2005-12-20
hi peoplezz

im up shit creek without a paddle

i want to run 98SE on my celeron 500Mhz computer
i have some queries first

*which one do i download im so confused:confused:  cause there are so many of them
*will this be enough to run it at a useable pace

dell L500cx
500 Mhz celeron(overclocked to 511)
128 mb ram @ 100mhz
10.0 gb hdd
ubuntu 5.10
had 98 SE before linux(will this product recovery cd work?)

*how do i get the MBR to point straight to the GRUB loader when it boots

thanx in advance

Mark Caetano

---

### Post by markcaetano@gmail.com on 2005-12-20
whats with all this empty silence 
im really desperate

mark

---

### Post by aysiu on 2005-12-20
[QUOTE=markcaetano@gmail.com]whats with all this empty silence 
im really desperate

mark[/QUOTE] I think people aren't answering because they don't understand what you're asking. What's 98SE? The 98 makes me think Windows 98. What's SE, though? What does this have to do with Ubuntu?

---

### Post by Video Toaster on 2005-12-20
[QUOTE=aysiu]I think people aren't answering because they don't understand what you're asking. What's 98SE? The 98 makes me think Windows 98. What's SE, though? What does this have to do with Ubuntu?[/QUOTE]

Probably 98 Second Edition... but I don't understand what he's asking either.  Could you please clarify?

---

### Post by markcaetano@gmail.com on 2005-12-20
ok

98 SE is short for

Microsoft Windows 98 Second Edition

in full detail-

Microsoft windows grapical user environment version 4.10.4444(what a mouthfull!!)

i want to run 98 SE in qemu cause i have a lot of .exe files and games
and because the pc originally came with 98 SE can i use the product recovery program to install 98 in qemu

does that explain it better

---

### Post by Video Toaster on 2005-12-20
Hmm... I'm not sure, but I don't think it would work if your recovery CD is tied to the physical machine's BIOS, as the CD would see the fake QEMU machine instead of the machine's actual BIOS.  For example, I don't think a current Dell Operating System CD would work... I don't know about yours.

Also, would you be able to upgrade your RAM?  128 MB is kinda small for one operating system, let alone two.  I'm not sure what kind of speed you'd get with a 500 MHz processor, either.

---

### Post by aysiu on 2005-12-20
My guess is that if the .exe can run in Windows 98, most likely it can also run on Wine (and at native speeds). If Qemu runs an entire operating system (98), it'll definitely be slower than running an .exe on Wine.

P.S. There's only *one* Qemu I can see in Synaptic Package Manager (see attached screenshot).

[quote=Ubuntu User Guide PDF]
A bit about Wine... I don't know how it works, but it does seem to work with a lot of simple Windows programs. I'll show you how I get Filezilla to work in Linux, as an example.

Assuming I've already [enabled extra repositories](http://www.psychocats.net/linux/sources.php), first, I install Wine:
sudo apt-get update
sudo apt-get install wine

Then, I download the setup.exe file for Filezilla. When I double-click on it, Wine will try to open the file. Then, the installer appears, just as if I were using Windows. Instead of installing Filezilla to C:\Program Files\Filezilla\, I'm going to override the default installation location and install it to z:\home\username\.wine\drive_c\Program Files\Filezilla. For some reason, z:\ is what Wine calls my Ubuntu partition.

Then, I set up a launcher (on the panel or in the menu) for the command wine &#8220;z:\home\username\.wine\drive_c\Program Files\Filezilla\Filezilla.exe&#8221;

That's it. Now when I click on that launcher, Filezilla will load up.

If a Windows program does not work with Wine, you may need Crossover Office. Cedega is a special version of Wine that's made for Windows-only games.[/quote]

---

### Post by markcaetano@gmail.com on 2006-01-30
Tried it and it didnt work

---

### Post by deathshadow on 2006-01-30
My advice: Use VMWare instead of QEMU - the setup is easier and it has better compatability.

Even though with either solution you aren't going to have 3d accelleration, which is why I'd just consider dual booting.

---

### Post by markcaetano@gmail.com on 2006-01-30
i have set up a fat 32 partition with win98 put it dosent show up is the GRUB

---

