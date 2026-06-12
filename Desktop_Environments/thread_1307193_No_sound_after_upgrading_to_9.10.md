---
title: "No sound after upgrading to 9.10"
date: 2009-10-30
forum: Desktop Environments
---

### Post by 47_MasoN_47 on 2009-10-30
I use optical audio for sound (whatever that series of numbers is...) and after upgrading to 9.10 I don't have any sound at all anymore.  I'm using an Asus P5K3 Deluxe with integrated sound if that helps.  If there are some log files or something I can post to help, please let me know.

Thank you!

---

### Post by gypsumwolf on 2009-11-02
I have a Dell Mini 10. The same thing with no sound happened to me after upgrade (of 9.10). Now the sound is working perfectly. I used this to fix the problem (Its very simple to do). Maybe the solution for your card is somewhat similar.

[http://georgeblog.nyarangi.com/2009/10/no-sound-on-dell-mini-10-running-ubuntu.html]("http://georgeblog.nyarangi.com/2009/10/no-sound-on-dell-mini-10-running-ubuntu.html")

Quoted from the website:"

Follow these steps:
1.First you must find which model of sound card you use, so run this command:


```
cat /proc/asound/card0/codec#* | grep Codec
```


Note: You should obtain this:


```
Codec: Realtek ALC269
Codec: Silicon Image SiI1392 HDMI
```


This means that your soundcard is ALC269. If it is not ALC269, follow the instructions here. Otherwise, continue to step 2.

2.Open /etc/modprobe.d/alsa-base with the following command:

```
sudo nano /etc/modprobe.d/alsa-base.conf
```


3.Paste the following line at the end of the file:

```
options snd-hda-intel model=basic
```


Save the file and close it.

4.Go to System>Preferences>Sound>Hardware.
On the Profile drop down menu, select "Analog Stereo Output".
Make sure the Output Volume is set to 100% and close.

5.Reboot and now you can enjoy Karmic with sound:) "

---

### Post by 47_MasoN_47 on 2009-11-05
The output of the terminal command came out "Analog Devices AD1988B" for me, so I don't think the rest of that tutorial would work since it is for intel sound cards.  Thanks for the link anyway though.

---

### Post by CovenStine on 2009-11-16
Different board, same card, same problem.
<bump>

---

