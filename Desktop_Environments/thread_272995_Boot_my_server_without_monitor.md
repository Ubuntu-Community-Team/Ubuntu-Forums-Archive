---
title: "Boot my server without monitor"
date: 2006-10-07
forum: Desktop Environments
---

### Post by pietrob71 on 2006-10-07
I'have made my wonderful server with Ubuntu Dapper. Fantastic! Everything works fine! Only one problem. I want to boot my server without mouse, keyboard and monitor and control it by VNC. All works fine but if I boot without monitor connected the resolution shift automatically on VGA (640x480) and when I connect to it by VNC I see a small desktop.

I don't like it![-( 

Is there someone that can help me?

Thanks in advance!

Pietro

---

### Post by ropers on 2006-10-07
Does this happen when you simply detach the monitor, or do you also take out the graphics adaptor card?

---

### Post by pietrob71 on 2006-10-07
I detach only the monitor's cable; the graphics adaptor card is integrated in the mainboard.

---

### Post by bartbes on 2006-10-07
Have you checked the settings of your VNC server? Is it bigger when you connect a monitor to the server and then connect via VNC?

---

### Post by pietrob71 on 2006-10-07
With same setting of VNC
boot with cable connected -> 1024x768
boot with cable disconnected -> 640x480

The monitor resolution of pc from I connect to server is bigger than resolution of server -from 1600x1200 to 1280x1024-

---

### Post by xristos on 2006-10-20
Same problem here .
Any ideas ?

---

### Post by mister_p_1998 on 2006-10-20
Well the quick and dirty way I use (to boot my box on a timer with the monitor turned off) is to run dpkg-reconfigure xserver-xorg and when it come to available resolutions - turn OFF 640 x 480. This then boots into the first available resolution, which on mine is 800 x 600. if you want a higher startup res, flag off all lower ones.
Steve

---

### Post by CatKiller on 2006-10-20
You could potentially put the setting into your xorg.conf to ignore the EDID frequencies - that's the bit that detects what your monitor is capable of, as I understand it. It doesn't get a successful report on any resolution, since there's no monitor there, which is why it comes up as VGA.

I can't remember what the option is, and I haven't tried it, but it might work.

---

### Post by jursoleo on 2006-11-05
boot without keyboard  [http://www.versalent.biz/keylim.htm](http://www.versalent.biz/keylim.htm)

---

