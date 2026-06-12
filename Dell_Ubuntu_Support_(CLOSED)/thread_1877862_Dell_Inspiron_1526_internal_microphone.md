---
title: "Dell Inspiron 1526 internal microphone"
date: 2011-11-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Kazuki Mishima on 2011-11-08
I have searched forums and documentation high and low, have tried installing various sound managers, editing my ALSA configuration file, and investigating every possible combination of possibly-relevant-seeming settings, but I have so far been unable to use my Dell Inspiron 1526 laptop's internal microphone on 64-bit Lubuntu 11.10. I was once able (under previous versions of 64-bit Ubuntu) to make the microphone available as an input source just by adding a line to alsabase.conf, but that no longer works.

Any ideas, anyone? Should I consider the possibility that this is a hardware issue? Should I buy a USB microphone and hope that it's compatible? (I've had my eye on the Samson Go, but I've no idea whether I could actually use it through Lubuntu or not.)

---

### Post by Rodney9 on 2011-11-08
This may be of help - [http://blip.tv/ubuntu-switcher/lubuntu-screencast-alsamixer-5559414](http://blip.tv/ubuntu-switcher/lubuntu-screencast-alsamixer-5559414)

If not, ask here and someone hopefully can help - [http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)
have a look at this site anyway it has plenty of tips for Lubuntu.

I use a set of Logitech PC Headset 120's with Lubuntu on my laptop, work perfectly with skype

Rodney

---

### Post by Kazuki Mishima on 2011-11-08
Thanks for the links. Tried alsamixer again, and the result was the same as always: there is no microphone volume setting for me to edit. The closest is a setting called "Front Mic Jack Mode," which is not a volume setting at all, but rather a setting with three options: "Mic In," "Line In," and "Line Out." Tinkering with this setting gets me nowhere. I installed gnome-alsamixer from the repositories, but running it produces only a segmentation fault. I didn't find anything about microphones on that Lubuntu thread, alas.

EDIT: I did try raising and lowering volume of the "Capture" and "Digital" input fields as well. The "Digital¨ field does produce some sound that I can record via Audacity, but it's nothing but white noise. The "Capture" field, though it is unmuted and at full volume, produces nothing, as do the "Capture 1" and "Capture 2" fields.

---

### Post by Rodney9 on 2011-11-09
I suggest you post this problem here for other Lubuntu users to see -   

Lubuntu One Stop Thread - 

[http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)


Also have you looked here -

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Rodney

---

