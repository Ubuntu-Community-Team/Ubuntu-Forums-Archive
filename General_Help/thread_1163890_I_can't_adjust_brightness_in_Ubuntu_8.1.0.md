---
title: "I can't adjust brightness in Ubuntu 8.1.0"
date: 2009-05-19
forum: General Help
---

### Post by moth_rain on 2009-05-19
when I install Ubuntu 9.04 I can adjust brightness by fn+brightness

now I want to downgrade to Ubuntu8.10 so I format harddisk and install

Ubuntu8.10 then I can't adjust brightness 

so How can I adjust brightness in Ubuntu8.10?

thank you very much
  

ps.I use notebook thinkpadx61 with Graphic card Intel GM965
and sorry for my poor english;)

---

### Post by bubba_169 on 2009-05-19
Neither could I while X was running. I found a workaround which was to press ctrl+alt+F1 to switch to a virtual console, adjust your brightness here and then press ctrl+alt+f7 to get back to your graphical desktop.

Hope this helps?

---

### Post by moth_rain on 2009-05-19
> **bubba_169 said:**
> Neither could I while X was running. I found a workaround which was to press ctrl+alt+F1 to switch to a virtual console, adjust your brightness here and then press ctrl+alt+f7 to get back to your graphical desktop.

Hope this helps?

I press ctrl+alt+F1 and I adjust brightness by press fn+brightness and press  ctrl+alt+f7
alredy but brightness not change

---

### Post by Egi_Power on 2009-05-19
> **moth_rain said:**
> when I install Ubuntu 9.04 I can adjust brightness by fn+brightness

now I want to downgrade to Ubuntu**8.1.0** so I format harddisk and install

Ubuntu**8.1.0** then I can't adjust brightness 

so How can I adjust brightness in Ubuntu**8.1.0**?

thank you very much
  

ps.I use notebook thinkpadx61 with Graphic card Intel GM965
and sorry for my poor english;)
There is no Ubuntu 8.1.0.
It is Ubuntu ***8.10***. (because it was released in October 2008.)
9.04 was released in April 2009, and so on...

Best regards,

Egi_Power

---

### Post by moth_rain on 2009-05-19
ok. I'm sorry :p

---

### Post by Egi_Power on 2009-05-19
> **moth_rain said:**
> ok. I'm sorry :p
No problem!
;)
Take it easy.

[I]EDIT:
It could be a bug:
[https://lists.ubuntu.com/archives/kernel-bugs/2009-February/048082.html]("https://lists.ubuntu.com/archives/kernel-bugs/2009-February/048082.html")
END OF EDIT[/I]

Best regards,

Egi_Power

---

### Post by moth_rain on 2009-05-19
thank you very much

now I can adjust brightness already by

[http://ubuntuforums.org/archive/index.php/t-367339.html](http://ubuntuforums.org/archive/index.php/t-367339.html)

in rep.2 nachotronics 

"I had the same problem, the best solution i found was blacklisting the "video" module, this can be done by typing the following into terminal:
 [COLOR=Magenta]echo 'blacklist video' | sudo tee -a /etc/modprobe.d/blacklist[/COLOR]
This will prevent the "video" module from getting loaded on system startup, so you need to reboot for the changes to make effect.

I tried searching what that module was intended for, but couldn't find much information, i only know it has something to do with video and acpi. I have done this almost a month ago, and i haven't had any problems or noticed any other changes besides the ability for adjusting brightness.

Hope this helps."

---

