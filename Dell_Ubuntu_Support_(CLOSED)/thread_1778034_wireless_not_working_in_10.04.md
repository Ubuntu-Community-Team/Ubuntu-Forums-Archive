---
title: "wireless not working in 10.04"
date: 2011-06-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rreyes3713 on 2011-06-08
I just installed 10.04 in my Inspiron 8600 so it dual boot in Window XP and Ubuntu but seems like I'm not getting any wireless signal in Ubuntu yet in XP its working fine.

One post recommend typing the following in the terminal:

sudo lshw -c network

... any other suggestions? [ as of typing this, I haven't tried the above script yet ]

---

### Post by Toz on 2011-06-08
Here is a link to a wireless troubleshooting guide that should get you started. [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")
Post back if you get stuck.

---

### Post by Toz on 2011-06-08
And...

[http://ubuntuforums.org/showthread.php?t=1765984&highlight=8600+wireless]("http://ubuntuforums.org/showthread.php?t=1765984&highlight=8600+wireless")

...in case you're laptop has the onboard BCM4306 wireless card.

---

### Post by rreyes3713 on 2011-06-08
Thanks, that helps.

I'll also try "Fn + F2"

The script "sudo lshw -c network"

=> gave me some info, identify the wireless card so that's some good news I hope.

I'm flip-flopping between XP and Ubuntu trying these scripts (lol)

I will definitely let you know how it goes.

---

### Post by rreyes3713 on 2011-06-10
Issue resolved!

This is a BCM43xx wireless card. Here's the link i used:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

... in the middle of the page tells you how to install the driver if you have no-Internet connection. You will have to download two files from the Internet so you will have to transfer these files to your Ubuntu computer. Also, you will have to have your Ubuntu CD or UBS flash drive where you will retrieve another file.

Read the direction.

Then re-boot! Wireless driver installed!

---

### Post by Toz on 2011-06-10
Great. Thanks for posting back the solution.

---

