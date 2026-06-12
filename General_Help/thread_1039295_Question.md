---
title: "Question?"
date: 2009-01-14
forum: General Help
---

### Post by azmo35 on 2009-01-14
Hi to all,but i have one new question, maybe this look stupid but my experience with Ubuntu is only of a few mounts so my question is, today my karnel was been update from 2.6.24-22 to 2.6.24-23 but on my grub menu is still show the older, i look through synaptic and the two are marked.Could someone help me understand this many thanks, azmo:confused:

---

### Post by Titan8990 on 2009-01-14
Sounds like a bug, does that kernel exist in the /boot dir? Do you have a separate boot partition?

---

### Post by azmo35 on 2009-01-14
Thanks for your reply, i do not have a separete boot partition,but on my boot folder i have this abi-2.6.24-22 abi-2.6.24-23 config-2.6.24-22 config-2.6.24-23 initrd-img-2.6.24-22 initrd-img-2.6.24-23 system-map-2.6.24-22 system-map-2.6.24-23 vmlinux-2.6.24-22 vmlinux-2.6.24-23 all generic and  backup for 2.6.24-22 and 2.6.24-23.

---

### Post by Titan8990 on 2009-01-14
This should have occurred automatically but you can manually edit menu.lst to  include your new kernel. 

Do:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak

gksu gedit /boot/grub/menu.lst


Just copy and past the lines of your current boot config and change the numbers to match your new kernel. Leave the existing lines in case it does not work, this way you can still boot your old kernel as needed.

If things really go wrong (not likely), you will need to restore the backup of menu.lst using the liveCD.

---

### Post by whoop on 2009-01-14
I think it's updated and installed correctly, but grub has not detected it (yet). So maybe your menu.lst is outdated.

I always do it manually
```

sudo nano /boot/grub/menu.lst

```

And copy your last kernel entry completely (looks something like this):
```

//DON'T COPY THIS. COPY FROM YOUR OWN FILE
title           Ubuntu 8.10, kernel 2.6.27-9-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.27-9-generic root=UUID=XXXXXXXXXXX ro
initrd          /boot/initrd.img-2.6.27-9-generic
quiet

```

paste it as the last entry in your menu.lst file
then change the version numbers in all the lines

There's also some command for this, update-grub. But I never used this.

---

### Post by KeyserSoze93 on 2009-01-14
Have you tried "sudo update-grub" to force it to regenerate the menu? That should have been run when the new kernel was installed, but you can make sure by doing it manually.

---

### Post by azmo35 on 2009-01-14
Thanks again i will do what you sugest and will be back to let you know if worked.

---

### Post by jocko on 2009-01-14
It's not a bug. If a kernel update changes the revision number of the package (such as 2.6.24[COLOR=Red]-22[/COLOR] --> 2.6.24[COLOR=Red]-23[/COLOR]), the old one is kept as a backup in case something is wrong with the new one.
If you want to clean up the boot menu, just uninstall the older kernel through synaptic (but it may be a good idea to keep it for a few days just to see that the new one does not cause any problems). Uninstalling it will automatically update the boot menu.
Editing menu.lst manually as some people have suggested will only be a temporary solution, as the old kernel will reappear in the menu every time an update runs update-grub.

---

### Post by azmo35 on 2009-01-14
Hi again but the code "sudo update-grub" still show 2.6.24-22 and 2.6.24-22 recovery mode

---

### Post by Titan8990 on 2009-01-14
> **jocko said:**
> It's not a bug. If a kernel update changes the revision number of the package (such as 2.6.24[COLOR=Red]-22[/COLOR] --> 2.6.24[COLOR=Red]-23[/COLOR]), the old one is kept as a backup in case something is wrong with the new one.
If you want to clean up the boot menu, just uninstall the older kernel through synaptic (but it may be a good idea to keep it for a few days just to see that the new one does not cause any problems). Uninstalling it will automatically update the boot menu.
Editing menu.lst manually as some people have suggested will only be a temporary solution, as the old kernel will reappear in the menu every time an update runs update-grub.


Jocko, his problem was not that the old kernel DOES exist but the new kernel DID NOT exist....

---

