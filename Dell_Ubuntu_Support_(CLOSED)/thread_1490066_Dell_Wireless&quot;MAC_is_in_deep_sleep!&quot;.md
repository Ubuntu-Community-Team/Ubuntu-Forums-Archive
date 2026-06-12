---
title: "Dell Wireless/&quot;MAC is in deep sleep!&quot;"
date: 2010-05-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by king mint on 2010-05-21
I am an unfortunate owner of one of the Dell XPS 1530 models that has serious wireless problems in Ubuntu. I have used every version since 8.04 and am now on 10.04, and with every version the wireless works 1 in every 4 or 5 times I turn on or restart my computer. What is so strange is that it is so erratic - mostly it doesn't work but sometimes it does.

For the first time in 10.04 there is (to my linux illiterate eye) an indication of what is going wrong: when Ubuntu starts to load an error message starts to repeat down the screen, reading: 

iwl3945 0000:0b:00.0: MAC is in deep sleep!

I have seen threads about this problem for the last couple of years - any google search for Dell/Ubuntu/iwl3945/wireless or the error message shows a large number of threads indicating that many users have this problem. However I cannot find a single thread in which anyone claims to have fixed it. Please tell me that someone here has solved this problem! My Ubuntu experience has so far been miserable because of this single issue!

Many thanks,

Eric

---

### Post by fantaxy on 2010-05-23
I'm having the same problem. Whenever I switch my laptop on, I've to wait for at least 90 seconds of the annoying message. :-x

---

### Post by king mint on 2010-05-24
Does your wireless card work after the message has finished? Mine does not so I have to keep restarting my computer (4-5 times) until the message does not come up and the wireless finally works.

Has nobody fixed this problem?!

---

### Post by Kirkland14 on 2010-05-25
Have you tried to make sure the right drivers are installed.  My 1545 wouldn't work at all until I hard wired into my router and went to System>Admin>Hardware drivers and got the current driver.  Don't know if this will help any as I am pretty new to Linux.  Good Luck

---

### Post by LK_gandalf_ on 2010-06-11
I have the same problem on the boot, I get 20-30 seconds of that message repeated, then it freeze and I have to manually reboot. The second time goes well. Wireless card works well, I just have that issue.

---

### Post by CamT on 2010-06-11
I've been dealing with this issue for the couple of years I've had my Dell XPS M1530 with an Intel 3945 wireless card.  On most distributions, the card only works randomly after rebooting several times.  When it doesn't work, it outputs the MAC in deep sleep message.

The only success I have had is using Fedora.  My card always worked flawlessly on that distro.  However, I've had to switch back to Ubuntu for some other reasons.

I've tried all sorts of fixes, but nothing has seemed to work.  Maybe someone who knows a bit more than me can look into the differences between these two distros to find a possible solution.

---

### Post by LK_gandalf_ on 2010-06-12
Yes it's quite serious that this issue remains unsolved, even because this laptop is quite popular and especially among (k)ubuntu users.

---

