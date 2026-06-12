---
title: "CS:GO server performing &quot;better&quot; when stress-tested?"
date: 2018-01-19
forum: Debian
---

### Post by probbzy on 2018-01-19
Hello! 
I recently set up a csgo server on an old machine and it's working surprisingly well. I cleared out core 1 and dedicated it to only the server. I took a note of the var and sv when there are **1/12** players online:[INDENT]Players: 1/12
Core: 1[/INDENT]

Pictures:
[IMG]https://image.prntscr.com/image/H7G4I8iISJKfX_nlOL3gHA.png[/IMG]
[IMG]https://image.prntscr.com/image/wW-CsEMfTm_XHzdyTUK1lA.png[/IMG]




Then I started to stresstest cpu 0 *(server is on core 1)* and got these stats:[INDENT]Players: 1/12
Core: 1[/INDENT]

Pictures:
[IMG]https://image.prntscr.com/image/U0K_SMpzQIu3aRLI5xIq1A.png[/IMG]
[IMG]https://image.prntscr.com/image/BlVYXmCoRdaL-Ke6Zg-HUg.png[/IMG]



As you can see my sv and var went down. I though it might be the cpu-frequency that was fluctuating so i forced it to 2.7GHz, but the results was the same. 
The server is hosted on an old laptop:[INDENT]hp elitebook 2560p
Intel(R) Core(TM) i7-2620M CPU @ 2.70GHz
4GB 1333MHz DDR3 RAM[/INDENT]
OS: Linux laptop 4.9.0-4-rt-amd64 #1 SMP PREEMPT RT Debian 4.9.65-3+deb9u1 (2017-12-23) x86_64 GNU/Linux
[B]Its plugged into the wall without a battery attached. 
[/B]
I disabled Intel HT in the bios but i could not find any power settings.
The server will never have more than 12/12 players online and I'm  pretty sure that it will handle that.




*(Sorry for bad English :oops:! I'm from Norway:wink:*)
[B]

EDIT: [/B]
Forgot to say that i disable intel_pstate module and enabled the [FONT=sans-serif]acpi-cpufreq module to control the frequency. [/FONT]

---

### Post by deadflowr on 2018-01-19
*Thread moved to **Debian***

---

