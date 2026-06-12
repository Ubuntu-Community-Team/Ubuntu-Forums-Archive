---
title: "Daemons that affect power"
date: 2009-04-21
forum: General Help
---

### Post by sol_kanar on 2009-04-21
Hi!

For a project I am currently working on, I managed to reduce cpu VID via Intel Enhanced Speedstep control. Basically, now I can read and write values into the MSRs (Machine-Specific Registers) and some of these MSRs store information about voltage and frequency.

I tried to write values into the MSR that controls the Speedstep and I managed to lower cpu VID to 1.350V to 1.238V: the problem is, it looks like that one (or more?) process is working against my settings, because when the CPU is heavily loaded (e.g. by some stress test like mprime - Mersenne Prime) cpu VID comes back to its maximum value (1.350V).

I removed all the daemons that I believe could influence voltage and Speedstep (cpufreqd, kacpi, powernowd, powertweak), but nothing worked: each time the CPU is loaded, cpu VID switches back to 1.350V .

Can anyone help me? Did I forget some process that could be working against me? (I am running an Ubuntu 8.10 distribution, with kernel 2.6.27-9-generic)

Thank you for your time! :-)

---

