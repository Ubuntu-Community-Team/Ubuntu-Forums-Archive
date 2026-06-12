---
title: "530N running hot?"
date: 2008-06-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Trindol on 2008-06-03
I have an Inspiron 530N running Hardy 64 bit. It's got the stock hardware and it's not overclocked.

E2160 processor (Core2 Duo)
NVIDIA 8300GS

sensors tells me the cores are idling around 50 °C. Fans are spinning normally, they ramp up and down as expected. I have cleaned out the case with canned air a few times and the box is well ventilated. During light-medium usage the temperature will get up to about 57, but it cools back down pretty quickly. I guess this temperature seems hot to me, but I don't really know what "hot" is for this machine, though I have seen many post that their idle temps are more like 30 °C (different hardware, but still 20 °C is a big difference). Room temp for me is about 23-26 °C, so a little hot. Can anyone comment if this is out of the ordinary?

---

### Post by HermanAB on 2008-06-04
50C is quite cold actually.  No problem here.

---

### Post by Technoviking on 2008-06-04
I believe upto 90 C is ok, and my computer has ran about 45-47 C for three years now.

---

### Post by tgrimley on 2008-06-05
50 C is not cold.. 

```

tgrimley@tlomm-node1:~$ sensors | grep Core; uptime
Core 0:      +34.0°C  (crit = +85.0°C)                  
Core 1:      +36.0°C  (crit = +85.0°C)                  
 17:04:05 up 6 days,  3:02, 11 users,  load average: 0.10, 0.24, 0.40

tgrimley@tlomm-node3:~$ sensors | grep Core; uptime
Core 0:      +45°C  (high =   +85°C)                   
Core 1:      +45°C  (high =   +85°C)                   
 17:04:39 up 3 days,  3:32,  6 users,  load average: 1.05, 0.87, 0.93

```

These are sitting up against each other with almost no ventilation..

---

### Post by al_mckin on 2008-06-06
Quite shocked that this is so low.
Can this be right?

alastair@dell-desktop:~$ sensors | grep Core
Core 0:      +17.0°C  (crit = +85.0°C)                  
Core 1:      +17.0°C  (crit = +85.0°C)                  
alastair@dell-desktop:~$

---

### Post by tgrimley on 2008-06-06
I guess it's possible if ambient is 15C and your proc is idle :)

---

### Post by Fearless Freep on 2008-06-13
I have a 530N  that was pre-installed with ubuntu. Can you point me in the right direction to find out how to access this temperature information?





> **Trindol said:**
> I have an Inspiron 530N running Hardy 64 bit. It's got the stock hardware and it's not overclocked.

E2160 processor (Core2 Duo)
NVIDIA 8300GS

sensors tells me the cores are idling around 50 °C. Fans are spinning normally, they ramp up and down as expected. I have cleaned out the case with canned air a few times and the box is well ventilated. During light-medium usage the temperature will get up to about 57, but it cools back down pretty quickly. I guess this temperature seems hot to me, but I don't really know what "hot" is for this machine, though I have seen many post that their idle temps are more like 30 °C (different hardware, but still 20 °C is a big difference). Room temp for me is about 23-26 °C, so a little hot. Can anyone comment if this is out of the ordinary?

---

### Post by tgrimley on 2008-06-13
Run

```

sudo apt-get install sensord
sudo sensors-detect
sensors

```

---

### Post by Fearless Freep on 2008-06-13
Thanks for the help!  I am too much of a noob to digest this all correctly so  I will post my result in hope that you will comment.  I am still running Ubuntu 7.10, could that be part of my problem with the missing drivers?  Do I simply add the i87 & coretemp lines  to /etc/modules: to get those 2 to work?

-----

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `smartbatt' (should be inserted):
  Detects correctly:
  * Bus `NVIDIA i2c adapter '
    Busdriver `UNKNOWN', I2C address 0x0b
    Chip `Smart Battery' (confidence: 5)

Driver `it87' (should be inserted):
  Detects correctly:
  * ISA bus, address 0x290
    Chip `ITE IT8718F Super IO Sensors' (confidence: 9)

Driver `coretemp' (should be inserted):
  Detects correctly:
  * Chip `Intel Core family thermal sensor' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# Chip drivers
# Warning: the required module smartbatt is not currently installed
# on your system. For status of 2.6 kernel ports check
# [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices). If driver is built
# into the kernel, or unavailable, comment out the following line.
smartbatt
it87
coretemp
#----cut here----

---

### Post by tgrimley on 2008-06-13
Oh, that's right.  It should have added them itself, but you need to do a 

```

sudo modprobe smartbatt
sudo modprobe it87
sudo modprobe coretemp 

```
if you don't want to reboot.  On the next boot they should be loaded.  IIRC, I didn't add smartbatt and I don't know what that is, but the other two look right. :)

There may be a better way of doing this, but I don't know it.

After that you can do 

```

sensors
```

---

