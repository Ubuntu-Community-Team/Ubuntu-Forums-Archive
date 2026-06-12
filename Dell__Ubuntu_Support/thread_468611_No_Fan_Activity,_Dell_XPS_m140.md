---
title: "No Fan Activity, Dell XPS m140"
date: 2007-06-09
forum: Dell  Ubuntu Support
---

### Post by EvilGnome on 2007-06-09
Hi, I just installed Ubuntu 7.04 on a Dell XPS m140, and the fans don't seem to be active. Please help me if you can, I don't want my laptop to overheat.

Thank you in advance for your help.

---

### Post by EvilGnome on 2007-06-10
Sorry for the false alarm, I installed gkrellm and the i8k stuff, and everything seems to be fine.

---

### Post by kDAVR on 2007-08-10
how did you get it to work with 18k and gkrellm. i tried both and still noactivity. i ahve the exact same laptop, but am using ubuntu studio, its still feisty fawn. would love to know your solution because i fear my laptop will overheat without the fans.

---

### Post by hophead929 on 2007-08-20
I have m140 and had the same issues. I found this info on another thread (would link it but I didn't bookmark it).

To check the temperature of the processor using the terminal, you can try:
watch acpi -V
(or watch acpi -Vf for Fahrenheit)

Fan and temp control (install gkrellm)
1. sudo apt-get install i8kutils gkrellm gkrellm-i8k
2. sudo modprobe i8k force=1
3. sudo gedit  /etc/modules
4. add the following line to the end of the file: i8k force=1
5. go to System > Preferences > Sessions > Startup Programs
6. Click ADD and put the command: gkrellm
Now you will see the GKrellm utility load at startup and you can then configure your fan thresholds in settings - plugins - Dell i8k

After installing gkrellm, I opened it and under Plugins, found Dell I8K Plugin. After enabling it, I saw that only the left fan was on. I changed the Temperature Units from Celsius to Fahrenheit, then the right fan came on. I thought this was a coincidence at first, but everytime I change it to Celsius, the right fan goes back off. 

Hope this helps.

---

### Post by hophead929 on 2007-08-20
Figured out why both fans only came on in Fahrenheit. In the plugin configuration there are temps triggers for the left and right fans, for low and high. By default, the numbers are set for Celsius. The right fan would not have cutoff again until the system was at 50 F had I not changed back to Celsius. 

Keeping the low triggers at 40 C and the high triggers at 45 C for both fans seems to work pretty well. The temp stays between 35 and 45 all the time so far.

---

### Post by kDAVR on 2007-08-23
well, i got it to work, i made th emistake of not configuring any of this as root, did it all as regular user. might work for you guys, just log in as root, get and install the same tools and then run gkrellm, right click select configure, select plugin and activate Dell i8k plugin.

good luck.

---

