---
title: "glxgears--gears deformed?"
date: 2005-07-20
forum: Gaming &amp; Leisure
---

### Post by Jmonti on 2005-07-20
Hello all!

This is a strange one. On my 1st install of Ubuntu, glxgears ran fine, as in, the fps were good and the spinning gears looked right. On my second install the fps are still good (12xxx- 13xxx) but the "gear display" is not running right. The gears look deformed and dont spin as much as vibrate. 3D games like tuxracer and neverball run fine. I'm just picky- and hate anything to be out of sorts, which is why I reinstall often. 

Could the nvidia drivers be messed up?

Thanks in advance.

---

### Post by artinla on 2005-07-20
It is just an optical illusion created when the scan rate of your monitor matches the frequency of the rotating teeth or certain harmonics of that frequency.  This occurs at varying levels because when gears is running, the framerate swings up and down, often crossing these harmonic thresholds.

Bottom line, it is normal, but particularly evident on really high end hardware.

Art

---

### Post by Jmonti on 2005-07-21
[QUOTE=artinla]It is just an optical illusion created when the scan rate of your monitor matches the frequency of the rotating teeth or certain harmonics of that frequency.  This occurs at varying levels because when gears is running, the framerate swings up and down, often crossing these harmonic thresholds.

Bottom line, it is normal, but particularly evident on really high end hardware.

Art[/QUOTE]


Hi Art,  That explanation sounds valid. I have changed the refresh rate from time to time, and I dont remember what I had it set at when it looked normal in my 1st install.  In any event, Im doing a clean install onto a bigger HD and will run it again after I install the drivers taking note of my refresh settings. 

Thanks for the help, I'll let you know how it goes.

On a completely unrelated topic (sorry)  how secure is the base Ubuntu system? I dont always run behind a router, so I'm wondering if Firestarter is a must- or overkill or what. Window$ has forced me to be Paranoid  :shock:  In other words, if I dont run any servers or anything and just setup for web surfing, just how hackable is a box running an updated Ubuntu install sitting on the web?

I know there are tools to test these things, but Im no sys-admin.  ;-) 

Thanks again

J

---

### Post by artinla on 2005-07-21
I know I am going to catch flak for saying this, but *my experience* has been that the base install of ubuntu doesn't need much in the way of added security.

Most of the threats out there are designed to damage windows systems, not linux.  As long as you aren't doing anything stupid (such as running a telnet server with a weak or no password) then not much is likely to do you harm.

f-prot offers an antivirus for linux (free) and I run it, but it has never detected a virus on my machine.  

I run my machine with the philosophy that nothing I have on there is really important.  If it is, I back it up.  I also like to use rar to encrypt my personal files and password them.  I think that the hassle of over-securing a system greatly overshadows the small possibility that someone will do my system harm and I would have to reload it.

Hope that answers your question.

Art

---

### Post by Jmonti on 2005-07-22
Hi Art,

well as you said, the drivers seem to be fine. I reinstalled and get the same "gears".
one strange thing is that after installing the nvid. drivers I am stuck with 60 Hz refresh rate. ???? so I cant even try another refresh to test it out. 

anyhow, thanks for the reply about security. I didn't think an antivirus was even needed. Are there viruses in the wild on linux boxes? Since I'm not running any type of server, or ssh or telnet ect.... I guess the standard firestarter will do fine. The day I have to run an antivirus,firewall,antispywear-anti adwear package on my linux box is the day I start running off a live cd for everything!!! LOL

Thanks again

---

### Post by evilghost on 2005-08-07
You've got a high-end card, I get the same stuttering you do.  I love it, as it's an indication that my hardware is working great.  I'm running at 1280x1024@100Hz.

For your refresh-rate issues, try running "gtf" in a terminal to generate the modeline you need to apply to your xorg.conf to run the right refresh/resolution.

---

### Post by dolf on 2005-08-08
export  __GL_SYNC_TO_VBLANK=1

before starting OpenGL programs should remove the flickering. It will however drastically reduce the framerate of glxgears to probably 75Hz.  Have a look at /usr/share/doc/NVIDIA..../README or wherever that sucker might fly around under Ubuntu about other goodies such as antialiasing etc.

---

### Post by Jmonti on 2005-08-09
Thanks guys, those are good tips. I'll take a look when I get home. It would be nice to be able to crank up the refresh rate. But to be honest, I'm looking at the LG L1980Q LCD and I think that will change my refresh options. Its hard to swallow that price tag though  :neutral:

---

