---
title: "Noisli not working"
date: 2014-04-07
forum: Gaming &amp; Leisure
---

### Post by riccardo5 on 2014-04-07
Hello, I would love to use Noisli ([http://www.noisli.com/](http://www.noisli.com/)) on my computer but I have not managed to do  it so far because it does not work: I can see the page properly but,  whatever feature I use, it is always completely silent (of course the  volume is not mute). I run Firefox on Ubuntu 12.04, and that might be  the problem. Is there a way to make it work also on Ubuntu? Does anyone have the same problem?
Thanks,
Riccardo

---

### Post by ajgreeny on 2014-04-07
It works for me, but it does need codecs to play mp3 files which are what download or stream from that page.

Install **ubuntu-restricted-extras** if you don't already have that package and you may be OK.

---

### Post by riccardo5 on 2014-04-07
Ok thanks, that's great. But how do I download the codecs? Could you please give me the terminal commands?

---

### Post by slickymaster on 2014-04-07
Just open a terminal window and run the following commands, one at a time:```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by riccardo5 on 2014-04-07
I've done as you wrote, but it's still not working :-(

---

### Post by slickymaster on 2014-04-07
Did **ubuntu-restricted-extras** installed successfully? Can you please post here the output of ```
apt-cache policy ubuntu-restricted-extras
``` using the code tags for the effect.

---

### Post by riccardo5 on 2014-04-07
riccardo@PC-Riccardo:~$ apt-cache policy ubuntu-restricted-extras
ubuntu-restricted-extras:
  Installed: 57
  Candidate: 57
  Version table:
 *** 57 0
        500 [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise/multiverse amd64 Packages
        100 /var/lib/dpkg/status

---

### Post by riccardo5 on 2014-04-07
I think they have been successfully installed, no?

---

### Post by slickymaster on 2014-04-07
> **riccardo5 said:**
> I think they have been successfully installed, no?

Yes, they have.

Are you able to play any MP3 files in your system?

---

### Post by riccardo5 on 2014-04-07
Yes I am! Never had problems with normal files mp3. I even contacted the developers of noisli and they couldn't understand the problem

---

### Post by slickymaster on 2014-04-07
Just guessing here, but do you have Flash Player installed? If not, install it.

You could also have a read at this: [Troubleshooting]("https://help.ubuntu.com/community/RestrictedFormats/Flash#Troubleshooting")

---

### Post by R33D3M33R on 2014-04-07
I would say firefox is outputing the sound to the wrong audio device. I suggest you install pavucontrol:

```
sudo apt-get install pavucontrol
```

Open the website in firefox and start playing, now run Pavucontrol. Under the Playback tab you will see to which device the sound is being sent and you will be able to change the device.

---

