---
title: "Ubuntu 20.04 freezes and does not allow any activity"
date: 2021-04-01
forum: Desktop Environments
---

### Post by Ashwin_D on 2021-04-01
I have been running Ubuntu 20.04 since Aug 2020 without any issues. Since the past 2 - 3 days I am encountering system freezes randomly without warning. The entire system freezes including the mouse keyboard and I am forced to a a  hard reboot by switching off the power and restarting. At first I thought it had to do with Qt5 and I removed that software. Now it froze when I used google-earth-pro. So I am thinking this could be a graphics card issue.  How can I identify my problem ? 

These are my system details  - Linux winash12-OptiPlex-7050 5.8.0-48-generic #54~20.04.1-Ubuntu SMP Sat Mar 20 13:40:25 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux and this is my graphics card

00:02.0 VGA compatible controller: Intel Corporation HD Graphics 630 (rev 04)

Best regards,
Ashwin.

---

### Post by ActionParsnip on 2021-04-01
Test your RAM health using Memtest86 as a good start

---

### Post by Ashwin_D on 2021-04-01
Thank you for your response. So I did run a complete system diagnostics using Dell. So you want me to run the memtest86 as additional tests ?

---

### Post by Ashwin_D on 2021-04-01
[https://linuxhint.com/run_memtest_ubuntu/](https://linuxhint.com/run_memtest_ubuntu/) I installed memtester and I ran a test using 100M and one iteration and no errors were reported. I shall run the memtest86 and get back.

---

### Post by daniewicz on 2021-04-02
Maybe a bad power supply?

---

### Post by Ashwin_D on 2021-04-03
> **daniewicz said:**
> Maybe a bad power supply?
How can I verify this ?

---

### Post by ActionParsnip on 2021-04-03
Open case and swap with a known good PSU. Also make sure that you have the latest BIOS.

---

### Post by Autodave on 2021-04-03
If you have more thanone RAM chip in there, try removing all but one of them (make sure it is in the #1 slot) and see what happens.  Test each of them individually by using the machine as you normally would.  If it fails on only one of them, then that one is your culprit.  If it fails on another one, then you are probably looking at a power supply.  As ActionParsnip already said, the best way is to swap the power supply if you have another available.

---

