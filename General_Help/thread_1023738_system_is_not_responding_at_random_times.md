---
title: "system is not responding at random times"
date: 2008-12-28
forum: General Help
---

### Post by chriskin on 2008-12-28
since the day before yesterday i am experiencing this : while in ubuntu my system stops responding at random times (the cursor turns to the icon it has for when we have to wait for something to finish, the screen turns gray and nothing moves)

at first it started happening only when i moved my mouse to another usb gate, yesterday it started happening every time i made a change (for example, unplugging the ac power and leaving the laptop running on battery) and today it happens at random moments, even when i do nothing at all with the computer :S

what should i do to make it stop?

---

### Post by atoponce on 2008-12-28
So, it sounds like Ubuntu is running on a laptop? What hardware? It is possible that some hardware could be failing, and causing the kernel to panic, which would give a total hard lock like you're experiencing. Is there anything in /var/log/messages or /var/log/dmesg that's worth noting?

---

### Post by chriskin on 2008-12-28
it is a fujitsu siemens amilo xi 2428, 2gb ram, 2.2gh dual core
can you tell me how to check those you just mentioned?

---

### Post by atoponce on 2008-12-28
Those log files are just text files. You can use any text editor to open them:

```
cat /var/log/messages
```
```
less /var/log/messages
```
```
vim /var/log/messages
```
```
gedit /var/log/messages
```

Same goes with /var/log/dmesg.

---

### Post by chriskin on 2008-12-28
in messages, there are many lines like these :
Dec 28 16:56:29 CNB kernel: [52574.602610] nautilus[1322]: segfault at 1 ip 00000001 sp bfa18d8c error 4 in nautilus[8048000+140000]
Dec 28 16:56:44 CNB kernel: [52589.552600] nautilus[6705]: segfault at 21 ip 00000021 sp bf8853fc error 4 in nautilus[8048000+140000]
Dec 28 16:57:39 CNB kernel: [52644.810692] nautilus[6896]: segfault at 1 ip 00000001 sp bff3dabc error 4 in nautilus[8048000+140000]
Dec 28 16:58:00 CNB kernel: [52666.358166] nautilus[7673]: segfault at 21 ip 00000021 sp bfe359ac error 4 in nautilus[8048000+140000]

in the other one ( /var/log/dmesg) there is a whole mess of things, i do not know what i should look for :S

---

### Post by redilyn on 2008-12-30
Chriskin Wrote:
"i will keep this in mind, yet by doing so i will lose many other options wont's i?
like the plugins for firefox, the compiz effects etc?
or not?"

Nope. Actually you might lose your firefox plugins but they should be easy to restore.

As for your compiz effects and other program settings. For the most part they are stored in your home folder. Press CTRL+H to see the hidden program folders.

After you reinstall ubuntu, install your programs. Your program settings will be just as they were before the reinstall

Before you reinstall ubuntu though you might want to check a few things.

1) Boot your computer and select memtest from the grub menu. Let this run overnight to check for errors

2) If memtest passes. Download and run Prime95, select stress test, and let that run over night to check for errors.

---

### Post by chriskin on 2008-12-30
i will most possibly do that then
it will take less than a day and it will fix everything
thanks :)

---

### Post by redilyn on 2008-12-30
No problem.

You should realize I suggested this before I found out you had a duplicate thread. about getting kernel panics. 

If you do not have a empty parition or hard drive where you can move your home folder to I would wait.

Without a spare parition or hard drive you are going to have to do a resize of your system partition and then create a new partition for /home before you can move your files, if you get a kernel panic during the resize.....well...its all over, your partition and files are gone.

Good Luck :)

---

### Post by chriskin on 2008-12-30
yes i know
hope for the best then :)

---

