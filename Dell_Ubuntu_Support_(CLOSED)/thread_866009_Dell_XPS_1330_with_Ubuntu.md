---
title: "Dell XPS 1330 with Ubuntu"
date: 2008-07-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fullymooned on 2008-07-21
I recently uninstalled the Windows Vista that came by default in my Dell XPS 1330 laptop and installed Ubuntu on it. I love the user friendliness and out of the box tools but am facing a lot of issues getting things to work that used to work with Windows. 

1. HDMI is not working anymore. 
2. I cannot connect to my Lexmark 2500 printer 
3. Creative XiFi Xtreme Audio is not working anymore and the sound from the speakers is extremely low 
4. Finger scan does not work anymore 

I am hoping to get all these issues resolved soon, else I am afraid I will have to re install the Windows Vista CD's which I really do not want to do. Would calling Dell support help?

---

### Post by Potatoj316 on 2008-07-21
Ok, you probably wont like my answers but here they are.
1. I dont think Linux has HDMI support
2. Not all printers work with CUSPS, try looking at the Lexmark site they had drivers for my printer
3. Check the sound settings manager
4. I dont know if the scanner is suported either.

I doubt you will get help from dell unless you bought the computer with ubuntu already on it from them.

---

### Post by fullymooned on 2008-07-21
I did not buy the Dell with ubuntu on it. But can I have them mail me the CDs for Ubuntu drivers since they do sell XPS with Ubuntu on it. 

For me having the HDMI and Printer is most important. Lexmark does not provide drivers for Ubuntu on their website.

---

### Post by Potatoj316 on 2008-07-21
They might provide debian (.deb) drivers and those will probably work in ubuntu.  I doubt they will send you disks for the drivers for free, but they might sell them to you.

---

### Post by damis648 on 2008-07-21
For the HDMI support, you must install the Nvidia driver. Use System>Administration>Hardware Drivers and check the box next to your card. When you reboot, use Fn+F8 to switch to HDMI, assuming it is plugged in.

---

### Post by damis648 on 2008-07-21
For the audio, double click the volume icon in the upper right hand corner. Click Edit>Preferences and check all the boxes. Now in the mixer, just unmute everything and turn up everything. As for the Printer, Lexmark does not provide adequate drivers for Ubuntu. Sorry. Try a google search, searching "ubuntu [printer model]" and see what you get. Also, for the fingerprint reader, have a look at fprint and fprint-demo.

---

### Post by paddy1978 on 2008-07-21
Can't help with 1-3 above, but for 4, you should try this: [http://thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger]("http://thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger")

There are specific instructions for Ubuntu (Hardy). With these, I manged to get fingerprint reading working fine on my xps m1330.

(There are also some instructions on the Ubuntu wiki, but I'm not sure they're correct and they seem a lot more complex... - they seem to apply to older versions too)

---

### Post by eximius1 on 2008-07-21
This site might help you:

[http://www.nervous.it/2007/11/linux-dell-xps-m1330/](http://www.nervous.it/2007/11/linux-dell-xps-m1330/)

And as for the HDMI:

> **clauslund said:**
> I just want to say what I did to get the HDMI video working on my Dell XPS m1330.

I have the nVidia gfx so this will be different for the ones with integrated gfx.

But I just installed the nVidia driver (the one "atomagically" suggested), then installed the nvidia-settings tool (also available through synaptic/apt-get).

Then run the nvidia-settings tool:

```
gksudo nvidia-settings
```

The XServer display configuration screen should have both the laptop and external display.
Configure things how you like them (I used TwinView and set things up as clones) and then you probably just need to restart X (Alt+Ctrl+Backspace).

Voila!

From another thread

---

### Post by TimDaniels on 2008-07-24
> **fullymooned said:**
> I recently uninstalled the Windows Vista that came by default in my Dell XPS 1330 laptop and installed Ubuntu on it. I love the user friendliness and out of the box tools but am facing a lot of issues getting things to work that used to work with Windows. 

1. HDMI is not working anymore. 
2. I cannot connect to my Lexmark 2500 printer 
3. Creative XiFi Xtreme Audio is not working anymore and the sound from the speakers is extremely low 
4. Finger scan does not work anymore 


I also have a M1330 Vista laptop onto which I've installed as a dual-boot the Dell Ubuntu 7.10 .ISO file.  I've gotten Ubunt's Bluetooth to work with my Dell Bluetooth Travel Mouse, but now I'm stuck in trying to get Wi-Fi to work.  In the Network dialog box, I can see the wireless entry contain the name of my Wi-Fi router, and all the parameters seem to be the same as in the Vista installation (whose Wi-Fi works fine).  WPA2 keeps revertiong to WPA, though, and I can't use the Wi-Fi to browse.  Owners of the M1330n seem to all experience Wi-Fi success "out of the box", and I'm wondering why I'm not seeing that.  Any ideas?

*TimDaniels*

---

### Post by TimDaniels on 2008-07-24
> **TimDaniels said:**
> I also have a M1330 Vista laptop onto which I've installed as a dual-boot the Dell Ubuntu 7.10 .ISO file.  [....]I'm stuck in trying to get Wi-Fi to work.

P.S. my router uses the "G" speed.

*TimDaniels*

---

### Post by akeel on 2008-09-09
> **eximius1 said:**
> This site might help you:

[http://www.nervous.it/2007/11/linux-dell-xps-m1330/](http://www.nervous.it/2007/11/linux-dell-xps-m1330/)

And as for the HDMI:



From another thread

I have another problem here guys, hopefully some of the guru`s can help me with this one. It is reagarding HDMI output on my 50" Panasonic flat screen.
I wanted to watch an episode of Prison Break on my tv with output from my laptop with Ubuntu 8.04. I set up the Nvidia X Server Settings gui. With screen nr 2 as my plasma screen. But when I set it up for my tv`s native resoulution 720p (1280x720) it outputs in 1280x800 :-(
It says down on the settings screen that it has switched to Meta Mode 1280x800 and thats it.
So everything I want to watch is being "cut" both vertically and horizontally.

Anyone had this problem??? It should put out the correct resolution all by itself like even the windows vista **** could do......

If I get this glitch fixed I will be 100% happy with Ubuntu :-) But this is a very very important thing for me as I mostly use the laptop for this purpose......

Thanks guys!

---

### Post by akeel on 2008-09-11
Anybody??????

---

### Post by goombamd on 2008-09-11
Does anyone else have a GPU temperature of >60 at all times, even when idling?  Then it gets really hot if trying to do anything like watch youtube or use compiz effects.

Still, no reason it should be really hot when idling. I've basically reverted back to windows because I can watch videos on windows and multitask without the laptop getting hot.  With ubuntu.. it BURRRRRRRNS

Anyone else with this issue? I tried some of the power savings suggestions but to little avail.  

It's clearly not the nvidia hardware since it works fine in Vista.

---

### Post by paddy1978 on 2008-09-12
I'm using the 'Sensors applet'. After about 30 mins of idling/web browsing it's showing 44C for GPU, 33 for CPU and 31 for disk. (Room temperature here is only about 19C though!)

Watching flash video and using some compiz effects for a few mins and the GPU temp goes up to mid-50s, CPU approaches 40.

---

