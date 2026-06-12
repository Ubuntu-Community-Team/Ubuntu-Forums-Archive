---
title: "Startup problems 14.04 LTS"
date: 2015-10-09
forum: Desktop Environments
---

### Post by pecoflyer on 2015-10-09
Hello

6 times out of 10 Xubuntu starts normally
3 times out of 10 after the Grub screen the screen turns black and nothing happens
           however : if I hit Ctrl+Alt+F1 an invite prompt appears ( no text)
                         after that, if I hit Ctrl+Alt+F7 screen becomes black again
If I then do a reset a get "ACPI PCC probe failed", 
              in this case, sometimes Xubuntu starts normally
                               sometimes nothing happens at all ( black screen)

1 time out of 0 I get a screen beginning with Busybox 1.21.1 and an invite prompt after initrmfs ( or something like that)

Can anybody help me out please?

Does this help?

```
pecoflyer@PC-DAD-UP:~$ lspci | grep "VGA compatible controller"
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Turks XT [Radeon HD 6670/7670]


```

Thank you

---

### Post by egeezer on 2015-10-09
When you use Ctrl+Alt+F1, try startx after the prompt, and if that gives you a Command Not Found, try startxfwm4.

---

### Post by pecoflyer on 2015-10-09
Now that you mention it , sometimes, when xubuntu has started, the windows do not always have a header although the xfwm4 --replace is executed at startup

---

### Post by pecoflyer on 2015-10-10
bump

---

### Post by pecoflyer on 2015-10-11
Bump2

---

### Post by pecoflyer on 2015-10-12
I thought the much vaunted Ubuntu community would help, but it seems my problem is either too complicated, or not worth even an acknowledgement.

---

### Post by wandalalakers on 2015-10-26
> **pecoflyer said:**
> I thought the much vaunted Ubuntu community would help, but it seems my problem is either too complicated, or not worth even an acknowledgement.

Try:
[https://forum.xfce.org/viewforum.php?id=4](https://forum.xfce.org/viewforum.php?id=4)

---

