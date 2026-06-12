---
title: "can i have 2 operating systems on one computer"
date: 2009-01-27
forum: General Help
---

### Post by zanic07 on 2009-01-27
hello everyone 

im new to ubuntu and linux and i was wondering if there was any way to make it so my computer gives me a choice on weather to load ubuntu or windows 

i have vista on the original hard drive and ubuntu on another hard drive that i just got. I have been able to switch between the 2 so far by unscrewing the side of my case and manually switching the 2 drives but thats a pain 

so is there any way to have both of my drives connected but choose what operating system to load on start up

---

### Post by munch3 on 2009-01-27
Omg ofcourse there is ^__^

in Linux:
run Terminal
type
```
sudo gedit /boot/grub/menu.lst
```

now this list was supposed to come installed with ubuntu, so i guess maybe the timeout time is set to 0, so find Timeout=*
and check which value is set there.

In Windows (vista):
Start > type msconfig and hit enter.
click the boot.ini tab and work from there....
first Check All Boot Paths, then set the Timeout you want,
etc.

please reply with your proggress i can try and help youfurther

---

### Post by jeffjanzen on 2009-01-27
EDIT: i was too late and munch3 already answered your question more thoroughly than i could.

---

### Post by SlowCheetah on 2009-01-27
That's no problem at all, i used 'Wubi' for that.

Info over here;
[http://blogs.zdnet.com/hardware/?p=1570&tag=nl.e622](http://blogs.zdnet.com/hardware/?p=1570&tag=nl.e622)

---

### Post by zanic07 on 2009-01-27
thanks a ton guys you this makes things a lot easier

---

### Post by estyles on 2009-01-27
msconfig?  huh?

If you can't get to linux because Windows is the default boot option, then boot from a LiveCD.  You will need to edit your /boot/grub/menu.lst file, and you will need to install grub to the MBR.

If you are unable to search and find how to do that, then I can help, but you'll need to boot from the LiveCD, open a terminal, and do "sudo fdisk -l" and "cat /boot/grub/menu.lst".  Post the output of both commands here.

---

### Post by zanic07 on 2009-01-27
thanks i just figured it out i had to adjust the time for how long the window would be open to change the boot areah im not sure what its called i have to hut F10 to enter the boot section but thanks a ton 

like i said though im compleetly new to linux i just downloaded it on sunday 25th and havent been able to play around with it at all till today

but thanks again and have a great day

---

### Post by munch3 on 2009-01-28
yay i helped ^^

---

