---
title: "A2DP not working in 16.04"
date: 2016-05-15
forum: Desktop Environments
---

### Post by jmarin on 2016-05-15
I have been struggling to get my bluetooth headphones (Sennheiser Momentum ) working with Xubuntu 16.04.  I have been able to make them work a few times, and when they work, they work ok.  It's just that I haven't found a reliable way to make them work every time.  I had Kubuntu 15.10 installed on the same computer and as far as I know, A2DP was working just fine every time.  With Xubuntu, I can usually get the headphones to show in Volume Control, but when I try to route audio to them, the signal meter bar freezes and I can hear nothing.

How can I debug this?

---

### Post by steve141 on 2016-05-22
Dido here!
I still have 12.04 Ubuntu installed and my bluetooth head set (Uproar Wireless) is working.  
Just installed 16.04 Xubuntu on a second HD and can't get the headset to work.  
Hate to go back to the other HD :(, 16.04 Xubuntu is just so pretty!

---

### Post by jeremy31 on 2016-05-22
[http://askubuntu.com/questions/775523/after-updating-to-16-04-bluetooth-audio-a2dp-mode-stopped-working](http://askubuntu.com/questions/775523/after-updating-to-16-04-bluetooth-audio-a2dp-mode-stopped-working)
Might help you out.  I have Ubuntu 16.04 on two laptops with no issues with A2DP using the default bluetooth manager.  It is possible that whatever bluetooth manager you are using in Xubuntu needs the audio.conf file and I know it isn't part of the Ubuntu 16.04 install

---

### Post by jmarin on 2016-05-31
I tried the askubuntu trick but it didn't help.  I can pair my headphones with xubuntu, but when I try to direct audio output to the headphones in A2DP "mode", the volume bar stops moving and I hear nothing.  If I select the headset profile, audio output works, but sound quality is awful.

---

### Post by sgarman on 2016-06-02
I'm encountering this as well, though switching to the headset profile also doesn't result in any audio. Everything worked fine when I was running 15.10. Have also tried a newer kernel (4.4) but am still having issues. I'm a bit obsessed with this problem and I'll report any resolution I come to in this thread.

---

### Post by sgarman on 2016-06-14
Update: I gave up - ended up buying a BT audio transmitter bridge and associate my headphones with that. :(

---

### Post by niburu1 on 2016-06-16
I have the same on Kubuntu 16.04 (upgrade from 15.10). It works if I remove the bluetooth device and pair it from new. But as soon as I disconnect and reconnect, A2DP doesn't work.

I tried the answer in [http://askubuntu.com/questions/775523/after-updating-to-16-04-bluetooth-audio-a2dp-mode-stopped-working](http://askubuntu.com/questions/775523/after-updating-to-16-04-bluetooth-audio-a2dp-mode-stopped-working) but it didn't work.

---

### Post by rilkeansoul on 2016-08-06
Bump
Exactly like above. 
Delete/Repair BT works once.

---

### Post by sgarman on 2016-08-06
I have promising news to report. The issue is in pulseaudio and has been identified in this bug:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1574324](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1574324)

I'm using the pulseaudio packages from Joakim and they work. So it's now just a matter of isolating which patch(es) cause the problem and the bug is In Progress with a High importance. So there should be an official update forthcoming eventually.

---

