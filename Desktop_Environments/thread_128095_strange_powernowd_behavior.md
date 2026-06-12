---
title: "strange powernowd behavior"
date: 2006-02-10
forum: Desktop Environments
---

### Post by einKI on 2006-02-10
Hi

My machine is an AMD Turion 1.8GHz. With the default configuration frequency scaling doesnt work.
But when I load the modules cpufreq-userspace and powernow_k8
and then
/etc/init.d/powernowd stop
/etc/init.d/powernowd start

i get
"This processor "AMD Turion(tm) 64 Mobile Technology MT-34" is known _not_ to support power-saving."

However when i do
cpufreq-selector -f 900000
the cpu switches to 900MHz according to /proc/cpuinfo.

But automatic frequency selection doesnt work either. I can write a shellscript
or a C++ programm and check in a timer cpu load and use cpufreq-selector from there.
But this is not really an optimal solution so have anyone an idea why the powernowd stuff doesnt work?

thx
Lukas

---

### Post by einKI on 2006-02-12
Hi

Problem is solved i had to manually add

powernow_k8
cpufreq_userspace
cpufreq_conservative
cpufreq_powersave
cpufreq_stats
cpufreq_ondemand
cpufreq_stats
cpufreq_userspace

to /etc/modules

now automatic frequency sclaing with the ondemand governor works but i dont know why this is not done automatically.
On my old laptop it works out of the box.

by
Lukas

---