### Post by bixejo on 2009-01-14
> **Titan8990 said:**
> Jocko, his problem was not that the old kernel DOES exist but the new kernel DID NOT exist....
I must admit that when I read the OP first time, I did understand just the same that Jocko did... (and still not sure)

*Edit: post #12 from OP makes it clear now. Both Jocko and me were wrong...*

---

### Post by azmo35 on 2009-01-14
Jocko,i think you are spot on, that is my question, i'm comfortable with menu.lst and when move from wubi to real partition i end up with a few karnels but now only the 2.6.24-22 was show on my menu.lst so if i remove one synaptic, may will start my problems because 2.6.24-23 is not ther,thanks.

---

### Post by jocko on 2009-01-14
> **Titan8990 said:**
> Jocko, his problem was not that the old kernel DOES exist but the new kernel DID NOT exist....
Where did you read that?
> **azmo35 said:**
> Hi to all,but i have one new question, maybe this look stupid but my experience with Ubuntu is only of a few mounts so my question is, today my karnel was been update from 2.6.24-22 to 2.6.24-23 but on [COLOR=Red]my grub menu is still show the older[/COLOR], i look through synaptic and the two are marked.Could someone help me understand this many thanks, azmo:confused:
If my problem was that the new kernel did not appear, I would say the new one was missing, not that the old one is still there...

Edit: See above... I was wrong...

If the new kernel is really missing from the menu, do not uninstall the old one...
So you've moved from wubi to a real install... That could have messed things up a little. Maybe grub still uses a menu.lst from the wubi install and not the real one??? Or perhaps update-grub uses the wrong menu.lst...

---

### Post by Titan8990 on 2009-01-14
> **bixejo said:**
> I must admit that when I read the OP first time, I did understand just the same that Jocko did... (and still not sure)

lol and now I am unsure....


Edit: red highlighting makes it clear now....

If you would like the kernel removed, follow jocko's instructions. Always make sure the new kernel works prior to removing the old one.

---

### Post by albinootje on 2009-01-14
> **azmo35 said:**
> today my karnel was been update from 2.6.24-22 to 2.6.24-23 but on my grub menu is still show the older, i look through synaptic and the two are marked.

You're writing that /boot shows the newer kernel, and Synaptic shows it too.
Are you sure it's not visible in the Grub menu ?

You can install startupmanager to make it easier to change your boot menu.
```

sudo apt-get install startupmanager

```

After installing, it's in -> System -> Administration -> StartUp-Manager

---

### Post by azmo35 on 2009-01-14
Well some people are more worried with a few mistakes that some on made but what i want to is solve this, so part of my menu.lst...

# ## End Default Options ##

title		Ubuntu 8.04.1
root		(hd0,1)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=ad51ef36-da6e-4e45-8d6a-c989ffa69d2f  ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,1)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=ad51ef36-da6e-4e45-8d6a-c989ffa69d2f  ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST#

many thanks for your replys,azmo.

---

### Post by azmo35 on 2009-01-14
So Jocko what you sugest to solve this problem,thanks.

> If the new kernel is really missing from the menu, do not uninstall the old one...
So you've moved from wubi to a real install... That could have messed things up a little. Maybe grub still uses a menu.lst from the wubi install and not the real one??? Or perhaps update-grub uses the wrong menu.lst...

---

### Post by Titan8990 on 2009-01-14
It appears that I did understand correctly...

Add this to you menu.lst:


```
title Ubuntu 8.04.1
root (hd0,1)/ubuntu/disks
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=ad51ef36-da6e-4e45-8d6a-c989ffa69d2f ro quiet splash
initrd /boot/initrd.img-2.6.24-23-generic

title Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root (hd0,1)/ubuntu/disks
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=ad51ef36-da6e-4e45-8d6a-c989ffa69d2f ro single
initrd /boot/initrd.img-2.6.24-23-generic
```

---

### Post by albinootje on 2009-01-14
> **azmo35 said:**
> Well some people are more worried with a few mistakes that some on made but what i want to is solve this, so part of my menu.lst...

It's best to put a new entry before this line : 
```

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

```
Or after the end of "AUTOMAGIC kernel list".

