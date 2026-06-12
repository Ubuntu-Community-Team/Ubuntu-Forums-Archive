---
title: "Conky battery time wrong"
date: 2009-03-26
forum: General Help
---

### Post by squaregoldfish on 2009-03-26
Hello

I'm running conky on my laptop, and have it displaying the battery percentage and time remaining as follows:

Battery: ${battery_percent BAT1}% (${battery_time BAT1})

The percentage is fine, but the time is completely wrong - it's currently showing a remaining time of 33m 34s, whereas other battery monitors reckon I've got over 3 hours of battery life left.

Does anyone have any thoughts on why it might be behaving this way?

Incidenatlly, I've tried this on another laptop and it's fine.
If also checked the acpi folders, and BAT1 is the only battery listed.
In case it's relevant, I'm using a Toshiba Satellite Pro.

Thanks in advance,
Steve.

---

### Post by ViMMeD on 2009-03-27
Also getting this problem, I notice for me it's only when the battery is recharging to full.  Say it takes 3 hours to fully charge, it will display the correct percentage, but it will show only a few seconds left to charge instead of 3 hours.  The discharge time seems accurate though.

---

