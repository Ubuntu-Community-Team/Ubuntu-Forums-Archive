---
title: "Everything seems so slow :("
date: 2009-03-12
forum: General Help
---

### Post by pavsid on 2009-03-12
Hi, i'm pretty new to Linux so bare with me.  I first installed ubuntu about 6 months ago and for some reason it was slow. So, regrettably i went back to vista, but determined not to give in to Billy i reinstalled ubuntu. At first it seemed loads better than the last time but recently its seemed slow again, more noticable when browsing the web. I don't mean pages take ages to load - they don't - but switching between tabs, scrolling down, flash elements all seem slower than vista - the final straw was how the image effects on the [http://script.aculo.us/](http://script.aculo.us/) homepage appear - to me, they are slow, stuttered and stick, but if i load vista up on VirtualBox (on same machine) then even in that the motions are smooth and crisp - there's gotto be something wrong?!

My specs are: 
Ubuntu 8.10 Server Edition
4GB RAM
2.6Ghz AMD Dual-Core X2 Processor
nVidia 8600GT Graphics Card

Hope someone can help, it's driving me nuts!

---

### Post by wolfen69 on 2009-03-12
is there a reason you are using server edition? it is probably not optimized for general usage.

---

### Post by Neo_The_User on 2009-03-12
> **wolfen69 said:**
> is there a reason you are using server edition? it is probably not optimized for general usage.

hahaha it isn't.

---

### Post by pavsid on 2009-03-12
> **wolfen69 said:**
> is there a reason you are using server edition? it is probably not optimized for general usage.

Hi, so that i can utilise all 4 gigs - but to be honest it's not really noticeably different in desktop edition

---

### Post by Neo_The_User on 2009-03-12
> **pavsid said:**
> Hi, so that i can utilise all 4 gigs - but to be honest it's not really noticeably different in desktop edition

then use desktop

---

### Post by DeMus on 2009-03-12
> **Neo_The_User said:**
> hahaha it isn't.

How do you mean it isn't?
The Op clearly wrote:
My specs are:
Ubuntu 8.10 **_Server Edition_**
4GB RAM
2.6Ghz AMD Dual-Core X2 Processor
nVidia 8600GT Graphics Card

You really think you know it all, don't you? Well, learn how to read first and then come back.

---

### Post by Neo_The_User on 2009-03-12
i read it. just because it works doesn't mean its "optimized for general usage" kind of like how ubuntu works for me but its not i686 optimized like arch linux is. ah yeah now see? that shut you up.

---

### Post by pavsid on 2009-03-12
> **Neo_The_User said:**
> then use desktop

what i mean is there's no noticeable difference with the problems i'm having, but having 4 gigs of ram will be better when i've got two virtual machines running rather than 3.2GB

---

### Post by doas777 on 2009-03-12
I may be missing the cut of your jibb as it were, but you can use 4GB ram with a AMD64 version of ubuntu desktop.

I agree with the others, server edition + ubuntu-desktop = slow

---

### Post by Neo_The_User on 2009-03-12
> **doas777 said:**
> I may be missing the cut of your jibb as it were, but you can use 4GB ram with a AMD64 version of ubuntu desktop.

I agree with the others, server edition + ubuntu-desktop = slow

hah I knew it. YIPEE!! I'm right.

---

### Post by pavsid on 2009-03-12
> **doas777 said:**
> I may be missing the cut of your jibb as it were, but you can use 4GB ram with a AMD64 version of ubuntu desktop.

I agree with the others, server edition + ubuntu-desktop = slow

Ok, hang on, you say server edition + ubuntu-desktop? I thought it was one or the other? In any case, i only recently upgraded to server edition, the first time i installed ubuntu it was the desktop version and still had the problems??

---

### Post by doas777 on 2009-03-13
ok lets take a step back.
there are 2 main distros of any given version of ubuntu, the Desktop and the Server.
the desktop version uses Gnome (or kde or xfce) for a GUI, but the server has no gui by default, and presents only a bash interface.

so thats distros, now onto packages.
the repository package (or meta-package) for the gnome GUI used in ubuntu desktop distro, is called 'ubuntu-desktop'. 

if I install the server distro, it does not have a GUI, but I want to put a GUI on it. I run the command:
```
sudo apt-get install ubuntu-desktop
```
that will install a GUI and a host of applications like open office, evolution, transmission, rythmbox, etc.
These systems are usually slower for desktop use, because the core OS is optimized for throughput, not output.

Sorry for the vague use of langague.

---

### Post by KayakJim on 2009-03-13
If you are in a position to reinstall Ubuntu, be sure to download the Desktop edition 64-bit version (this appears below the green download button on the download page).

---

### Post by KayakJim on 2009-03-13
What does a web host have to do with a desktop system running slow?

---

### Post by muteXe on 2009-03-13
V8.04 for the win.  Seriously.

---

### Post by pavsid on 2009-03-13
> **KayakJim said:**
> If you are in a position to reinstall Ubuntu, be sure to download the Desktop edition 64-bit version (this appears below the green download button on the download page).

Ok, i'm gonna go with the reinstall with 64bit for now, otherwise i fear something inside me will take over my body and make it start using windows again, which makes me feel nauseous.

Will i have to reinstall all programs and services etc or is there an easy way to restore them in the new install?

Thanks for all your comments folks (and thanks but no thanks for the free hosting!!)

---

### Post by KayakJim on 2009-03-13
While I am sure that you could probably get away with using your previously installed programs, you would be best off to start from scratch. This is of course just my opinion.

---

### Post by linuxisevolution on 2009-03-13
Sounds like a kernel problem. When you turn on your computer quickly hit escape and choose the third or sixth option down. The kernel your using may not be optimized...

[B][SIZE="4"]You could also try to install a lighter desktop UI. For instance, install lxde. Click applications >> Accessories >> Terminal. Then type:

sudo apt-get install lxde

and hit enter. It will ask for you password, and you won't be able to see it as you type, just type it and hit enter.

Next, log out. (system >> log out) Then click "sessions" and choose LXDE. Then login.

[/SIZE][/B]
P.S: If the third option down is memtest, Try using some other kernel listed.

---

### Post by pavsid on 2009-03-13
I think i may have solved it..(for now)

It's to do with my graphics card drivers. I was using the recommended ones and read somewhere that upgrading to the latest ones off the nvidia website would solve it - and it has. Here's how:-

- download latest driver & save to /home/user/
- press Ctrl + Alt + F1   # to come out of gnome
- type sudo /etc/init.d/gdm stop   # to stop x-server
- type sudo sh NVIDIA-Linux-x86-180.29-pkg1.run (or name of file)
- follow install instructions
- type sudo /etc/init.d/gdm start    # to start x-server
- press Ctrl + Alt + F7   # to return to gnome
- or type sudo reboot    # to reboot PC

I did have some problems getting my normal display back, i think this was due to some error in the nvidia config file, but with the help of EnvyNG and reinstalling the driver a couple of times i managed to get into nvidia-settings.

I'll still be taking all your advice and scrapping server edition for 64bit though, but will wait until i get my new hard drives...

thanks to all, hope this helps any others encountering the same

---

