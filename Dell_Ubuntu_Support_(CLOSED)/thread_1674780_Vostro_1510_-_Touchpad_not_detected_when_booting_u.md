---
title: "Vostro 1510 - Touchpad not detected when booting up with power cable attached"
date: 2011-01-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TDK800 on 2011-01-24
Running Ubuntu 10.10 with Gnome

When power cable is attached touchpad is not detected. When removing power cable for first 5 seconds during bootup and then re-attaching, then touchpad works fine. Not using a mouse, so don't know if it is also problematic. Using generic chargers, not a Dell charger, but everything worked fine with generic chargers on Ubuntu 9.04 - 10.04.


 xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Integrated Webcam                       	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=14	[slave  keyboard (3)]



When booting up with power cable, these two are not found 90% of time, 10% of time these are somehow discovered when clicking the touchpad buttons during startup:

&#8627; PS/2 Mouse                           	id=12	[slave  pointer
&#8627; AlpsPS/2 ALPS GlidePoint             	id=13	[slave  pointer  


When booting up on battery power, touchpad is detected 100% of time.

---

### Post by syed.rakib.al.hasan on 2011-05-06
i am having the same problem here........ what is the workaround

---

### Post by mörgæs on 2011-05-07
How does it work in a live boot of 11.04?

---

### Post by syed.rakib.al.hasan on 2011-05-07
umm....... i never performed a live boot of Ubuntu 11.04 - i just upgraded from 10.10

---

### Post by mörgæs on 2011-05-07
That is often the problem. Testing before installing is the only way of knowing how it behaves on your hardware.

---

### Post by syed.rakib.al.hasan on 2011-05-07
> **mörgæs said:**
> Testing before installing is the only way of knowing how it behaves on your hardware.

well, i have been using ubuntu since 9.10....... it's not like for every release after 6 months, we download the whole ISO, then test drive it in live mode and then install........ we always UPGRADE when a new stable version is released.

and just so on the topic, my problem with **touchpad not detected** is not a reproducible problem..... sometimes it is detected during start-up....... and sometimes it is NOT detected during start-up......... if it's not detected during start-up, then i have to repeatedly restart the machine until ubuntu detects my touchpad.......... i don't think using a live test drive would have helped in understanding the problem which is not reproducible.

---

### Post by mörgæs on 2011-05-08
> **syed.rakib.al.hasan said:**
> it's not like for every release after 6 months, we download the whole ISO, then test drive it in live mode and then install........ we always UPGRADE when a new stable version is released.


Who are 'we'? 

I could never dream on anything else than a fresh install. If you take a look around in the fora these days, you will see a whole lot of problems being caused by a bad upgrade and solved with a reinstall.

Feel free to believe that an upgrade should work, and I agree with you on that. Reality is just otherwise.

---

### Post by powerofslack on 2011-05-15
Sort of defeats the point of having upgrades if they can only be used to do a clean install from scratch.  Also sort of defeats the point of having a help forum if you just use it as a place to be a know it all **** with no actual useful suggestions, Morgaes.

I have the same exact problem after maverick to natty upgrade, also occurs intermittently, will post fix here when I fix it.  I had this problem on a long ago previous upgrade on the same machine, I think from 7 to 8, and was able to find a workaround that permanently fixed it until now (which I think I didn't save a copy of the terminal from unfortunately) but I can re-fix it and then will post here.

---

### Post by powerofslack on 2011-05-15
Confirmed fix: [http://ubuntuforums.org/showthread.php?t=953995&page=2](http://ubuntuforums.org/showthread.php?t=953995&page=2)

---

### Post by Cyber Source on 2012-10-28
Thanks guys. This weird *** bug was driving me nuts and this particular laptop of my friends had a completely dead battery, so the grub kernel commands worked perfectly!
Just another example of how Linux and the Open Source Community just plain ROCK!!!!

---

