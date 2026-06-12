---
title: "Second Monitor always overlayed with green hue"
date: 2009-08-22
forum: Desktop Environments
---

### Post by ccbristo on 2009-08-22
A few months ago, I set up xinerama so that I could run two monitors off of my laptop.  It worked great for the first few weeks or so, but recently, the second monitor has spent an increasing amount of time with a green "overlay". All windows appear green on the second monitor, including the desktop wallpaper.  At first, it would last a few seconds, then return to normal.  Now the overlay is almost always present.

I have ruled out the monitor and connection as the source of the problem by connecting the monitor to a different computer (it worked correctly).

I have not been able to rule out the rendering software or the hardware in the laptop at this point.

I also took a screen shot of a single window (Alt+Prnt Scrn) on that monitor, and saw that the screenshot did not have this overlay.  I am not confident enough in that test to rule out drivers or any other software that may be involved in determining the colors sent to the monitor.

If you look at the attached image, you can see that the monitor on the left shows a default ubuntu wallpaper, that is mostly red.  The monitor on the right should be the exact same color, but for some reason, the wallpaper appears green.

Does anyone know of any diagnostic tools I could use to track this down?  Any help is greatly appreciated.  Thanks in advance.

---

### Post by ccbristo on 2009-09-26
In case anyone is interested, I installed Windows 7 on the same computer and see the same issue when using that computer.  Since I have already ruled out the monitor as the cause by connecting it to another computer and not seeing the issue, and can now see the problem using two different OSes, I am certain this is a hardware issue.  I have a feeling this is related to a BIOS update released by HP that fixed issues with the fans waiting too long to turn on, thereby allowing overheating.  This burned up my network card some time ago, and I can only assume that this must have also done some damage to the video hardware.  Not sure that I mentioned my hardware previously, but I have an HP Pavilion dv9000nr laptop. I believe it is a 2007 model, but I don't quote me on that part.  Hope this helps in case anyone else runs into this.

---

### Post by betolima on 2009-09-29
[Hi ccbristo]("http://ubuntuforums.org/member.php?u=651801"),

Thats a hardware problem for sure.. but I don't believe it could be related to the BIOS .. seems like you have just a hardware malfunction .. maybe a dirty connector or a problem in video cards circuitry itself .. first thing to try is cleaning the video connector ..

[]s

---

### Post by ccbristo on 2009-09-29
I agree that the BIOS update is not the cause, but I think the problem for which the update was released allowed this problem.  The BIOS updated corrected fan control problem which allowed overheating.  This problem burned up the network card, and I think it must have also affected the video hardware.

---

### Post by betolima on 2009-09-29
I saw a lot of fan problems on HP notes, but never hardware burning as result ... actually I have never seen a hardware burning without external causes.. it seems very unlikely .. especially if you didn't get some minor malfunction before ... if you're sure thats the problem, then its solved .. if you  have the skills, you could try to measure signal levels over the plug .. but my first guess would be that a video card burned would affect both displays .. cause the hardware driver that feeds the monitor is probably the most strong component on the board.. the issue here is that messing around on notebook hardware is somewhat complicated .. I trying to recover a compaq from video issues myself right now .. and after a lot of screws I didn't even reach the card yet ... 

Sometime ago I went to a office and a girl complained about a monitor acting funny .. the image, a few minutes after turning on, starts to become smaller and smaller .. some tech guy said to her that was a monitor problem and it would cost a lot .. with nothing to loose I gave a shot and poked around on the plug a little bit .. for my surprise it solved .. probably dirt on the plug ... 

I believe it would be my first try on your machine too ..

---

### Post by ccbristo on 2009-09-29
Good point about affecting both monitors.  I guess a defective connection cannot be ruled out at this point as well.  I might try to get some compressed air tomorrow and see if that helps. I am afraid of jamming something in there for fear of seriously damaging the port.

---

### Post by betolima on 2009-09-29
Based on high quality components used today, I believe is very unlikely you would need a air compressor .. try to clean the female plug (the monitor one) with cotton and alcohol (be *very* gentle on that) and then use it to poke a little bit on male plug (computer one) ... but I still believe it would be better you take the machine to a tech service, doesn't it ? Unless you're in a area where there's no such facility ... after all it seems pretty sure thats not a software issue and a hardware one on notebook is not easy to address ...

[]s

---

