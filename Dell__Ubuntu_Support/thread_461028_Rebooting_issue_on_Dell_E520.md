---
title: "Rebooting issue on Dell E520"
date: 2007-06-01
forum: Dell  Ubuntu Support
---

### Post by mifi on 2007-06-01
Hi

forgive me if this is the wrong forum (and please direct me to the right one)... I have searched the forums for this issue, but all I could find is something similar in the Apple forum.

I have just installed a fresh Dell E520 (core 2 duo, 2GB), and replaced the ATI compatible card video card for a nVidia product.
All is working very well, except the reboot.

When I tell it to reboot, Ubuntu shuts down until the last screen just before the reboot (you know, with the logo and the empty progress bar), and then hangs. Nothing happening.

The power down works just fine and actually switches off the machine, so it seems to be incapable of the restart.

Anyone any suggestions?

Thanks
Mifi

---

### Post by jimbob on 2007-06-01
I encountered this problem in Edgy and for a time during development in Feisty also but it seems to have gone away for now.

I achieved some success by adding acpi=off and noapic to the kernel boot line in /boot/grub/menu.lst.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by mifi on 2007-06-02
I understand acpi is used for plug'nplay features as well. 

Switching it off is used on older hardware, since acpi has to be supported by hardware.

However, my machine is a brand new Dell E520.

Perhaps I need to switch off acpi because my PC is Vista capable? ;) 

Some people seem to have the same problem on Kubuntu, but I do not see anyone with a solution.

mifi

---

### Post by jtp51 on 2007-06-02
I have this issue as well.

I googled "reboot E520" and found that I needed to add "reboot=b" under Bug #114854 at:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/114854](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/114854)

Booting with reboot=b works around the problem.

I have not a clue what that means at all...

Have you been able to solve this issue yet?

Thanks,

---

### Post by bapoumba on 2007-06-03
Thread moved to "Ubuntu Dell Support" sub forum.

---

### Post by mifi on 2007-06-04
> **jtp51 said:**
> 
Booting with reboot=b works around the problem.

It does. Thanks.

> **jtp51 said:**
> 
I have not a clue what that means at all...


Neither have I. 
I did do a little search, but it was not obvious to find it documented.
Anyways, it is working.

Thanks.
mifi

---

### Post by bapoumba on 2007-06-04
> **mifi said:**
> 
Neither have I. 
I did do a little search, but it was not obvious to find it documented.

So did I, out of curiosity.

[http://www.faqs.org/docs/Linux-HOWTO/BootPrompt-HOWTO.html]("http://www.faqs.org/docs/Linux-HOWTO/BootPrompt-HOWTO.html")
> The `reboot=' Argument

This option controls the type of reboot that Linux will do when it resets the computer (typically via /sbin/init handling a Control-Alt-Delete). The default as of v2.0 kernels is to do a `cold' reboot (i.e. full reset, BIOS does memory check, etc.) instead of a `warm' reboot (i.e. no full reset, no memory check). It was changed to be cold by default since that tends to work on cheap/broken hardware that fails to reboot when a warm reboot is requested. To get the old behaviour (i.e. warm reboots) use reboot=w or in fact any word that starts with w will work.

Other accepted options are `c', `b', `h', and `s', for cold, bios, hard, and SMP respectively. The `s' takes an optional digit to specify which CPU should handle the reboot. Options can be combined where it makes sense, i.e. reboot=b,s2


This howto can be found all over the place, and in many different languages.
Looks like "b"uses the bios reboot ?

---

### Post by mifi on 2007-06-04
> **bapoumba said:**
> So did I, out of curiosity.

[http://www.faqs.org/docs/Linux-HOWTO/BootPrompt-HOWTO.html]("http://www.faqs.org/docs/Linux-HOWTO/BootPrompt-HOWTO.html")

This howto can be found all over the place, and in many different languages.
Looks like "b"uses the bios reboot ?A very interesting link. Thanks for the addition.
mifi

---

### Post by magicfab on 2007-06-05
> **jtp51 said:**
> I have this issue as well.

I googled "reboot E520" and found that I needed to add "reboot=b" under Bug #114854 at:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/114854](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/114854)

Booting with reboot=b works around the problem.


You need to follow these steps:

1) Boot normally into the graphic environment
2) Open a terminal : Appllications > Accessories > Terminal
3) Edit the GRUB menu system file using admin rights, by issuiung this command:
> sudo gedit /boot/grub/menu.lst
4) Search for the folliowing text in the file:
> ## additional options to use with the default boot option, but not with the
5) A few lines below, replace the following line so it reads like this:
> # defoptions=quiet splash reboot=b
(do NOT remove the # signs)
6) Save the file, exit your terminal, reboot

This should make your change permanent, even through update.

Let us know if it works for you so I can put it up on Dell's wiki.

Cheers,

---

### Post by jtp51 on 2007-06-05
magicfab: I went through these steps and everything worked perfectly.

Thank you,

---

### Post by mifi on 2007-06-05
Ok. So I am spotting an opportunity to learn something... ;)

> **magicfab said:**
> 
5) A few lines below, replace the following line so it reads like this:

(do NOT remove the # signs)

I added the 'reboot=b' parameter to the line starting with 'kernel'. And it works for me. You seem to be adding the 'reboot=b' to a line that looks like it is comment.

I noticed the update-grub script will pick it up, probably removing one set op #'s. Hmmm. 

mifi

---

### Post by gavin2x on 2007-07-29
I have tried the reboot b, c, h, and w options and none seem to be working for me. I even got rid of the splash and quiet options just in case something was going on there. I should mention i am running 7.04 server headless (not a dell factory install). Any help would be much appreciated

---

### Post by gavin2x on 2007-07-31
I solved my problem. One of the post said to edit the stanza that looked like this:

# defoptions=quiet splash reboot=b

but after looking in the logs i noticed reboot=b was not being passed so i added it to the stanza i saw in the logs which looked like:

/boot/vmlinuz-2.6.20-15-server root=UUID=22908533-0687-4f1e-b1b4-b32ef70b588c ro quiet splash reboot=b

Then i sudo shutdown -h now (shutdown and halt) to make sure the kernel was loaded with the new args and tried sudo shutdown -r now (shutdown and restart) and it restarted as expected.

---

