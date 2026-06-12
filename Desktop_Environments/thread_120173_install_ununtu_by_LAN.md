---
title: "install ununtu by LAN"
date: 2006-01-20
forum: Desktop Environments
---

### Post by svitj on 2006-01-20
I'm trying to install Ubuntu in an acer 4150, but he said that he cant't see CD drive... :( 
So I would like to install Ubuntu by LAN, how can i do that?

thanks!

---

### Post by greenway on 2006-01-21
[QUOTE=svitj]I'm trying to install Ubuntu in an acer 4150, but he said that he cant't see CD drive... :( 
So I would like to install Ubuntu by LAN, how can i do that?

thanks![/QUOTE]

Hey there, 

I did it once with my boss' Toshiba Protege using the howto on wiki (look out for netboot). I don't remember the exact details but I do remember it wasn't all that difficult, you have to have a DHCP server running and the wiki pages will tell you how to configure it to give out a special lease for your Acer. For the Protege I was able to boot it from the network by selecting this option in the BIOS, however I am not sure if you're Acer has this option, look for it in the BIOS. If not, you will have to create a netboot disk. Pretty sure this is also explained in the wiki...

Hope this will get you on your way!

-mattijs

---

### Post by svitj on 2006-01-26
Ok! Thanks!

I will try, and then I say something!

---

### Post by ozorba on 2006-06-20
[QUOTE=greenway] 
I did it once with my boss' Toshiba Protege using the howto on wiki (look out for netboot). I don't remember the exact details but I do remember it wasn't all that difficult, you have to have a DHCP server running and the wiki pages will tell you how to configure it to give out a special lease for your Acer. For the Protege I was able to boot it from the network by selecting this option in the BIOS, however I am not sure if you're Acer has this option, look for it in the BIOS. If not, you will have to create a netboot disk. Pretty sure this is also explained in the wiki...
[/QUOTE]

I have tried to install it using the instructions from here:

[http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)

However, it appears that the kernel cannot find the network card and it hangs up.

Has anyone suceeded to install Ubuntu onto a Toshiba Protege 3480CT?

Thanks,
OZ

---

### Post by Craigus on 2006-09-20
Yes - I used this guide:

[https://help.ubuntu.com/community/Installation/WindowsServerNetboot](https://help.ubuntu.com/community/Installation/WindowsServerNetboot)

I have installed on both a 3490 and a 3480 using this method.

---

