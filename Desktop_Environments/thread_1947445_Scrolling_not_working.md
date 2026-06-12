---
title: "Scrolling not working"
date: 2012-03-26
forum: Desktop Environments
---

### Post by satanicat on 2012-03-26
Hello.

the scroll in my netbook works bad, it jumps up or down, so is not very trustful, so i have to use the arrow keys.

I thought it was a problem with the trackpad but yesterday i connected a mouse and scrolling with the mousewheel was giving me the same issue.

so anyone knows what could i do?



cheers.

---

### Post by satanicat on 2012-03-26
anyone?

---

### Post by Rodney9 on 2012-03-27
You could try installing synaptiks, it is available in the Software Centre

synaptiks touchpad configuration tool. this package contains a configuration  tool for touchpads. The package provides a kcm module (for systemsettings), as well  as a plasma widget and kded module to help managing touchpads, especially in KDE environments.




For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by satanicat on 2012-03-28
But im afraid is not a trackpad problem, the mousewheel has the same issue.

Im under Lubuntu 11.10

salut

---

### Post by Toz on 2012-03-28
What happens if you:
```
sudo rmmod psmouse
```
...then
```
sudo insmod psmouse
```

---

### Post by satanicat on 2012-03-28
It disabled the trackpad. 
insmod did nothing.
i rebooted and everything is like before.

---

### Post by Toz on 2012-03-28
Try this instead:
```
sudo modprobe -r psmouse
sudo modprobe psmouse
```

If that still doesn't work, try adding **i8042.nomux** to your kernel boot line.

---

### Post by satanicat on 2012-04-09
> try adding i8042.nomux to your kernel boot line.

Thats the last hope i think, i still cant solve it. but i dont know how to edit the kernel boot line.

Do you think that will work? because the scrolling **works**, but bad, the scrollbar goes to the top of the page very quick while scrolling, every time.

any ideas?

PS: now this is my only issue, lubuntu rules!

---

### Post by Toz on 2012-04-09
It may be a problem with an inconsistent IRQ signal. That kernel parameter may solve the issue for you. You can test it temporarily by following the instructions [here]("https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot"). 

If it works, we can make the parameter permanent. If it doesn't, simply reboot your computer to get it back to this state.

---

