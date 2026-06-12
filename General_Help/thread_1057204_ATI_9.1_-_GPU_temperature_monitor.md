---
title: "ATI 9.1 - GPU temperature monitor"
date: 2009-02-01
forum: General Help
---

### Post by marcgh on 2009-02-01
Is there any way to monitor the GDU temperature like sensor applets?

I have a ATI RADEON 4850 and the new drivers 9.1 installed, my Ubuntu is 8.10 with the latest updates.

I can read the GPU temperaure in the terminal with the command:

   aticonfig --od-gettemperature

but I would like to have it more graphically and eventually together with the other system temps. in the sensor applets.

Thanks for any suggestion.

---

### Post by marcgh on 2009-02-02
What if I BUMB this nicely?

---

### Post by marcgh on 2009-02-04
bump. Anybody?

---

### Post by ahepas on 2009-02-04
hello. you can use conky. put this line in conkyrc ${color slate grey}GPU Temp:${color} ${execi 60 aticonfig --adapter=0 --od-gettemperature}°C
, change it according to your needs. 
cheers

---

### Post by marcgh on 2009-02-04
Thanks Ahepas, 
I will try this when I am back home later in the day.

---

### Post by XSAlliN on 2010-05-31
Ok, so i tried the above in conky and this is what I get:

[img]http://img708.imageshack.us/img708/1142/screenshotkkl.png[/img]

Tried to tweak it the best I could but, that's the best result so far... 

Browsed hundredths of posts from conky config thread, but no luck. Mostly nVidia, and the few ATi related didn't work at all...

All I wanted was:

GPU Temp: 38*C 

=====

Did any of you found a better config? 

I'm Ubuntu Lucid 10.04 - catalyst 10.5 linux k. 2.6.34

---

### Post by XSAlliN on 2010-05-31
Anybody? :confused:

---

### Post by Urithar on 2010-06-01
I am trying to find this out to, got a 5450  though.
found this:

${execi 60 aticonfig --od-gettemperature | grep Temperature | cut -c43-47}C

gives me the temperature with 2 decimals (38.00). dunno how i can get rid of the decimals though :(. would like to reduce it to 1 decimal or just none tbh. buit its my first time using ubuntu :) so i cant say i got a big clue of what i am doing.

---

### Post by Ralfito on 2010-11-14
Does

${execi 10 cat /proc/acpi/thermal_zone/TZ02/temperature | grep '[0-9][0-9]' -o}°C

work for you?

---

### Post by mirrors on 2011-07-31
> **Urithar said:**
> I am trying to find this out to, got a 5450  though.
found this:

${execi 60 aticonfig --od-gettemperature | grep Temperature | cut -c43-47}C

gives me the temperature with 2 decimals (38.00). dunno how i can get rid of the decimals though :(. would like to reduce it to 1 decimal or just none tbh. buit its my first time using ubuntu :) so i cant say i got a big clue of what i am doing.

Sorry to bump this ancient thread, but for all the people arriving from Google etc., here's the code to only display it to two decimals like OP inquired.

${execi 60 aticonfig --od-gettemperature | grep Temperature | cut -c43-44}C

---

