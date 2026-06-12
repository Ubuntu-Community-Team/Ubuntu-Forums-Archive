---
title: "How to autolaunch modprob on startup - related to Xbox controller drv"
date: 2019-04-09
forum: Gaming &amp; Leisure
---

### Post by homemdacaverna on 2019-04-09
Hi, in order for xpad to recognize the xbox 360 wireless controller I have to launch the “modprobe -r xpad / modprobe xpad” commands everytime I start the computer. 

Is there a way to automate this task on start up?

---

### Post by oldrocker99 on 2019-04-10
It may work in your startup programs if you add it just as you typed it, without the quotation marks.

---

### Post by homemdacaverna on 2019-04-11
Can you please instruct me on this? I am new to Ubuntu.

I searched how to do it but what made didn't work.

---

### Post by oldrocker99 on 2019-04-12
There should be a Startup Programs app in your Preferences menu. Click on "Add," and enter the command. You should log out and log back in so it'll start.

---

### Post by homemdacaverna on 2019-04-14
It didn't work.
I tried entering the commands as two different applications too, but that didn't work neither.

I believe the Startup Programs does not work for 'sudo' commands since I have enter my password.

Any other ideas?

---

### Post by oldrocker99 on 2019-04-14
Here is a somewhat complicated installation instructions using WINE to run it:

[https://www.unixblogger.com/how-to-get-your-xbox-360-wireless-controller-working-under-your-linux-box/](https://www.unixblogger.com/how-to-get-your-xbox-360-wireless-controller-working-under-your-linux-box/)

And here are detailed compilation from source code for a driver:

[https://github.com/atar-axis/xpadneo](https://github.com/atar-axis/xpadneo)

Don't be afraid of compiling source code. Just follow the instructions.

I hope this helps.

---

