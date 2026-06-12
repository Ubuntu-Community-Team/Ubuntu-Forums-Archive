---
title: "battery icon doesn't update the remaining battery time when discharging"
date: 2009-01-28
forum: General Help
---

### Post by c.mueller on 2009-01-28
I just did an automatic upgrade and a pop up notified me "Battery switched off". Afterwards the battery status icon in my status bar is no longer working. It will display the status properly when charging, but not do any updates on discharging.

cat /proc/acpi/battery/BAT0/state displays the proper remaining capacity, but is missing present rate and voltage.
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            unknown
remaining capacity:      41200 mWh
present voltage:         unknown

I just disconnected the power plug for 2 minutes, the capacity drop immensely fast. 

I have a Sony Vaio VGN-FE41M with Kubuntu 
cat /etvc/issue returns Ubuntu 8.04.2

Any ideas? I appreciate any suggestion? Many thanks in advance

Cheers,
Christine

---

