---
title: "How to permanently kill a process."
date: 2009-01-26
forum: General Help
---

### Post by johnnyxxxcakes on 2009-01-26
I always have the bluetooth applet on in the Process List within the System Monitor. If I kill the bluetooth process, that should give me slightly more battery life on my laptop. Well everytime I kill the process, it comes back on startup. Is there anyway to keep it from coming on all together?

---

### Post by x33a on 2009-01-26
go to system -> administration -> services

disable bluetooth device management from there.

---

### Post by adamlau on 2009-01-26
Or remove 'bluetooth' and accompanying 'bluez' packages if you do not require Bluetooth support at all, being careful not to remove conditional packages if you require them.

---

### Post by Egi_Power on 2009-01-26
> go to system -> administration -> services

disable bluetooth device management from there.

The easiest way is how x33a suggested, I think.

After the next time you boot up, it won't start the process at startup, so you won't have to kill it.

---

### Post by johnnyxxxcakes on 2009-01-27
Okay, thank you guys.

---

### Post by SunnyRabbiera on 2009-01-27
Hire Chuck Norris, will keep it dead too :p
(Chuck Norris jokes never get old :D)

---

