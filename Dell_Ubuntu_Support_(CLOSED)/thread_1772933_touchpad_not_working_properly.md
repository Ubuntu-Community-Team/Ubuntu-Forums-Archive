---
title: "touchpad not working properly"
date: 2011-06-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by netopalis45 on 2011-06-01
I have a Dell Inspiron 1501 laptop with Ubuntu 11.04 installed. When I am at the login screen my touchpad works just fine but as soon as I log in the touchpad stops working. As far as I can tell, I have not turned it off so I am not sure what is going on. Any ideas?

---

### Post by maverick280857 on 2011-06-02
I had a similar problem on my Dell XPS 15. Try installing touchpad-indicator. It indicated that my touchpad was turned off.

---

### Post by netopalis45 on 2011-06-02
Thanks for the tip. Unfortunately I could not install touchpad-indicator (apt-get could not find it) but I did manage to install synaptiks and that fixed the toucpad immediately.

---

### Post by jonasbdotcom on 2012-04-08
> **netopalis45 said:**
> Thanks for the tip. Unfortunately I could not install touchpad-indicator (apt-get could not find it) but I did manage to install synaptiks and that fixed the toucpad immediately.

I know it's a bit late - but somebody might search for the topic and get to this post.

According to Ubuntu.com you can do it by doing this.

```
sudo add-apt-repository ppa:atareao/atareao
sudo apt-get update
sudo apt-get install touchpad-indicator
```

Source: [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

### Post by rahul_lav on 2012-08-02
try:
echo "options psmouse proto=imps"|sudo tee -a /etc/modprobe.d/psmouse.conf; sudo modprobe -r psmouse; sudo modprobe psmouse

works for me

---

### Post by katoiam on 2012-08-08
Hello,

Looking for help!

I tried the command above. It worked to a degree. Previously I had no right mouse click, which I now have and before it was overly sensitive and didn't enjoy having a finger touching on the right and left click areas.

Now it works but I have lost multi touch and synaptics claims I don't have a touchpad!

Can any one help?


touchpad-indicator
#####################################################
No LSB modules are available.
#####################################################
Distributor ID: Ubuntu
Description:    Ubuntu 12.04 LTS
Release:        12.04
Codename:       precise
Version:        x86_64
#####################################################

Touchpad-Indicator version: 0.9.3.10
#####################################################

xinput list
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Synaptics TouchPad                   id=12   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Power Button                              id=8    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=9    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_1.3M             id=10   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=11   [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                          id=13   [slave  keyboard (3)]


I have the new dell xps15 

cheers,

---

### Post by abugabbu on 2012-08-10
For XPS editions, you need a kernel update as CyPS/2 Cypress Trackpad is the original driver. So, you can easily install that with the steps mentioned here:
```
http://www.techjail.net/solved-dell-xps-1315-problem-brightness-single-tap-touch-scroll.html
```

And as the Original poster told, I guess the problem is with you might have disabled the H/w from the Windows system and might not have worked with Ubuntu

---

### Post by katoiam on 2012-08-10
thanks abugabbu,

unfortunately that didn't do anything! synaptiks still doesn't see my touchpad. This patch seems to be for the previous xps editions not the newer ivy bridge ones. I believe the xps13 that this patch was made for is the previous edition.

I was sure the hardware wasn't turned off in wondows as I rarely use winblows, but checked none the less, and it was fine.

The problem started when I ran the command:


echo "options psmouse proto=imps"|sudo tee -a /etc/modprobe.d/psmouse.conf; sudo modprobe -r psmouse; sudo modprobe psmouse


like I said previously it helped in a way, but now synapiks recons I don't have a touchpad, so no multi touch etc.

I guess that what I get for using command with out know what they are doing!

any on know how to reverse what the command did?

cheers

---

