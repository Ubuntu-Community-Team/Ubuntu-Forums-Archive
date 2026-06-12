---
title: "Need to send in my laptop. How to hide ubuntu?"
date: 2009-02-02
forum: General Help
---

### Post by di11avou on 2009-02-02
Hi. 

I'm dual booting vista and ubuntu on my laptop. I made a seperate partition on the hard drive for ubuntu.

I have to send in my laptop for service and want to have it boot straight into windows like ubuntu wasn't even there.

What would be the best way to do this? And how would I reverse it once I get my laptop back?

Thanks for the help.

---

### Post by Agent ME on 2009-02-02
Just edit your /boot/grub/menu.lst file.
In a terminal:
```
export EDITOR=gedit
sudoedit /boot/grub/menu.lst
```
Set the default to the correct index (if windows is first on the boot list, put 0, if second, put 1, if third, 2, etc), and uncomment the hiddenmenu option (change "#hiddenmenu" to "hiddenmenu").

To change it back, just press escape on boot-up, and you can get to the operating system list menu.

---

### Post by Locutus_of_Borg on 2009-02-02
```
gksudo gedit /boot/grub/menu.lst
```
insert or edit into there:

```
timeout=0
hiddenmenu
default=#
```

where # is your vista entry (note the first listing is 0, the second is 1, etc)

when you get it back, to boot into ubuntu, right after your BIOS screen is displayed, tap the Esc key until grub loads, boot ubuntu, re-edit file

---

### Post by cdtech on 2009-02-02
Just fixmbr using your Windows CD then reinstall GRUB when you get it back. That way they could not even see or boot into the Ubuntu OS. Easy.........

**UPDATE::.**
I save a copy of my sector (MBR) so if I have problems with my boot partition I can reinstall it using the dd command. I have both the GRUB and Windows MBR and can switch between either on the fly. Good idea to save a copy of your MBR.

---

### Post by iitywygms on 2009-02-02
Be sure to back up.  I sent mine back and they reformatted the drive and reinstalled windows.

---

### Post by di11avou on 2009-02-04
Thanks for the help guys. This is my first attempt with linux and so far I'm really enjoying it. 


That's a good idea about backing up MBR and Grub. And I did make sure to save all my important files. Hopefully they don't have to reformat it.

---

### Post by stepram on 2009-04-10
Another tip, once you have changed the boot order you can add a blank tile line, this will leave the options below it on the menu but will hide the text for these options.  I have used it to hide Vista, but I'm sure it will work the other way round. 

[full instructions are on my blog; http://stephen.blog.kraya.net/2009/04/09/editing-grub-on-ubuntu-810/]("http://stephen.blog.kraya.net/2009/04/09/editing-grub-on-ubuntu-810/")

---

