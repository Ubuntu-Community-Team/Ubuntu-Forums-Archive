---
title: "System hang on hibernate / shutdown"
date: 2005-04-29
forum: Desktop Environments
---

### Post by dave9191 on 2005-04-29
This is something that has me a little stumped. Sometimes when i try to shut the system down or hibernate it. It will completly lock up. No keyboard or mouse response. All i can do is just brutally turn it off. Ive yet to see a pattern of when it locks up. It doesnt do this under windows or the old version of ubuntu. 

I know this is insanly little info, but thats all ive got to work on. Any help would be appriciated. 

Dave

---

### Post by muzza on 2005-04-29
I can't help you, but I can confirm that it has happened to me a few times recently.

Just to let you know what I was doing... over two nights, I finally connected to ADSL and installed a modem/router. I also installed Kubuntu desktop and fiddled and tweaked to get the network and sound working.

I also tried to share some partitions with Windoze. Spent a lot of time in the terminal typing stuff that others suggested (coz they told me to!) and I can't tell you at what point the peeoota froze.

It hasn't done it for two nights now and things seem to have settled. 

Maybe I should stay away from that command line!

---

### Post by InvIsiBlekID on 2005-09-19
i have the same problem on my sony vaio laptop.  whenever i try to shut down ubuntu, it locks up.  i do not have the problem with windoze but if anyone has any help it would be appreciated.  

im using Breezy pre-release 5.10 (not kde, but it shouldnt matter for this....at least i dont think)

---

### Post by mlomker on 2005-09-19
[QUOTE=dave9191]Ive yet to see a pattern of when it locks up. It doesnt do this under windows or the old version of ubuntu. 
[/QUOTE]

Does that mean you're running breezy?  Betas are betas.

That being said, I never try to hibernate or sleep on my laptop.  If you're running Hoary and it's hanging on a normal shutdown then that's unusual.

---

### Post by skoal on 2005-09-19
Typically, I believe these types of problems are related to the acpi implementation.  If you want to use acpi, then I don't know what to suggest.  You might want to pass a grub kernel boot time option acpi=off and solely use APM.  I think you can still do that, can't you? I think BIOS(s) using APM can hibernate as well.  I may be mistaken...

\\//_

---

### Post by TheIdiotThatIsMe on 2005-09-19
My computer also hangs every time I try to reboot or shut down. I use Hoary, and have not figured out why it does this. It hangs right after something about LVM Volumes [OK] and then hangs when it says Rebooting.... or Shutting Down.....

---

### Post by dave9191 on 2005-09-20
[QUOTE=mlomker]Does that mean you're running breezy?  Betas are betas.
[/QUOTE]

No, I was running Kubntu 5.04 when I posted this hence my choice of forums. The old version of ubuntu I was refering to was warty. I don't trust beta's for a full time OS. 

This is a thread I completely forgot about. The number of times that kubuntu would lock up on me reduced a lot after I made all sortf of changes. I stopped using kdm and just logged on the command line using startx if I wanted X. And I changed over to fluxbox. I stopped using hibernate and used suspend to RAM instead. 

I noticed some problems with the ACPI implementation on my computer. It woudn't power down usb ports in suspend to RAM. Which chewed up more battery then it should , but I could charge my laptop while the computer was in suspend, which was kinda cool. 

My system would occasionally freeze up when restoring from suspend to RAM, but on shutdowns it seemed ok now. But I reduced the number of shutdowns I did so I might have just stopped noticing. 

I've also stopped using ubuntu now and Im giving Gentoo a try. Looks like a really good distro for me :)

---

### Post by mlomker on 2005-09-20
> This is a thread I completely forgot about.


Someone with Breezy revived it and I didn't notice the original post date.

> 
I've also stopped using ubuntu now and Im giving Gentoo a try. Looks like a really good distro for me :)

I actually tried Gentoo first but their amd64 version hung on boot and Kubuntu worked on my machine.

---

### Post by dave9191 on 2005-09-20
[QUOTE=mlomker]
I actually tried Gentoo first but their amd64 version hung on boot and Kubuntu worked on my machine.[/QUOTE]

(K)Ubuntu was brilliant for me as everything worked out the box :D But now I feel its time to take more control.

As for breezy, there could be a huge number of reasons that might still get resolved before the release that are causing the halting. 

Dave

---

