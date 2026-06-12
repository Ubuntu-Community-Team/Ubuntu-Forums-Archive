---
title: "My Screen went blank when I changed users"
date: 2012-05-08
forum: Desktop Environments
---

### Post by ABCraine on 2012-05-08
I have a new computer and installed Ubuntu 11.10.

This has been working for a few weeks now.

Today, I logged in as user A, switched users to B, then logged B out.
The screen I got next was the log in screen, so I logged back into A.

Now my screen is blank with a blinking cursor in the upper left corner.
An internet search reveals this question coming up for the past 4or5
years, but I couldn't find any answers.

Please help.

---

### Post by sudodus on 2012-05-08
It is a good idea to make a controlled or soft reboot. Avoid brutal power off, because that can create problems with disk errors!

One way might be to start a text terminal pressing three keys at the same time:

***ctrl + alt + F3***

(you can often use F1 ... F6)

and log in using your normal user and password. Then you can run the command

```
sudo reboot
```

and enter the password (again). If this does not work you can do the following:

Press the two keys ***alt + SysRq*** (often on the same key as PrintScreen) and without releasing alt + SysRq press slowly ***r e i s u b*** one each time in sequence.

Clarification: (alt + SysRq) {R E I S U B}

---

### Post by ABCraine on 2012-05-08
I was able to log in from an ssh shell on my Windows machine.
I didn't like the idea of powering off.

Why does this happen? How can I avoid it in the future?  I would like to set this machine up to collect data regularly from the web, and needing to reboot to switch users is not optimal.

Thanks

---

### Post by sudodus on 2012-05-09
> **ABCraine said:**
> I was able to log in from an ssh shell on my Windows machine.
I didn't like the idea of powering off.

Why does this happen? How can I avoid it in the future?  I would like to set this machine up to collect data regularly from the web, and needing to reboot to switch users is not optimal.

Thanks
I understand that you know what you are doing. It was a good idea to log in via ssh and solve the problem.

It should not happen, and I don't know why it does happen. Can you repeat it? I mean, will it happen every time you switch users and log back into the first user, or only sometimes? Or was it a singular event, maybe because of some recent update, that would have needed a reboot?

Do you remember if you had used some program, that used the graphics or filled the RAM and caused swapping?

---

### Post by ABCraine on 2012-05-09
I don't think it always goes blank when we change users.  I will definitely do some tests today to try and reproduce/parameterize this.

This brings up another, perhaps related issue:
User A will leave a bunch of stuff on the screen; e.g. multiple open browsers, terminals, etc, lock the screen and not return for several hours or maybe a day.  When user A logs back in, the screen behaves strangely.  It will be black, then as the mouse is moved around or clicked, parts of the top page will be seen (maybe a top bar, or a search window), several minutes later more and more of the window will show up until it is fine again.

As I type this, I'm also thinking that multiple Linux desktops might also be in use.  Again, I'll be doing some tests today.

Thanks

---

### Post by sudodus on 2012-05-09
> **ABCraine said:**
> I don't think it always goes blank when we change users.  I will definitely do some tests today to try and reproduce/parameterize this.

This brings up another, perhaps related issue:
User A will leave a bunch of stuff on the screen; e.g. multiple open browsers, terminals, etc, lock the screen and not return for several hours or maybe a day.  When user A logs back in, the screen behaves strangely.  It will be black, then as the mouse is moved around or clicked, parts of the top page will be seen (maybe a top bar, or a search window), [COLOR="Red"]several minutes later more and more of the window will show up until it is fine again.[/COLOR]

As I type this, I'm also thinking that multiple Linux desktops might also be in use.  Again, I'll be doing some tests today.

Thanks
This is a typical sign that the RAM was filled and some data was swapped. Restoring data from the swap partition is ***very slow*** compared to RAM. If you want this functionality, and your motherboard can manage it, you can increase the RAM. 

The alternative is discipline, to shut down applications, that are not necessary, when you (and the other users) leave the computer. Or to use a desktop environment with a smaller foot-print, XFCE of Xubuntu or LXDE (ultra-light) of Lubuntu.

If you post the specs of the computer, particularly cpu, ram and graphics card/chip it will be easier to suggest what to do.

---

### Post by dr_saaron on 2012-05-09
I've had this problem ever since upgrading to oneiric, with never a problem before that release.  I upgraded to precise this morning and found that everything will work fine for a while (I even posted in another thread that I had found some strange solution that didn't make sense) but then it just stop working and you get the blinking cursor again.  

One thing you can do when you have the blinking cursor is hit ALT-F7 or ALT-F8 which should get you to a login prompt for one of your users, I guess the first two to login so the :0 or :1 sessions.  Assuming you know the password for that account you can log in and then switch to the specific user you are looking for instead of going to Switch User Account "feature" which is an alias for blinking cursor.

---

### Post by ABCraine on 2012-05-09
> **sudodus said:**
> This is a typical sign that the RAM was filled and some data was swapped. Restoring data from the swap partition is ***very slow*** compared to RAM. If you want this functionality, and your motherboard can manage it, you can increase the RAM. 

The alternative is discipline, to shut down applications, that are not necessary, when you (and the other users) leave the computer. Or to use a desktop environment with a smaller foot-print, XFCE of Xubuntu or LXDE (ultra-light) of Lubuntu.

If you post the specs of the computer, particularly cpu, ram and graphics card/chip it will be easier to suggest what to do.

Here are the specs: 
CPU: AMD FX-8120 Zambezi 3.1 GHz (8 core)
RAM 16 GB
Graphics: Gigabyte </span>GV-N210D3-1GI NVIDIA GeForce 210 1024MB DDR3 PCIe 2.0 x16 
Mobo: Asus Sabertooth 990FX

Appreciate your help.
 </span>

---