And can you please post the output of :
```

dpkg -l|grep linux-image

```

---

### Post by azmo35 on 2009-01-14
> **albinootje said:**
> It's best to put a new entry before this line : 
```

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

```
Or after the end of "AUTOMAGIC kernel list".

And can you please post the output of :
```

dpkg -l|grep linux-image

```

 > azmo@azmo-laptop:~$ dpkg -l|grep linux-image
rc  linux-image-2.6.24-19-generic              2.6.24-19.41                                Linux kernel image for version 2.6.24 on x86
rc  linux-image-2.6.24-21-generic              2.6.24-21.43                                Linux kernel image for version 2.6.24 on x86
ii  linux-image-2.6.24-22-generic              2.6.24-22.45                                Linux kernel image for version 2.6.24 on x86
ii  linux-image-2.6.24-23-generic              2.6.24-23.46                                Linux kernel image for version 2.6.24 on x86
ii  linux-image-generic                        2.6.24.23.25                                Generic Linux kernel image
azmo@azmo-laptop:~$ :rolleyes:

---

### Post by albinootje on 2009-01-14
> **azmo35 said:**
> 
ii linux-image-2.6.24-23-generic 2.6.24-23.46 Linux kernel image for version 2.6.24 on x86


Good. 
The "ii" means that there were no problems detected during the installation, that kernel should be installed correctly.

---

### Post by azmo35 on 2009-01-14
Good for mi a newbe said that is intalled and working,but the question is how i prevent this on the next update and how to know if i use the correct menu.lst,thanks.

---

### Post by albinootje on 2009-01-14
> **azmo35 said:**
> Good for mi a newbe said that is intalled and working,but the question is how i prevent this on the next update and how to know if i use the correct menu.lst,thanks.

Can you run :

```

sudo update-grub

```
Post any errors, and then post the complete output of /boot/grub/menu.lst please ? Thanks.

And you don't have StartUpManager installed and in use ?
Because I do, and I have only one kernel entry in the Grub config, but.. it's the newest kernel, the 2.6.24-23-generic.

---

### Post by azmo35 on 2009-01-14
Well i add what Titan8990 said to do[PHP]Add this to you menu.lst:[/PHP][HTML]title Ubuntu 8.04.1
root (hd0,1)/ubuntu/disks
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=ad51ef36-da6e-4e45-8d6a-c989ffa69d2f ro quiet splash
initrd /boot/initrd.img-2.6.24-23-generic

title Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root (hd0,1)/ubuntu/disks
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=ad51ef36-da6e-4e45-8d6a-c989ffa69d2f ro single
initrd /boot/initrd.img-2.6.24-23-generic[/HTML] and worked fine, the only thing i got on mi mind is next karnel update maybe will happen again for now thanks for all that reply.

---

### Post by jocko on 2009-01-16
I got a new idea for how to try to fix your problem: force update-grub to generate a completely new menu.lst:
1. Rename your old menu.lst:
```
sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.bak
``` (note that this temporarily leaves you without a menu.lst, so do not reboot at this stage).
2. Have update-grub make a new one:
```
sudo update-grub
```(you will be told there is no menu.lst and asked if you want a new one to be generated, answer "y" for yes).
3. Update-grub does not look for windows, so you will need to copy everything after "### END DEBIAN AUTOMAGIC KERNELS LIST" from the old meny.lst to the new one:
```
gksudo gedit /boot/grub/menu.lst.bak /boot/grub/menu.lst
``` (this will open both files in tabs in gedit, just browse to the end of the old file, copy the windows entry from there and paste it in the end of the new one. You may also want to make sure the boot menu will not be hidden, so find this section:```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR=Blue]#[/COLOR] hiddenmenu
```Make sure there is a "#" in front of the last "hiddenmenu".
And while you have the new one open, check if the new kernel is there.

If this would not work out, just rename the backup:
```
sudo mv /boot/grub/menu.lst.bak /boot/grub/menu.lst
```

---

### Post by azmo35 on 2009-01-20
Tanks for your reply but i add like suggested the new kernel,and today is the 4td day i boot from the new kernel [2.6.24-23] and so far it is working, thanks again to all that help me.

---

