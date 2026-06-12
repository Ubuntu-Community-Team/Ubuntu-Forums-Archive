---
title: "Desktop lock up + logs entries"
date: 2009-03-15
forum: Desktop Environments
---

### Post by alexpotato on 2009-03-15
Hey everyone,

Been having the following issue:

After my laptop is idle for a random amount of time, the system is in partial lockup. Here is what I have determined so far:

-the time "freezes" both using ntp and not. e.g. It will be stuck at some time in the past so if the current time is 9:45 it will show 6:34 (when I assume the issue begins)
-I can ctrl + tab through tabs in firefox but I can't click on applications, places etc
-I can hit caps lock and num lock and the light turns on but then it won't go off.

I am using Ubuntu 8.04. I have turned off compiz desk effects as well as the gnome power manager(other ideas people had). If you guys need any other details(e.g. output on hardware etc) just let me know.

Below is the output from /var/log/messages around the time of the freeze. I keep seeing the same entry over and over again.

Mar 14 21:45:46 stealth kernel: ]  [tick_notify+0x25b/0x390] tick_notify+0x25b/0x390
Mar 14 21:45:46 stealth kernel: [20788.261706]  [notifier_call_chain+0x30/0x60] notifier_call_chain+0x30/0x60
Mar 14 21:45:46 stealth kernel: [20788.261746]  [raw_notifier_call_chain+0x17/0x20] raw_notifier_call_chain+0x17/0x20
Mar 14 21:45:46 stealth kernel: [20788.261766]  [processor:clockevents_notify+0x19/0x5760] clockevents_notify+0x19/0x60
Mar 14 21:45:46 stealth kernel: [20788.261788]  [<f8869619>] acpi_idle_enter_simple+0x166/0x1b9 [processor]
Mar 14 21:45:46 stealth kernel: [20788.261841]  [cpuidle_idle_call+0x7c/0xb0] cpuidle_idle_call+0x7c/0xb0
Mar 14 21:45:46 stealth kernel: [20788.261859]  [cpu_idle+0x45/0xd0] cpu_idle+0x45/0xd0
Mar 14 21:45:46 stealth kernel: [20788.261882]  [start_kernel+0x31f/0x3b0] start_kernel+0x31f/0x3b0
Mar 14 21:45:46 stealth kernel: [20788.261894]  [unknown_bootoption+0x0/0x1e0] unknown_bootoption+0x0/0x1e0
Mar 14 21:45:46 stealth kernel: [20788.261956]  =======================

---

