---
title: "Updating menu.lst to current kernel version"
date: 2009-02-15
forum: General Help
---

### Post by Shobuz99 on 2009-02-15
Hi.
I've been reading a previous thread on updating boot/grub/menu.lst
to accommodate a windows partition... While reading, I saw a command to update the grub.. "sudo update-grub"... I tried this to get my menu.lst to run the most recent kernel version 2.6.27-11-generic. 

Currently, my menu.lst has 2.6.27-10-generic listed at the top (under the windows partition swap). The reason is because I chose, when the update was installed at the time, to leave the menu.lst as it was and not change the menu.lst. Now I think I made a dumb decision: partial list below:
[COLOR="Navy"]
[B]title		Windows XP Home
root		(hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader    +1

title		Ubuntu 8.10, kernel 2.6.27-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=8bb89afd-e18e-4e91-8a66-2394af41fb39 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-10-generic
quiet

title		Ubuntu 8.1[/SIZE]0, kernel 2.6.27-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=8bb89afd-e18e-4e91-8a66-2394af41fb39 ro  single
initrd		/boot/initrd.img-2.6.27-10-generic

title		Ubuntu 8.10, kernel 2.6.27-8-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-8-generic root=UUID=8bb89afd-e18e-4e91-8a66-2394af41fb39 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-8-generic
quiet[/B][/COLOR]



I was lazy and didn't want to re-edit menu.lst so that windows xp
could be on the top of the list....anyway...

I ran sudo update-grub and it appeared to update the menu.lst; but
when i opened the menu.lst file, version 2.6.27-11-generic was not
in the list. I want it to be the version I use when I select it from the grub/menu.lst instead of version 2.6.27-10-generic. 

results below:

[B][COLOR="DarkRed"]sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.27-10-generic
Found kernel: /boot/vmlinuz-2.6.27-8-generic
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-18-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

[/COLOR][/B]


How do I do that?

thank you for your advice and help.

Shobuz99

---

### Post by uidb4056 on 2009-02-15
> **Shobuz99 said:**
> Hi.
I've been reading a previous thread on updating boot/grub/menu.lst
to accommodate a windows partition... While reading, I saw a command to update the grub.. "sudo update-grub"... I tried this to get my menu.lst to run the most recent kernel version 2.6.27-11-generic. 

Currently, my menu.lst has 2.6.27-10-generic listed at the top (under the windows partition swap). The reason is because I chose, when the update was installed at the time, to leave the menu.lst as it was and not change the menu.lst. Now I think I made a dumb decision: partial list below:
[COLOR=Navy]
[B]title        Windows XP Home
root        (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader    +1

[COLOR=Lime]title        Ubuntu 8.10, kernel 2.6.27-10-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-10-generic root=UUID=8bb89afd-e18e-4e91-8a66-2394af41fb39 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-10-generic
quiet

title        Ubuntu 8.1[/size]0, kernel 2.6.27-10-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-10-generic root=UUID=8bb89afd-e18e-4e91-8a66-2394af41fb39 ro  single
initrd        /boot/initrd.img-2.6.27-10-generic
[/COLOR]  
title        Ubuntu 8.10, kernel 2.6.27-8-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-8-generic root=UUID=8bb89afd-e18e-4e91-8a66-2394af41fb39 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-8-generic
quiet[/B][/COLOR]



I was lazy and didn't want to re-edit menu.lst so that windows xp
could be on the top of the list....anyway...

I ran sudo update-grub and it appeared to update the menu.lst; but
when i opened the menu.lst file, version 2.6.27-11-generic was not
in the list. I want it to be the version I use when I select it from the grub/menu.lst instead of version 2.6.27-10-generic. 

results below:

[B][COLOR=DarkRed]sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.27-10-generic
Found kernel: /boot/vmlinuz-2.6.27-8-generic
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-18-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

[/COLOR][/B]


How do I do that?

thank you for your advice and help.

Shobuz99

You can edit menu.lst file with running from terminal 'sudo gedit /boot/grub/menu.lst'

Then select the marked green lines do copy and paste to duplicate, then replace the number 10 of each line appearing the kernel number with 11 on the first set of lines you have copied.

---

### Post by Shobuz99 on 2009-02-15
> **uidb4056 said:**
> You can edit menu.lst file with running from terminal 'sudo gedit /boot/grub/menu.lst'

Then select the marked green lines do copy and paste to duplicate, then replace the number 10 of each line appearing the kernel number with 11 on the first set of lines you have copied.

uidb4056,

Ok. I did what you suggested. It seems to have worked. 
But was it really THAT simple all along? Wow..
I thought that simply changing the version number was 'cosmetic',
and that the "kernel /boot/vmlinuz-2.6.27-10-generic *root=UUID=8bb89afd-e18e-4e91-8a66-2394af41fb39*... is unique to  version 10... 
so I thought that just changing the number from 10 to 11 would not make a difference.
Also, I've forgotten what command I use in terminal mode to see what version of the kernel is actually running...

Thanks uidb4056
I appreciate your help..

shobuz99

---

### Post by uidb4056 on 2009-02-15
> **Shobuz99 said:**
> Hi.
I've been reading a previous thread on updating boot/grub/menu.lst
to accommodate a windows partition... While reading, I saw a command to update the grub.. "sudo update-grub"... I tried this to get my menu.lst to run the most recent kernel version 2.6.27-11-generic. 

Currently, my menu.lst has 2.6.27-10-generic listed at the top (under the windows partition swap). The reason is because I chose, when the update was installed at the time, to leave the menu.lst as it was and not change the menu.lst. Now I think I made a dumb decision: partial list below:
[COLOR=Navy]
[B]title        Windows XP Home
root        (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader    +1

title        Ubuntu 8.10, kernel 2.6.27-10-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-10-generic root=UUID=8bb89afd-e18e-4e91-8a66-2394af41fb39 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-10-generic
quiet

title        Ubuntu 8.1[/size]0, kernel 2.6.27-10-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-10-generic root=UUID=8bb89afd-e18e-4e91-8a66-2394af41fb39 ro  single
initrd        /boot/initrd.img-2.6.27-10-generic

title        Ubuntu 8.10, kernel 2.6.27-8-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-8-generic root=UUID=8bb89afd-e18e-4e91-8a66-2394af41fb39 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-8-generic
quiet[/B][/COLOR]



I was lazy and didn't want to re-edit menu.lst so that windows xp
could be on the top of the list....anyway...

I ran sudo update-grub and it appeared to update the menu.lst; but
when i opened the menu.lst file, version 2.6.27-11-generic was not
in the list. I want it to be the version I use when I select it from the grub/menu.lst instead of version 2.6.27-10-generic. 

results below:

[B][COLOR=DarkRed]sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.27-10-generic
Found kernel: /boot/vmlinuz-2.6.27-8-generic
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-18-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

[/COLOR][/B]


How do I do that?

thank you for your advice and help.

Shobuz99

> **Shobuz99 said:**
> uidb4056,

Ok. I did what you suggested. It seems to have worked. 
But was it really THAT simple all along? Wow..
I thought that simply changing the version number was 'cosmetic',
and that the "kernel /boot/vmlinuz-2.6.27-10-generic *root=UUID=8bb89afd-e18e-4e91-8a66-2394af41fb39*... is unique to  version 10... 
so I thought that just changing the number from 10 to 11 would not make a difference.
Also, I've forgotten what command I use in terminal mode to see what version of the kernel is actually running...

Thanks uidb4056
I appreciate your help..

shobuz99

We are here to help people and get help too. For your information what I told you to do works because the related kernel files exist (you can look for it at /boot folder).

Regarding to '[I]root=UUID=8bb89afd-e18e-4e91-8a66-2394af41fb39' is equivalent to 'root=(hdx,y)' the UUID string is a unique ID for each partition in your system, you can inspect this running in terminal 'sudo blkid' and you can see all UUID's of your partitions.

[/I]

---

### Post by Shobuz99 on 2009-02-15
> **uidb4056 said:**
> We are here to help people and get help too. For your information what I told you to do works because the related kernel files exist (you can look for it at /boot folder).

Regarding to '[I]root=UUID=8bb89afd-e18e-4e91-8a66-2394af41fb39' is equivalent to 'root=(hdx,y)' the UUID string is a unique ID for each partition in your system, you can inspect this running in terminal 'sudo blkid' and you can see all UUID's of your partitions.

[/I]

Thank you very very much!I appreciate it.

Shobuz99

---

### Post by mcduck on 2009-02-15
By the way, if you move the Windows entry to correct place in the menu.lst you can safely let updates reqrite the file and still keep windows entry.

Just keep it outside of the section marked as "Debian automagick kernels list". Just put the Windows entry right before this section if you want Windows to appear first on the list. Only the "automagick kernels list"-section is rewritten during updates, everything outside it will stay.

(actually even the comments in the menu.lst file will tell you this.. ;))

---

### Post by Shobuz99 on 2009-02-15
> **mcduck said:**
> By the way, if you move the Windows entry to correct place in the menu.lst you can safely let updates reqrite the file and still keep windows entry.

Just keep it outside of the section marked as "Debian automagick kernels list". Just put the Windows entry right before this section if you want Windows to appear first on the list. Only the "automagick kernels list"-section is rewritten during updates, everything outside it will stay.

(actually even the comments in the menu.lst file will tell you this.. ;))

Thanks McDuck!

My menu.lst is slightly different than the syntax you referred to, 
but I tried anyway, and it seems to work. Partial of my menu.lst:

.......
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
title		Windows XP Home
root		(hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader    +1
## DO NOT UNCOMMENT THEM, Just edit them to your needs


thanks again.
shobuz99

---

### Post by logos34 on 2009-02-15
You might want to move that windows entry to the bottom of menu.lst:

> "Your Windows entry to be automagically deleted every time Ubuntu is updated with a new kernel if you paste it anywhere between the beginning and the end of the debian automagic kernels list. (Well, it shouldn't have been there in the first place). Many users don't understand that and blame GRUB or Ubuntu for their problems." 
[http://users.bigpond.net.au/hermanzone/p15.htm#DEBIAN_AUTOMAGIC_KERNELS_LIST](http://users.bigpond.net.au/hermanzone/p15.htm#DEBIAN_AUTOMAGIC_KERNELS_LIST)

---

### Post by Shobuz99 on 2009-02-15
> **logos34 said:**
> You might want to move that windows entry to the bottom of menu.lst:

logos34,

Wow..thanks for the advice and the link. I will definitely use this to my enjoyment! I appreciate it.

Shobuz99

---

### Post by mcduck on 2009-02-16
> **Shobuz99 said:**
> Thanks McDuck!

My menu.lst is slightly different than the syntax you referred to, 
but I tried anyway, and it seems to work. Partial of my menu.lst:

.......
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
title		Windows XP Home
root		(hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader    +1
## DO NOT UNCOMMENT THEM, Just edit them to your needs


thanks again.
shobuz99
Just move the windows entry above the "### BEGIN AUTOMAGICK KERNELS LIST"-line and everything will be fine.

---

