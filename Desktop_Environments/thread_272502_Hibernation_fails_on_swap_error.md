---
title: "Hibernation fails on swap error"
date: 2006-10-06
forum: Desktop Environments
---

### Post by nofrak on 2006-10-06
I recently did some partitioning of my drive that involved me replacing my extended swap partition with a primary one so that i could have an extended partition elsewhere on the disk.  Now when I try to hibernate, I get a message about needing to run swapon /a, and then it takes me back to the locked screen login box.  

Are these two related (I don't use hibernation all that often, so I'm not positive)?  Do I need to manually point the hibernation directions to the new swap partition?  Or will it just not work with Swap as primary instead of extended?

Help me ubuntu-forums: you are my only hope.

---

### Post by Daniel15 on 2006-10-08
> I get a message about needing to run swapon /a, and then it takes me back to the locked screen login box

I had the same problem when I moved my partitions around. I searched around everywhere but couldn't find how to fix it. Eventually, I discovered it myself. I fixed it by doing this:
 - Edit **/etc/mkinitramfs/conf.d/resume** to point to the new swap partition. You can do this using any editor, but you'll need to edit it as root:
```

gksu gedit /etc/mkinitramfs/conf.d/resume

``` (if using gedit)

```

sudo nano /etc/mkinitramfs/conf.d/resume

``` (if using nano)

 - Edit **/boot/grub/menu.lst** to have a 'resume=' parameter for both the default options, and the kernel you use. To do this, open /boot/grub/menu.lst, and find a line starting with # defoptions= (as an example, mine was ```
# defoptions=quiet splash
```). At the *end* of this line, add 'resume=' followed by your swap partition. For example, mine now looks like:
```

# defoptions=quiet splash resume=/dev/sda8

```
DON'T remove the # at the start!

Next, scroll down to the bottom of that file, and find the kernel that you're using (in my case, I'm using the 2.6.15-27-686 kernel). At the *end* of the 'kernel' line for this kernel, add the same 'resume=' parameter. As an example, my kernel section looked like:
```

...
title           Ubuntu, kernel 2.6.15-27-686
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.15-27-686 root=/dev/sda6 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-686
savedefault
boot
...

```

After editing, it now looks like:
```

...
title           Ubuntu, kernel 2.6.15-27-686
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.15-27-686 root=/dev/sda6 ro quiet splash resume=/dev/sda8
initrd          /boot/initrd.img-2.6.15-27-686
savedefault
boot
...

```

Save and exit, and then restart your computer. Hibernation should now be working fine :)

---

### Post by RikoW on 2006-10-08
I had the same problem for the same reason. Find here the solution I tried successfully:

[http://ubuntuforums.org/showthread.php?t=273118]("http://ubuntuforums.org/showthread.php?t=273118")

Hope that helps, :)

                Riko

---

