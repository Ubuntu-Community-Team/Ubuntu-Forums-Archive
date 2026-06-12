---
title: "Grub Problem"
date: 2009-03-10
forum: General Help
---

### Post by SuperIntense on 2009-03-10
I need help desperately! I was doing a memory test with Grub and I messed with a memery setting and now my computer will not boot to anything. I can't even get it to the BIOS. Please help. Also I installed Ubunto on an external hard drice so I wouldn't mees with my normal Vista system. When I get this back up is there a way to get this grub off?

---

### Post by Distilled on 2009-03-10
Does it post at all?

Does it show anything at all? Or is it just black? It's pretty tough to brick a computer..not really but I doubt you bricked it by changing a memory setting -.-

---

### Post by SuperIntense on 2009-03-11
It does not show anything or even try to boot. It just runs doing noting. I changed how the memory is looked at. If I could just get to some kind of boot menu icould probly fix this. Any idesa

---

### Post by MaxIBoy on 2009-03-11
Does the screen display the logo of your computer manufacturer or motherboard manufacturer? If so, there's hope.

Because if it doesn't even do that, some hardware is bricked. It could be that Memtest86+ (which is the memory testing program and is not the same as GRUB) put your RAM sticks through a stress-test and caused them to fail. If this is true, then the RAM sticks were very near failure anyway and it's a good thing you discovered the issue sooner rather than later.

Try removing one RAM stick at a time to see if that's the problem.

---

### Post by SuperIntense on 2009-03-11
Nothing comes up. I think I changed the Boot manager. Is there a way to fix this. Nothing at all comes up

---

### Post by MaxIBoy on 2009-03-11
Nothing comes up *at all?* Not even something like this:
[http://farm3.static.flickr.com/2409/2196184775_987ede884f.jpg?v=0](http://farm3.static.flickr.com/2409/2196184775_987ede884f.jpg?v=0)
[http://filedb.experts-exchange.com/incoming/2008/05_w21/27062/Award-BIOS.jpg](http://filedb.experts-exchange.com/incoming/2008/05_w21/27062/Award-BIOS.jpg)
[http://img465.imageshack.us/img465/7982/9750newsplashscren2xl.jpg](http://img465.imageshack.us/img465/7982/9750newsplashscren2xl.jpg)

In that case it's a hardware problem and you need to start troubleshooting your hardware.

---

### Post by kmac on 2009-03-11
What makes you think you changed the boot manager?

Your problem lies far before you even get to the boot manager. If it was tthe boot manager, you'd still be able to do things like booting from CD, which if you can't even get to BIOS, you probably have a bigger problem.

---

### Post by SuperIntense on 2009-03-11
I don't know! I am just guessing! All I know is it was working fine and then I ran this memory test and then I changed something in the test and now nothing. No screen, No boot up nothing. I was just trying to learn Linux. I thought it was safe installing on external drive. I did not know about the grubb boot mgr. Can anyone tell me how to get my windows to boot back up? I have an external usb sata reader if I need to take the hard drive out and put something back on it from another computer. I just want my computer back.

---

### Post by MaxIBoy on 2009-03-11
From what you describe, it looks as if your hardware failed or is having difficulties. If it's a desktop, open up the case, blow away the dust, check that all the cables are plugged in right, things like that. If you have multiple RAM sticks installed, remove one at a time,  switch them around in their slots, and so on. If you have a spare RAM stick, try that too. If it's a laptop, this might not be possible.


The computer should at least get as far as a POST, BIOS screen, or blinking cursor of some kind. If it doesn't even get that far, if the screen doesn't even light up, if computer's case lights don't blink, that means it's a hardware problem. 

Perhaps you jostled the computer and it shook something loose. Perhaps you had a lot of dust in your computer and the memory test made it work harder than usual, causing it to overheat from all the dust. I'm not sure. But this is a "nuts and bolts" problem, not a "ones and zeros" problem. Linux is pretty powerful, but it's not *that *powerful. 



For what it's worth, I'm terribly sorry that you have to deal with this crap. I've been there, and it's not fun.

---

### Post by 3l3vans on 2009-03-11
i would try unplugging your devices and re-plugging them and then boot from cd. MAYBE when you were in bios you change the boot order (i don't know the technical name) its the menu that tells the computer what order to check for boot devices. if this is the case there should be a key you can hit (its f10 on mine) while its booting that will give you a menu that will allow you to boot from cd. its usually called "boot options" or something like that.

---

### Post by SuperIntense on 2009-03-11
It was a hardware problem and unplugging everything and then reloading fixed it.

---

