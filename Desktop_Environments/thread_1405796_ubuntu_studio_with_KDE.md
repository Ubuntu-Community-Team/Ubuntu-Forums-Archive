---
title: "ubuntu studio with KDE"
date: 2010-02-13
forum: Desktop Environments
---

### Post by Linux&amp;Gsus on 2010-02-13
Hi all,
quick question.
I'm thinking about trying Ubuntu Studio. But I really love KDE. Since Ubuntu Studio has a low-latency kernal I guess it's better to install that version and then KDE on top of it rather then installing Kubuntu and then adding the Ubuntu Studio package.

1) Is that assumption (install order) correct?
2) What do I have to expect when I do that? What about speed, any compatibility issues with some software, etc?
3) For the occasational video and or music project would you prefer EXT3 or EXT4? Currently I have EXT4 on my Kubuntu all the way without problems. But I'm not sure if there is a advantage/disadvantage for a more video/music related use-case.

I have a 1.7GHz laptop with 1.5GB RAM. So, I know that it's not a extremely fast machine, anyway. But I'm thinking of giving that a try. Not sure of sometimes now-ish or when 10.04 comes out. Depends mainly on time.

But some answers to these questions would surely help.

Thanks all,
L&G

---

### Post by Linux&amp;Gsus on 2010-02-15
Bump?! 8-[

---

### Post by NightwishFan on 2010-02-15
You can install KDE/Kubuntu and the linux-rt kernel, then modify grub to boot the RT kernel by default, or remove the other kernel. I have never heard of any issues with Ext4 and multimedia, and I have used it for a while without issues.

The Ubuntu-Studio package will install Gnome I believe. So just find the apps you need and install them on KDE individually.

---

### Post by Linux&amp;Gsus on 2010-02-15
Hi and thanks.

The linux-rt kernel, I assume, is that "low latency kernel" that come by default with the ubuntustudio distro, right?
I roughly know what this kernel is doing and that it's is kinda needed for any audio work (video as well??). But I haven't found any info on what it means for the system in general. E.g. speed, resources needed compared to standard kernel, etc. Any siginicant difference while doing "normal" office work (documents, internet, emails, etc).

Is there even a chance that my Skype will come back to live? Currently my Skype can only chat, no audio what so ever...

Might be a stupid question, but are there any good and dummy-proof tutorials around on how to install that kernel on a stock K/Ubuntu?
When it comes to things like that I'm a total noob. I've never experimented with anything since I depend on my laptop for my everyday work.


Cheers,
L&G

---

### Post by NightwishFan on 2010-02-15
The realtime kernel is designed for audio work and other low latency tasks. It differs from the stock Ubuntu kernel in that it has a timer frequency of 1000hz instead of 250hz. That leads to better reactiveness at the expensive of a higher cpu usage. It also is patched to support kernel level preemption, which is essential to time critical tasks. In short, it will more reliably perform time critical tasks for slightly less overall performance.

You can install the realtime kernel on Ubuntu or any Ubuntu based system (such as Kubuntu) by typing this command:
```
sudo aptitude install linux-rt
```

The realtime kernel can coexist with the standard kernel and both can be installed at once. You can choose between them at boot. It is also possible to set the rt kernel as default.

As for normal work there should not be much difference. It is designed to avoid dropouts in time critical multimedia work. I do not think it will make a difference in Skype unless more precise scheduling is required.

Please feel free to ask any questions.

---

### Post by Linux&amp;Gsus on 2010-02-16
OK, was easier then I thought. After I figured out how I change GRUB to boot by default from the other kernel (I don't get a GRUB menu where I can choose, it's just booting what ever kernel is the default) it worked like a charm.

Thanks for your help and explanation about the kernel.
Now I can play around a little bit and see what I can do with all the audio goodness.


Cheers,
L&G

---

### Post by NightwishFan on 2010-02-16
Hold in shift while booting to get the grub menu.

---

### Post by lostinstarlight on 2010-02-16
Newbie alert! I've just installed UbuntuStudio and then came across an option to install kUbuntu on top of that. I did this, mainly because I like the KDE comics widget, ;) but now I'm wondering from this thread if installing kUbuntu may have messed up the UStudio latency. Do you know how I can find this out? It's already changed the very cool UbuntuStudio animated splash screen at the start of the boot-up process to a rather diminutive kUbuntu animation - any ideas what I should be looking for to change that back as well?

lis

---

### Post by NightwishFan on 2010-02-16
No, if you have installed KDE it just means you have KDE and GNOME installed, which is a bit menu messy, but otherwise fine. You may still be using the realtime kernel.

Also, to fix splash screen I think just use:
```
sudo dpkg-reconfigure usplash-theme-ubuntustudio
```

---

### Post by Linux&amp;Gsus on 2010-02-16
Holdign Shift works, thanks for that.
Learning something new everyday...  ;)


@lostinstarlight
To be sure about the kernel in a terminal type the following command:
```
uname -a
```
That gives you a little info about your installed system, including the exact kernel version you are currently running. If it says something like this:
```
Linux *your-computer-name* 2.6.31-14-generic...
```
then it seems to have changed the kernel

If it says something like this:
```
Linux *your-computer-name* 2.6.31-9-rt...
```
it should still be UStudio kernel. Notice the **-rt** at the end of ther kernel version number. To me at least that seems to indicate that the realtime kernel is running.
Someone, please correct me if I'm wrong.


Cheers,
L&G

---

### Post by lostinstarlight on 2010-02-16
Thanks for that - the kernel seems to have remained the same. I'm still getting the kUbuntu splash and now the launcher has decided to lose its options for shutdown and restart. Maybe I should just stop fiddling, but if everyone did that where would Linux be? Maybe I need to reinstall the kUbuntu desktop.

lis

---

### Post by drumkitcat on 2010-02-18
I was running Kubuntu 9.10 and UbuntuStudio 9.10 as a dual boot set up for a couple of months... after spending time working in each environment I just found that I liked UbuntuStudio better (the gnome environment) - for me it was more stable and I just liked how things worked together, flow of menu system, etc.  So I reformatted my laptop and am running only UbuntuStudio on it now.

---

