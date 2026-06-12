---
title: "D610 Wireless not working - Jaunty"
date: 2009-04-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by arepaking on 2009-04-27
Hello,
I just did a Jaunty fresh install. Everything seems to work fine except the wireless card.

Does anyone know how to properly configure it?

Thanks in advance,
AK

---

### Post by coffeeaddict22 on 2009-04-28
Hi,
Welcome!
There's a fair bit of additional information you can get about your setup, it's easiest through a terminal (Applications/Accessories/Terminal).  Open one up, and copy in the following commands (easiest way is highlight with left mouse button, paste by clicking with mddle moouse button where you want to drop the text):
```
lshw -C network
```
```
ifconfig
```
```
sudo iwconfig
```
with that, it should be easier to figure out what's not happening.  Have a look at [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo"), or post the stuff back here.

---

### Post by arepaking on 2009-04-28
> **coffeeaddict22 said:**
> Hi,
Welcome!
There's a fair bit of additional information you can get about your setup, it's easiest through a terminal (Applications/Accessories/Terminal).  Open one up, and copy in the following commands (easiest way is highlight with left mouse button, paste by clicking with mddle moouse button where you want to drop the text):
```
lshw -C network
```
```
ifconfig
```
[CODEsudo iwconfig[/CODE]
with that, it should be easier to figure out what's not happening.  Have a look at [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo"), or post the stuff back here.

Thanks Coffeeaddict, I will go through this documentation and I'll post my results.

Regards,
-AK

---

### Post by urugTON on 2009-09-18
This likely isn't going to help AK, but for those searching the forums, I'm typing this from a coffee shop with AT&T wireless.  Ok, Starbucks if you have to know.  My trusty Dell D610 is working fine from here and it has worked from two different home routers too.  

I did not have any issues with the wireless.  It worked flawlessly from the LiveCD and there were no issues once Jaunty was installed.

I have an Intel PRO/Wireless 2200BG card in my 610.

---

### Post by dabre on 2009-09-21
My D610 wireless card didn't work despite trying all the procedures I found in searches. I'm no geek so can't explain why they did not work but I eventually discovered a foolproof method.
 
Does your D610 have a bluetooth card installed? I can't remember why but I got the idea that this was the reason for problems I was having.
 
Procedure: -
1. Firstly, In BIOS setup set wireless control to Application only (not Fn+F2/App)
 
2. Boot linux
 
3. In synaptic package manager download b43-fwcutter (need to do Reload first).
When b43-fwcutter loads, you must check the box "Fetch and extract firmware" then click the Forward button.
After b43-fwcutter is finished start terminal emulator and at command line type:
"sudo ifconfig wlan0 up"
You should get no messages and the wireless LED above D610m keyboard should light up.
If you get an error then b43-fwcutter has not worked - did you check-mark the box?
 
4. Click the network icon and you should now see all the wireless networks around you.
 
You can right-click the network icon and uncheck Enable Wireless as an alternative to Fn+F2 to switch off the wireless card.
 
This worked on Ubuntu 9.04 and Knoppix.
 
Dave

---

