---
title: "nullmailer-send use so much CPU"
date: 2008-12-31
forum: General Help
---

### Post by NawaMan on 2008-12-31
I realizes that every few minutes my CPU and disc access go up the roof and stay there for about 20 seconds. After some investigations, found that the programs that do this is nullmailer-send. So I killed it and the problem completely disappear.

My questions are Can I permanently remove it? How? Will it effect my other use? The only think I can think of is that come of the crontab job may use it (but after observing for a while, it does not seems to launch nullmailer-send and there seems to be no other problems).

It does not seems to be problem on other of my computers (also my girlfriend's).

My computer Sony VAIO VGN-C140G
DUO Core T5500 @1.66GHz
Memory 2.0GB
Ubuntu 8.10
Kernel 2.6.27-9-generic
GNOME 2.24.1

I have Apache 2, MySQL, OpenSSH running as server.
I use GDesklets.
I have System Monitor applet and Weather monitor (that comes with the Gnome panel Calendar).
I have crontab schedule for automatic backup jobs but non of them directly use nullmailer-send. All of the task has '>/dev/null 2>&1' to produce to emails (which I am not sure it use nullmailer-send or not but after kill nullmailer-send there seems to be no effect to those tasks and nullmailer-send does not get reloaded).

Thanks in advance
NawaMan

---

### Post by dcstar on 2008-12-31
> **NawaMan said:**
> I realizes that every few minutes my CPU and disc access go up the roof and stay there for about 20 seconds. After some investigations, found that the programs that do this is nullmailer-send. So I killed it and the problem completely disappear.

My questions are Can I permanently remove it? How? Will it effect my other use? The only think I can think of is that come of the crontab job may use it (but after observing for a while, it does not seems to launch nullmailer-send and there seems to be no other problems).
..........
I have crontab schedule for automatic backup jobs but non of them directly use nullmailer-send. All of the task has '>/dev/null 2>&1' to produce to emails (which I am not sure it use nullmailer-send or not but after kill nullmailer-send there seems to be no effect to those tasks and nullmailer-send does not get reloaded).


Various things run in Cron will send mail if they need to, and if you do not have a MTA installed then it may well cause problems.

Install the **postfix** and **mailx** packages and see if that makes a difference.

---

### Post by NawaMan on 2009-01-01
Thank you very much for the reply. I have installed postfix and will observe for a few days if any problem will arise. During the installation, I found that nullemailer-send is automatically removed so I think at lease it should solve my performance problem.

I am curious that even if I use ' > /dev/null > &1' there still be email being sent? Is that clause supposed to eliminate that? What should those email suppose to contain. I don't know if any email have been sent because I don't know how check those email.

Thanks again,
NawaMan

---

