---
title: "No audio while viewing google video and youtube videos"
date: 2006-06-25
forum: Desktop Environments
---

### Post by Which_one's_Pink on 2006-06-25
Hello,

I have this peculiar problem. When I view videos in google videos and in youtube in mozilla (the application is macromedia flash)I can only see the video but cannot hear any sound. But I can perfectly view videos with audios while watching soccer highlights at the fifa site(the application is mplayer). Do I have to download any codecs for flash ? 

Thanks
which_ones_pink

---

### Post by Maggot on 2006-06-25
I havent check into it but I lost sound for those as well recently. It did work before.

---

### Post by Craig Caldwell on 2006-06-25
A reboot will fix the prob.
For a while.

---

### Post by Winblowz on 2006-06-25
Do this...
```
sudo nano /etc/firefox/firefoxrc
```
Then, go to where it says 

FIREFOX_DSP=

...and change it so it says

FIREFOX_DSP="none"

...then, reboot

---

### Post by bullon on 2006-06-25
i have the same problem...

mine is already set to "none" and i still have the problem, oh well...

---

### Post by bullon on 2006-06-25
fixed! i found a solution [here]("http://ubuntuforums.org/showthread.php?t=160439")

install "alsa-oss" and then open the file already mentioned:

```
sudo gedit /etc/firefox/firefoxrc
```

and change 

FIREFOX_DSP="none"

to 

FIREFOX_DSP="aoss"

restart firefox...

then open monty pythons [fish slapping dance]("http://www.youtube.com/watch?v=ZMKCLyhBBwI") to see if it worked

---

### Post by Which_one's_Pink on 2006-07-04
It worked ! Thanks a zillion !

---

### Post by harryhoudini66 on 2006-07-04
Maybe this should be made a sticky. I see it is a very common problem and it took me a bit of time to find the solution when I first installed ubuntu a week ago.

---

### Post by amunimanghi on 2006-07-05
I used this earlier, and firefox wouldn't start the next time i booted up. If that happens just type this in the terminal: ```
sudo gedit /etc/firefox/firefoxrc
``` and change aoss to auto. That fixed it for me.

---

### Post by beamo on 2006-07-09
Thanks for this thread! Changing it to "auto" fixed it for me, too. I haven't used linux since Hoary Hedgehog, which would always crash on me. I'm seeing that this version is greatly improved and has yet to have a single hiccup :D 

Except for having to run 32 bit Firefox in order to get plugins to work, and it looks like Shockwave player isn't going to work at all :| , this thing is flawless. What a great job Ubuntu has done.

---

### Post by duff on 2006-07-09
Is there an Epiphany equivilant?

---

### Post by No Whammies on 2006-07-15
> **duff said:**
> Is there an Epiphany equivilant?

How about one for Opera?

---

### Post by Grim_n_Evil on 2006-07-17
This is the fourth tutorial that does not work for me ](*,)

---

### Post by rOoNy911 on 2008-05-10
> **amunimanghi said:**
> I used this earlier, and firefox wouldn't start the next time i booted up. If that happens just type this in the terminal: ```
sudo gedit /etc/firefox/firefoxrc
``` and change aoss to auto. That fixed it for me.

I have FireFox 3 Beta 5 and i have no firefoxrc file. :S

---

