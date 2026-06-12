---
title: "Dell Inspiron 1525 with no sound"
date: 2009-01-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Dooghey on 2009-01-22
Hello, community!

I have a problem with my pre-installed Ubuntu on a Dell Inspiron 1525.
This problem is that for every kernel update, Ubuntu ignore the sound-card and says me, when I click on the sound icon, "You don't have the right GStreamer graft installed".

My father had solved the problem a little time ago, but I don't know how he did.
I think my sound-card is a "Intel Corporation 82801H" but I'm not sure, 'cause I not already used to text commands.

I need your help and I can answer your questions if you give me the command which explain it.

(PS: excuse my English, I'm French and it had been a long time since I wrote a text in English... ;) )

---

### Post by usstitan on 2009-01-22
Hello and welcome, I had the same problem with my dell 1525 and this is how I fixed it. Go to this [site]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade") and scroll down to the bottom on follow the instuctions. you have to do this in terminal as far as i know. Just remember to change 2.6.24-17-generic to 2.6.24-23-generic (which i presume is the latest kernal you have). Hope this helps.

---

### Post by linux_tech on 2009-01-23
what is output of :

```
cat /proc/asound/card0/codec#* | grep Codec
```

---

### Post by Dooghey on 2009-01-23
Well, *Usstitan*, my kernel is the 2.6.27-11-generic 'cause I had probably take this as an update without reading it :( 
So, how can I change to 2.6.24-23 kernel version (I have it, but I need to switch kernels)?

*Linux_tech*, the output for your command is that I don't have any file of this... maybe because I didn't update all the 2.6.27-11 kernel which is describe as "non-free Linux kernel modules". 
I think I need a change from this 2.6.27-11 kernel to the 2.6.24-23 kernel, as I said it in my answer to Usstitan.

---

### Post by Dooghey on 2009-01-24
Well, I reactualize this post, because it passed on the 2nd page and I didn't have answer which solve my problem...

So, is there anyone who know how to change kernel version...?

---

### Post by usstitan on 2009-01-25
hay sorry so long replying. mad weekend. right to change the kernal you boot up in, when you switch on the computer and after the dell logo has gone you should see a blank screen with press esc to enter the menu in the top left, so press escape before the countdown ends and that will bring up all the kernals on your pc. select the latest kernal which i think is 23 and it will boot up in that (though it should be doing that anyway) then once it's up and running put in the commands i put in the previous post. 

If the latest kernal isn't there i would check your update settings, cause it should automaticly boot to the latest kernal anyway. Hope this helps, let me know how you get on.

---

### Post by Dooghey on 2009-01-25
Hum... The command doesn't work when I'm running under 2.6.24-23 kernel version...

Does it sucks if I remove violently the 2.6.27-11 directory? O.o
Moreover, I have a "linux-restricted-modules" directory which contains some directories like "ath_pci", "wlan_ccmp"... what is this?


Sorry for all these questions, but... it drives me mad... >.<

---

### Post by usstitan on 2009-01-25
hmm, thats weird. are you getting any error message when you type in the commands?

---

### Post by Dooghey on 2009-01-25
I get the classical "no file or directory".

Running under 2.6.24-23 doesn't change anything, I lost =o=

---

### Post by pablo180 on 2009-01-26
Had the same problem when I accidentally upgraded to kernel 2.6.24-23, I spent ages trawling to find an answer but it was fairly simple to fix. 

What is the result when you type the following into a terminal?

```
uname -r
```

That is the kernel that you are currently running. 

As usstitan said press esc when at the grub menu you will probably see something like:

Ubuntu 8.04.2, kernel 2.6.24-23-generic
Ubuntu 8.04.2, kernel 2.6.24-23-generic (Recovery Mode)
Ubuntu 8.04.2, kernel 2.6.24-22-generic
Ubuntu 8.04.2, kernel 2.6.24-22-generic (Recovery Mode)

Select the one that says Ubuntu 8.04.2, kernel 2.6.24-22-generic, that is the last one that works with sound. If that still doesn't work follow the instructions on the Dell site that  usstitan linked to earlier. [Then download the new driver here]("http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/hsfmodem_7.68.00.09oem_i386.deb"). Right click and install.

You will need to uninstall all the kernel modules after 2.6.24-22-generic in Synaptic to stop it booting from them, and then untick the backports option in updates, if that is what caused the update.

That is what I did and it now works fine.

---

### Post by sumit.kalra999 on 2009-01-27
Hi,
i also faced same kind of problem in the begining on my Dell inspiron 1525,but when i perform hardware testing, i got back the sound of my laptop with 75% of its maximum level...
just perform "Hardware Testing"

---

### Post by Dooghey on 2009-01-27
@ Pablo180 : I tried once more to run under 2.6.24-23 and my sound is back, maybe some trick my laptop did me last time...
I now just need to delete packages from the 2.6.27-11... I'll try to find them, not to have to select the 2.6.24-23 every time I power my laptop...

Thank you so much, all of you! ;)

---

### Post by usstitan on 2009-01-27
Hi, glad the problem is sorted now but I am still curious why your laptop is booting up in the old kernal by default. Hmm, mystery.

---

