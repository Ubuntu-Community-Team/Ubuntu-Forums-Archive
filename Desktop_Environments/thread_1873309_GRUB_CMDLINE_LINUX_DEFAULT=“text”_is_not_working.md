---
title: "GRUB_CMDLINE_LINUX_DEFAULT=“text” is not working"
date: 2011-11-01
forum: Desktop Environments
---

### Post by m_abdelfattah on 2011-11-01
I am trying to make Ubuntu run in text mode only as I want to use it as local server. I searched and found that I should edit /etc/default/grub and replace quiet splash with text then run update-grub, but nothing happens. Any suggestions?

---

### Post by haqking on 2011-11-01
> **m_abdelfattah said:**
> I am trying to make Ubuntu run in text mode only as I want to use it as local server. I searched and found that I should edit /etc/default/grub and replace quiet splash with text then run update-grub, but nothing happens. Any suggestions?

you need to do the following after making grub changes

```
sudo update-grub
```

However if it is 11.10 then the "text" no longer works, it is dont with a .override file

[http://ubuntuforums.org/showpost.php?p=10798400&postcount=4](http://ubuntuforums.org/showpost.php?p=10798400&postcount=4)

---

### Post by m_abdelfattah on 2011-11-01
Thanks haqking for your fast reply, but I did what mentioned in the topic u suggested but nothing. I still log-in to GUI mode.

---

### Post by haqking on 2011-11-01
> **m_abdelfattah said:**
> Thanks haqking for your fast reply, but I did what mentioned in the topic u suggested but nothing. I still log-in to GUI mode.

so it is 11.10 you have ?

Why not install Ubuntu server which comes with no GUI as you want a server ?

So you did everything in the link ? (presuming you are running 11.10 that is)

---

### Post by m_abdelfattah on 2011-11-01
Yes, I've 11.10 and I did everything in the link !

---

### Post by haqking on 2011-11-01
> **m_abdelfattah said:**
> Yes, I've 11.10 and I did everything in the link !

can you post the contents of your grub and the gdm.override

Cheers

---

### Post by m_abdelfattah on 2011-11-01
/etc/init/gdm.override
```
manual
```

/etc/default/grub
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by devos50 on 2011-11-01
I´m also having the same problem, only difference is that I am on ubuntu server where I want a GUI for some easy management if needed, but by default I want to start in text-mode. After installing ubuntu-desktop, it boots default with the GUI. In 11.04 I could just use GRUB_CMDLINE_LINUX_DEFAULT= quiet text but I just upgraded to 11.10 and I can´t use it anymore: it will still boot in GUI. Also, that gmd.override trick is also not working for me :(

Any help with this problem would be greatly appreciated:D

---

### Post by haqking on 2011-11-01
> **devos50 said:**
> I´m also having the same problem, only difference is that I am on ubuntu server where I want a GUI for some easy management if needed, but by default I want to start in text-mode. After installing ubuntu-desktop, it boots default with the GUI. In 11.04 I could just use GRUB_CMDLINE_LINUX_DEFAULT= quiet text but I just upgraded to 11.10 and I can´t use it anymore: it will still boot in GUI. Also, that **gmd**.override trick is also not working for me :(

Any help with this problem would be greatly appreciated:D

it is gdm not gmd.

However i presume you both did a

```
sudo update-grub
```

after editing the grub ?

and its the gdm.override there after a reboot ?

---

### Post by m_abdelfattah on 2011-11-01
> **haqking said:**
> it is gdm not gmd.

However i presume you both did a

```
sudo update-grub
```

after editing the grub ?

and its the gdm.override there after a reboot ?

Yes, I did 
```
sudo update-grub
```

and gdm.override still exists after reboot.

---

### Post by devos50 on 2011-11-01
> **haqking said:**
> it is gdm not gmd.

However i presume you both did a

```
sudo update-grub
```after editing the grub ?

and its the gdm.override there after a reboot ?

Yeah I meant gdm. I did sudo update-grub and gdm.override is also still there after a reboot.

---

### Post by haqking on 2011-11-01
mmmm the answer is i dont know....LOL

I am guessing it is LDM related as 11.10 now uses LDM.

I will play in a Virtual machine in a little while and get back to ya unless someone else chimes in.

cheers

---

### Post by sisco311 on 2011-11-01
> **haqking said:**
> 
I am guessing it is LDM related as 11.10 now uses LDM.


D'oh! Of course, 11.10 defaults to LightDM. So we have to disable LightDM, not GDM... 

```
echo 'manual' | sudo tee /etc/init/**lightdm**.override
```

---

### Post by drs305 on 2011-11-01
Regarding the original post:

Are you sure "text" is a valid kernel option? I've not seen that used in a Grub 'linux' line before, but I learn something new every day. If it can be used as a kernel option I'd appreciate seeing the link.

I use the following as my kernel options page, but it could be outdated:
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt]("http://www.kernel.org/doc/Documentation/kernel-parameters.txt")

---

### Post by devos50 on 2011-11-01
> **sisco311 said:**
> D'oh! Of course, 11.10 defaults to LightDM. So we have to disable LightDM, not GDM... 

```
echo 'manual' | sudo tee /etc/init/**lightdm**.override
```

Thank you for your response, but im still booting in GUI. The file lightdm.override is there. Is there anything else I can do?

And text is a valid boot option. I used to boot into text mode with it on 11.04 :)

---

### Post by drs305 on 2011-11-01
> **devos50 said:**
> 
And text is a valid boot option. I used to boot into text mode with it on 11.04 :)

Thanks for that! :-)

I can't reboot my real system for the moment but the 'text' option did work in my VM's. For what it's worth, it worked in both Natty *and* Oneiric without any modifications of system files.

---

### Post by sisco311 on 2011-11-01
> **drs305 said:**
> Regarding the original post:

Are you sure "text" is a valid kernel option? I've not seen that used in a Grub 'linux' line before, but I learn something new every day. If it can be used as a kernel option I'd appreciate seeing the link.

I use the following as my kernel options page, but it could be outdated:
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt]("http://www.kernel.org/doc/Documentation/kernel-parameters.txt")

Well, not a *real* kernel option, because it wasn't interpreted by the kernel. 

It was a *dirty hack* used by GDM's Upstart job to prevent GDM from running if the **text** parameter is present. Here is the relevant part of the code:
```

cat /etc/init/gdm.conf

# gdm - GNOME Display Manager
...
    # Check kernel command-line for inhibitors
     for ARG in $(cat /proc/cmdline)
     do
         case "${ARG}" in
             **text**|-s|s|S|single)
                 **exit 0**
                 ;;
         esac
     done
...

```

---

### Post by drs305 on 2011-11-01
That makes perfect sense now. Thanks *sisco311*.

---

### Post by haqking on 2011-11-01
> **sisco311 said:**
> D'oh! Of course, 11.10 defaults to LightDM. So we have to disable LightDM, not GDM... 

```
echo 'manual' | sudo tee /etc/init/**lightdm**.override
```

ahh cool, i tried with a ldm.override and it wasnt working......i never thought to try lightdm.override

LOL

I was only playing in a VM for the purposes of helping out in this thread, but glad i got it sorted for future reference

cheers

---

### Post by m_abdelfattah on 2011-11-02
> **sisco311 said:**
> D'oh! Of course, 11.10 defaults to LightDM. So we have to disable LightDM, not GDM... 

```
echo 'manual' | sudo tee /etc/init/**lightdm**.override
```

Thanks Sisco311, that works for me :)

---

### Post by sisco311 on 2011-11-02
You are welcome!

Don't forget to mark this thread as solved.

---

