---
title: "Total Memory (=RAM and SWAP) overflow"
date: 2009-01-17
forum: General Help
---

### Post by b4b4_j4g4 on 2009-01-17
I was wondering if somebody could give me a hint about the reason for the memory overflow that occured for the 1st time on my computer.

Running few usual applications - skype, evince, nautilus.
A wlan connection, a vpn connection and one open ssh forward with nautilus. No programming, or any kind of weather simulation going on :)

I left the computer for a few minutes to find it completely overloaded and unresponsive. 
The system monitor was showing a full RAM, full swap, and the hard disk was continuously busy.

Linux fidji 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

Acer Travelmate 290
RAM - 512MB
Swap ~ 1GB

System: Intrepid Ibex (originally fresh install) updated with ubuntu-security

Attached is the /var/log/messages output.

---

### Post by utnubuuser on 2009-01-17
Can you check your log files to see?  Open ssh... an attack?

---

### Post by b4b4_j4g4 on 2009-01-17
Good point with the attack, but that is very unlikely.
I did not mention that the 2nd machine I was forwarding to, is also mine, both sitting on a fairly insecure lan.
If someone would actually manage to exploit my patched ssh-server, he probably wouldn't be flooding the swap. 
I believe there is about a 100 times bigger chance something with gnome doesn't work, rather than ssh, that could cause this.

Anyway, I checked the /var/log/auth on both machines, both ok.

If you want me to check any specific log or thing, please let me know.

---

### Post by briealeida on 2009-01-17
Can you reliably recreate the problem?

When you do recreate the problem, check the Processes tab of System Monitor. You can sort my memory usage. Notice anything odd?

---

### Post by linux_tech on 2009-01-17
check in /var/log/messages to see if there is anything related to troubleshoot

---

### Post by b4b4_j4g4 on 2009-01-18
@briealeide
No, I can't recreate the problem. Even if I could, once the ram and swap file is full, it means the kernel could not sort out the problem and things get pretty stalled -> system is unresponsive (even to Ctrl-Alt-Bcksp etc...)

@linux tech
unfortunately no 'troubleshooting' mentioned in the log

In fact I posted to this forum cause I hoped someone could have a look at the log I attached and clarify it.

---

