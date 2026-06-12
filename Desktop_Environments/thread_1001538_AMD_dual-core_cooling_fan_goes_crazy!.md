---
title: "AMD dual-core: cooling fan goes crazy!"
date: 2008-12-04
forum: Desktop Environments
---

### Post by randywilharm on 2008-12-04
With high-load applications like Cinelerra, one of the
cooling fans has excessively HIGH R.P.M. and according to
the readout it looks like one processor is taking
all the load instead of both processors.

I actually removed the heat sink and cleaned it
spotlessly (it was dirty) but the fan still
speeds up.

Attached is .png of terminal readout.

Can anyone help me with this?

---

### Post by randywilharm on 2008-12-04
Can anyone tell me if the
readings on the .png look abnormal?

---

### Post by sayakb on 2008-12-04
Probably a CPU intensive process? Install **htop** and post the output of htop from terminal.

---

### Post by randywilharm on 2008-12-09
THank You for your reply-

I have installed HTOP and enclosed are 2 images
showing HTOP readout before and after using a
high CPU draw application (KINO DV editor).


EDIT: 12-09-08  --i'M SORRY ABOUT THE PICS I replaced them

with good ones

---

### Post by randywilharm on 2008-12-09
> **LinuxIsInnovation said:**
> Probably a CPU intensive process? Install **htop** and post the output of htop from terminal.

THANK YOU for your reply.

I posted some .png images of the HTOP

to replace the first ones. Please tell me what you think.

---

### Post by keithld on 2008-12-10
**randywilharm**, after you cleaned the heat sink did you use any kind of thermal conductor like Arctic Silver when you replaced it???...

Usually due to the unevenness of surfaces you need a compound spread evenly between the CPU & the Heat Sink in order for the heat sink and the fan to do their job correctly... I replaced my heat sink a year or so ago on my Dual AMD before I decided to run Ubuntu/Linux and I'm not seeing any of my three fans going crazy at all... Are yours also making a lot of buzzing, vibrating noises??? This could mean that one of them or more are at the end of their life and need to be replaced...

I use "Everest" while in WinblowsXP to monitor my fans and I usually see the RPM's go up and down depending on what I am doing, such as surfing, Photoshop or whether I'm running SETI@Home when both processors are chugging away...

---

### Post by psusi on 2008-12-10
Your temperature looks a little bit high, but not bad.  Temp1 is the CPU, Temp2 is probably the northbridge, and Temp3 is probably somewhere else on the motherboard, which is why they are different temperatures.

My motherboard doesn't have sensors connected to temp2 and 3, but I've got fancontrol working well and most of the time when the system is relatively idle and running at only 1 GHz, the temperature hovers around 30 and the fans often shut off entirely.  Even under heavy load on both cores of my Athlon 64 X2 5000+, the temp doesn't really go over 45 which is where I have the fans going full power.  I keep an eye on the temp and fan speeds on the top pannel in gnome with sensors-applet and the cpu frequency scaling monitor applet.

---

### Post by randywilharm on 2008-12-10
You just taught me something. 
I did'nt even know about that stuff.
I upgraded to 8.10 and it's gotten a little quieter
With all this in mind, i'm going to mark
this issue as solved. THanks for your work. 



> **keithld said:**
> **randywilharm**, after you cleaned the heat sink did you use any kind of thermal conductor like Arctic Silver when you replaced it???...

Usually due to the unevenness of surfaces you need a compound spread evenly between the CPU & the Heat Sink in order for the heat sink and the fan to do their job correctly... I replaced my heat sink a year or so ago on my Dual AMD before I decided to run Ubuntu/Linux and I'm not seeing any of my three fans going crazy at all... Are yours also making a lot of buzzing, vibrating noises??? This could mean that one of them or more are at the end of their life and need to be replaced...

I use "Everest" while in WinblowsXP to monitor my fans and I usually see the RPM's go up and down depending on what I am doing, such as surfing, Photoshop or whether I'm running SETI@Home when both processors are chugging away...

---

### Post by randywilharm on 2008-12-10
After cleaning the heat sink I replaced it
without using a thermal conductor
like ARCTIC SILVER and that is the no 1 suspect
in the CPU temp issue.

After upgrading to 8.10 the fans were a little
quieter (with heavy load on CPU) and with
this in mind i'll mark this as SOLVED.

And many thanks to you all for your good advice!

---

### Post by keithld on 2008-12-10
Without the compound your CPU will run hotter because there is not perfect contact between it and the Heat Sink... Artic Silver is one of the best and helps transfer the heast to the Heat Sink...

---

