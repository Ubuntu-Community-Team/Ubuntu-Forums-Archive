---
title: "my laptop machine freeze"
date: 2006-09-03
forum: Desktop Environments
---

### Post by BasiX on 2006-09-03
Hello. I am using Ubuntu 6.06.1 Dapper Drake. I got some problems. Sometime the whole computer freezing. I can´t quiting gnome or nothing. I have used my laptop machine at Windows XP but when I installed ubuntu the computer apperared wierd. I have reinstalled ubuntu two times but the computer continue to freeze. The only appz I have installed are VLC, XMMS, Apache2, php5, wlassitant, aMSN, xchat, no-ip etc. I have not installed ATI graphic drivers becuase I get errors when I installed that. The wierd thing is that I could listen to music maybe 12 hours. But when I start xchat or firefox the machine freeze. This is very wierd. Any suggestion?

// BasiX

---

### Post by ispmarin on 2006-09-03
Can you give more details about it? What is the hardware of the laptop? Did you try to start firefox or other applications on a terminal and look for error messages? Can you post a dmesg and a lspci, and also the error that the driver gave you?

---

### Post by bulldog on 2006-09-03
Is your problem internet related?

Do you have a working ethernet card?
Is it configured the right way?

Because when you contact the internet it's going wrong.

I should look in that direction if I where you.

---

### Post by BasiX on 2006-09-03
#isparin

[HTML]http://www.pappaline.com/myggan/pastebin/1440977646.txt[/HTML]

I did also do a check on wlassistant, check there (the url above) I got some errors there.

When I installed the ATI driver I get a wrong in the xorg.conf. I had a backup so I use that instead. 

#bulldog

I think the problem is Internet related. Yes my wireless card working. But maybe not right. I don´t know. I don´t know if I have configured the right way. Maybe not. How would I do to confiugred that right then? Yah. When I have internet connection the computer freeze.

// BasiX

---

### Post by ispmarin on 2006-09-03
I think that you problem is not the internet, but the ACPI. Your ACPI seems to not load correctly. Try to disable the ACPI on boot and sees if it works.

---

### Post by BasiX on 2006-09-03
hmm. how do I disable ACPI then? :)

// BasiX

---

### Post by BasiX on 2006-09-03
Ok. I have disable ACPI now and it freeze now again :(. I can´t understand why my laptop like to freeze :). hm :/. 

[HTML]http://www.pappaline.com/myggan/pastebin/1440977646.txt
[/HTML]

---

### Post by ispmarin on 2006-09-03
You can follow the instructions on this post:
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

