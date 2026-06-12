---
title: "Quickie - text editor in safe terminal mode"
date: 2005-03-15
forum: Desktop Environments
---

### Post by marcadams on 2005-03-15
Hi just a quick question for those people familiar with Linux...

I've got a problem with my Nvidia configuration locking my PC on Boot.
During boot I can press ESC and get to the safe terminal mode.

I need to edit a config file - what commandline application can I do this with ?


Many thanks
Marc

---

### Post by LongTooth on 2005-03-15
I've tried to use several editors. Most just don't do for me. But for my money - and maybe is because I don't do any heavy duty programing and such - Gedit is the one to use. Just key in 'sudo gedit /etc/ whatever'. It's a GUI editor that can do whatever you want.

---

### Post by ember on 2005-03-15
Try vi. Important commands:

i : switch to insert mode
del : delete a single character in insert mode
esc: leave insert mode 

:wq (when not in insert mode): write file and quit

---

### Post by marcadams on 2005-03-15
hi LongTooth;

Unfortunately I don't think Gedit will work as I will be in an entirely text based environment (Safe terminal mode from boot).

Cheers
Marc

---

### Post by fdoving on 2005-03-15
[QUOTE=marcadams]hi LongTooth;

Unfortunately I don't think Gedit will work as I will be in an entirely text based environment (Safe terminal mode from boot).

Cheers
Marc[/QUOTE]
 try nano if it's installed.

---

### Post by iomicifikko on 2005-03-15
[QUOTE=fdoving]try nano if it's installed.[/QUOTE]
 nano for sure, really simple.

another one really simple is "joe" but nano should be installed as default

byez

---

### Post by mike998 on 2005-03-15
I believe pico is also available which if I remember rightly actually has the commands available and their shortcuts at the bottom of the terminal.
I personally prefer vi, it takes some getting used to, but I like it.

It's always a good idea to have an idea on how to use editors like vi, pico, nano etc.  You will find that you have an advantage over yourself in situations like this where you don't have an X session to work with.  I used to have to hand configure a lot of files when getting FreeBSD running, and got used to using vi from this.

---

### Post by marcadams on 2005-03-15
Thanks for your help everyone!

In the end I used nano - the only mistake I initially made was saving the file in Mac mode ..douh!

But as soon as I got that sorted, I made my change and I finally have my system back

Yipeee  [-o< 

Thanks again for everyone's help,
Marc

---

