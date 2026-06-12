---
title: "Ubuntu system shuts off randomly after booting"
date: 2009-02-05
forum: General Help
---

### Post by dxplosiv1 on 2009-02-05
This may be more of a hardware issue than anything but I still need a little insight.

For the past couple of weeks, when I start Ubuntu, it will work fine for about 30 to 45 minutes and then suddenly shut off. To get it back on, I have to flip off the switch on the power supply off so that the led lights on my pc go out, and then flip it back on and reboot the computer.

I'd had this issue a couple of years back and found that my computer was overheating. I checked bios and my cpu temp usually reads between 37 and 42 degrees Celsius. I don't think it's over heating. My pc once read 85 Celsius and managed to stay on fairly long before I fixed that.

 Also, I dual boot with Windows and rarely use it. So I booted into Windows and let it run all day while at work and come home and it's still on. Bottom line, I thought it was hardware related but Windows is able to run all day and Ubuntu only for about 45 at a time. With this, I'm thinking it's software related somehow but don't know where to start. Any ideas?

---

### Post by dcstar on 2009-02-05
> **dxplosiv1 said:**
> This may be more of a hardware issue than anything but I still need a little insight.

For the past couple of weeks, when I start Ubuntu, it will work fine for about 30 to 45 minutes and then suddenly shut off. To get it back on, I have to flip off the switch on the power supply off so that the led lights on my pc go out, and then flip it back on and reboot the computer.

I'd had this issue a couple of years back and found that my computer was overheating. I checked bios and my cpu temp usually reads between 37 and 42 degrees Celsius. I don't think it's over heating. My pc once read 85 Celsius and managed to stay on fairly long before I fixed that.

 Also, I dual boot with Windows and rarely use it. So I booted into Windows and let it run all day while at work and come home and it's still on. Bottom line, I thought it was hardware related but Windows is able to run all day and Ubuntu only for about 45 at a time. With this, I'm thinking it's software related somehow but don't know where to start. Any ideas?

Make sure the Ubuntu CPU clock speed management is actually working.

Also see if it is after "x" minutes of idle as it may be going into suspend and that may be the problem.

---

### Post by cmnorton on 2009-02-05
First, look at your logs right after you reboot.

sudo tail /var/log/syslog
sudo tail /var/log/messages

dmesg | less

Look for something tell-tail. You don't need to post the output here.

Will the system stay up with a live CD like Ubuntu or recovery CD like Knoppix?

---

### Post by dxplosiv1 on 2009-02-05
> **dcstar said:**
> Make sure the Ubuntu CPU clock speed management is actually working.

Also see if it is after "x" minutes of idle as it may be going into suspend and that may be the problem.
I'll try to take a look at the CPU clock speed management when I get in the house. I checked for the 'x' minutes option as well, but my pc is turning off. Everything shuts off except for the green led power light on my case....

---

### Post by dxplosiv1 on 2009-02-05
> **cmnorton said:**
> First, look at your logs right after you reboot.

sudo tail /var/log/syslog
sudo tail /var/log/messages

dmesg | less

Look for something tell-tail. You don't need to post the output here.

Will the system stay up with a live CD like Ubuntu or recovery CD like Knoppix?
I can give the live cd a try and see if that keeps my computer up and running

---

### Post by cmnorton on 2009-02-06
A lot of debugging is looking for non-causes. Booting from a live or rescue CD says something about your motherboard and memory.

Once booted, you can try mounting the hard-drive and see if that causes you to shutdown. Although disk problems should be in the logs.

---

### Post by dxplosiv1 on 2009-02-07
> **cmnorton said:**
> A lot of debugging is looking for non-causes. Booting from a live or rescue CD says something about your motherboard and memory.

Once booted, you can try mounting the hard-drive and see if that causes you to shutdown. Although disk problems should be in the logs.
So far, all I've done is turn off my screensaver, and ran the latest updates from Synaptic since my internet was down for the past 5 days. I left it on over night and it's still running now. I'll keep you up to date....Thanks for the help though

---

