---
title: "system unresponsive"
date: 2006-01-09
forum: General Help
---

### Post by kasemodz on 2006-01-09
Alright I was installing ndiswrapper and added it to hte modules list. Turns out that ndiswrapper didn't work properly, so on bootup its hanging at Loading modules. How can I bypass this so I can edit the file and remove it from the modules file.

---

### Post by kasemodz on 2006-01-10
anyone? I just need to remove ndiswrapper from the modules file.

---

### Post by healychan on 2006-01-10
boot and run the system in safe mode.

edit the /etc/modules file and remove the word "ndiswrapper"

or type "sudo ndiswrapper -m ABC" where ABC is the name of your driver.

you can find the driver name in by "ls /etc/ndiswrapper" command.

---

### Post by healychan on 2006-01-10
[QUOTE=healychan]boot and run the system in recovery mode.

edit the /etc/modules file and remove the word "ndiswrapper"

or type "sudo ndiswrapper -m ABC" where ABC is the name of your driver.

you can find the driver name in by "ls /etc/ndiswrapper" command.[/QUOTE]

Notice that running in recovery mode will not provide any GUI frontend, even text editor. You will need to use "vi" editor. Open the file by this 
```
vi /etc/modules
```

---

### Post by Pyerwoh on 2006-01-10
I made the exact same mistake !  Now I am trying to boot in 'safe mode', and not sure exactly how to do that. Is it the same as Recovery Mode? I am booting into that, and I still get the same problem with the system hanging when it tries to deregister the ndiswrapper driver.  Can anyone point me in the right direction?

Thanks,
Peter

---

### Post by healychan on 2006-01-10
[QUOTE=Pyerwoh]I made the exact same mistake !  Now I am trying to boot in 'safe mode', and not sure exactly how to do that. Is it the same as Recovery Mode? I am booting into that, and I still get the same problem with the system hanging when it tries to deregister the ndiswrapper driver.  Can anyone point me in the right direction?

Thanks,
Peter[/QUOTE]
Try to press Ctrl + c when "loading modules". It may skip that step and continue the start up process. Than you can restore your setting.

---

