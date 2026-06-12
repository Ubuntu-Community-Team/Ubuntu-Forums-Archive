---
title: "Speakers and headphones are working together"
date: 2013-08-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by CHANGALRAYUDU on 2013-08-19
Hello  this  is rayudu


my new laptop has preinstalled ubuntu 12.04 lts .my built in speakers are working fine. At the same time headphones are also working fine.
When i connect my headphones volume not muted in built in speakers. Volume not controlled when i plugged in headphones. I am receiving sound from built in speakers and headphones togethers.

There is some distrubances to others by these kind of things.

And my laptop is dell vostro 2520


please provide any solution for this .........


Thanks for the answers

---

### Post by papibe on 2013-08-19
Hi CHANGALRAYUDU. Welcome to the forums ):P

Could you open a terminal, run these commands, and then paste the results in another post?
```
lsb_release -a

uname -a

lspci -nnk | grep -iA2 audio
```
Regards.

---

### Post by Gilad_Pellaeon on 2013-08-19
If your dell laptop is anything like my older dell optiplex 745 desktop I had to actually go into the ALSA mixer settings in Lubuntu and turn down the Mono bar to 00 to turn off the internal speakers. I do not know if Ubuntu with the unity interface can access or has this same Alsamixer or not but that was how I disabled the internal speakers so I could listen to music and watch videos in peace on my headphones without disturbing the misses lol. :) Left and right arrow keys to move and up/down arrow keys to adjust.


[IMG]http://u.cubeupload.com/Pellaeon2/alsamixerdelloptiple.png[/IMG]

---

### Post by CHANGALRAYUDU on 2013-08-20
Thankyou for your reply.

i just run those commands in terminal and the results are

bcr@bcr-Vostro-2520:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise


bcr@bcr-Vostro-2520:~$ uname -a
Linux bcr-Vostro-2520 3.2.0-51-generic #77-Ubuntu SMP Wed Jul 24 20:18:19 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


bcr@bcr-Vostro-2520:~$ lspci -nnk |grep -iA2 audio
00:1b.0 Audio device [0403]: Intel Corporation Panther Point High Definition Audio Controller [8086:1e20] (rev 04)
    Subsystem: Dell Device [1028:0558]
    Kernel driver in use: snd_hda_intel

These are the results when i run those commands. First time i am using this Operating System and  i am very Naive user for this OS.

Thanks in advance....

---

### Post by papibe on 2013-08-20
Thanks.

Open a terminal, copy this command and run it:
```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```
Then restart your machine.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by CHANGALRAYUDU on 2013-08-20
Thankyou for u r reply

It works fine for me.....:smile::smile: 

Thanks again ...........

---

### Post by papibe on 2013-08-20
Great! :D

Please mark the thread as SOLVED when you have chance ([here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")'s how to do it).

Come here often and have fun.
Regards.

---

### Post by Shabeeb_Khan on 2013-09-05
Hi,

I tried this but no luck still the same

---

### Post by Jessica_Perrie on 2014-03-24
> **Gilad_Pellaeon said:**
> If your dell laptop is anything like my older dell optiplex 745 desktop I had to actually go into the ALSA mixer settings in Lubuntu and turn down the Mono bar to 00 to turn off the internal speakers. I do not know if Ubuntu with the unity interface can access or has this same Alsamixer or not but that was how I disabled the internal speakers so I could listen to music and watch videos in peace on my headphones without disturbing the misses lol. :) Left and right arrow keys to move and up/down arrow keys to adjust.


[IMG]http://u.cubeupload.com/Pellaeon2/alsamixerdelloptiple.png[/IMG]

I was having the same issue as the OP, and this solution solved it. Thanks!

---

### Post by Gvi9 on 2014-04-07
i too have same problem please help me out

---

### Post by Gvi9 on 2014-04-07
i have tried above given commands but its not working 

please help me out 

thanks in advance

---

