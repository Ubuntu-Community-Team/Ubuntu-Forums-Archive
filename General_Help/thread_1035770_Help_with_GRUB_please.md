---
title: "Help with GRUB please"
date: 2009-01-10
forum: General Help
---

### Post by reflexsa on 2009-01-10
Hey people,

Sorry for the GRUB question, I realise that there is a lot of info on this but I am fairly new to ubuntu and I think I need specific help.

I had to re-install win xp on a partitioned with ubuntu and xp. If I set my primary boot device in my bios to the drive with ubuntu and xp I get an an error 17.

I downloaded a program "auto super grub disk" that lets me access the grub menu, but this works only if I boot with my other drive set as default, so I am able to access ubuntu,

I have tried this:

grub> find /boot/grub/stage1

for this command I get an error 15 saying file not found even though it is actually there.

If I try and guess with the routing

grub> root (hd0,0)

grub> setup (hd0)

I get an error 17 saying it cannot mount the selected partition

Im not sure what I messed up but it is a bit frustrating having to boot from my slave drive so that I can access ubuntu.

Any help would be greatly appreciated and thanks in advance

---

### Post by meierfra. on 2009-01-10
Did you use "sudo" to  run grub?

```
sudo grub
find /boot/grub/stage1 
```

This will return (hdX,Y), where X and Y are some numbers. Use these numbers below:

```

root (hdX,Y)
setup (hdX)
quit
```

If this does not help, download the [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/") to your desktop. Then run the script with


```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create the file "RESULTS.txt" on your desktop. Post the content of the file (place it inside the CODE tags by clicking on the # symbol)

---

