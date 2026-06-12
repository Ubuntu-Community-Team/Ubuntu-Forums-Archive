---
title: "How to disable gnome responding to my IR remote control?"
date: 2011-02-06
forum: Desktop Environments
---

### Post by upgrdman on 2011-02-06
I have a StreamZap IR remote control and receiver. It is setup with LIRC and I use it with MythTV. Around a year ago some update caused Gnome to respond to a few of the remote's button presses.

For example, using the volume buttons on my remote will have the same affect as using the volume buttons on my keyboard, or playing with the panel applet.

It didn't do this before, and I liked it that way. But I see no way to disable Gnome's responses to my remote. Any ideas? I tried Googling to no avail.

-Farrell

---

### Post by gamhead on 2011-02-24
Im trying to understand what is driving the gnome volume controls as well.. Ive removed my .lircrc etc.. Please share anything you find, and Ill do the same :)

---

### Post by semler on 2011-03-12
See 

[http://wiki.xbmc.org/index.php?title=Streamzap_PC_Remote#Xinput:_Preventing_Streamzap_from_becoming_a_keyboard]("http://wiki.xbmc.org/index.php?title=Streamzap_PC_Remote#Xinput:_Preventing_Streamzap_from_becoming_a_keyboard")

Henning

---

### Post by upgrdman on 2011-03-15
semler: Thank you! I have been asking around for a while now and could not figure it out. It did not dawn on me that X could be the culprit.

-Farrell

---

### Post by guyrichie@hotmail.com on 2011-12-04
Hello All,

I've had a similiar issue with my Windows Media Centre remote control.  As described above Xorg saw my remote as a keyboard input device.  This was an issue for me as I assign my power button to launch XBMC or MythTV within gxmessage and every time the Gnome shutdown option window appeared in addition.

to resolve this I modified the above solution to suit the MCE remote I have.

in a terminal:

$ xinput list #locate the exact product name Xorg saw my remote as.

$ sudo gedit /usr/share/X11/xorg.conf.d/90-mce_usb.conf

copy and paste the below into gedit substituting MatchProduct for my remote as per xinput list output

Section "InputClass"
  Identifier "Ignore MCE_USB as Keyboard input"
  MatchProduct "Media Center Ed. eHome Infrared Remote Transceiver (147a:e017)"
  MatchIsKeyboard "true"
  Option "Ignore" "true"
EndSection

Save, reboot.

It is possible to deactivate just certain buttons rather than the whole remote - see: [https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input) for good reading

Cheers.

---

### Post by gamhead on 2011-12-04
Not particularly useful but I just want to share that I ended up going back to Windows 7.. suddenly frame rates are high in Flash, things just work, UI is nice.

Unity pushed me well over the edge, sorry! :lolflag:

---

### Post by Kissell on 2012-03-13
It was very much useful to me...  I've been messing with this forever, probably have over 40 hours invested in trying to get my IR remote to work in Ubuntu 11.10...  nobody would respond to my forum posts about it...  and this was it...  Xorg was taking it so LIRC couldn't use it.  

I also had to change the ir-keytable protocol to the Japanese NEC standard (for the old Apple A1156 white remotes).  

Wow, been messing with this forever and finally came across this thread, you really helped me out a lot.

---

### Post by Kissell on 2012-03-14
well crap, this works on my laptop now, thanks to that trick of editing xorg.conf to tell it to ignore the IR receiver...  

But now I can't get it to work on my desktop computer...  I did all the same stuff, I think...  but same problem as before, "irw" doesn't recognize any button presses, even though "ir-keytable -t" and "irrecord" do...  but I have xorg ignoring the receiver on this computer, and verified that with "xinput list"...  so I'm still stuck...  

I got it to work on the laptop because it was more comfortable to work in another room..  now I'm trying to get it to work on the actual computer I need it on, and am completely stuck and have no idea why..  copied all the config files over from the laptop and still nothing...  must be missing something I did somewhere...

---

