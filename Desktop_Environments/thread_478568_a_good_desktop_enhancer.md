---
title: "a good desktop enhancer"
date: 2007-06-19
forum: Desktop Environments
---

### Post by linux noooob on 2007-06-19
ok so i have ubuntu 7.04 and i wanted to use beryl on it but i Keep having trouble *and no one is answering my questions* so i wanted somthing simpler. so is there any kind of program like beryl but is less of a hassle.

---

### Post by JanvL on 2007-06-19
Hi,

If you are new to linux stick to KDE or GNOME.
You must first learn to handle Linux before you
start experimenting with things like Beryll.

I know it looks very nice but Linux is no windows
and that is to learn first.
You know KDE or Gnome have loads of themes to
make them look very nice.

Have fun.

Jan

---

### Post by linux noooob on 2007-06-19
i am no noob to linux dispite my name i still now the basic terminal commands and other things i am a fast learner.

---

### Post by llamakc on 2007-06-19
Are you asking good questions? Filling them with a bunch of detail? Being patient? Posting the Beryl-related questions in the Desktop Effects & Customization forum?

To answer your question you can play with stuff like transset from the repositories, or persevere with getting Beryl running.

---

### Post by evilc on 2007-06-19
> **linux noooob said:**
> ok so i have ubuntu 7.04 and i wanted to use beryl on it but i Keep having trouble *and no one is answering my questions* so i wanted somthing simpler. so is there any kind of program like beryl but is less of a hassle.

Check your other post someone is trying to help.

---

### Post by steveneddy on 2007-06-19
I have found that lurking in other Beryl posts and going to the Beryl website can do wonders for your understanding of Beryl and how to get it running correctly. 

If you are on Feisty, then it should be easier than the "old days" of Dapper.

Just read as much as you can and make sure that you take the first steps first and get the bugs worked out of each step before moving along to the next step. I have been using Beryl since, well.....for about two years and this is the method I used. Just read, read, read and then dive in.

My suggestions, for what they count towards I can't say, but never the less, here they are.

1. Get the correct video driver for your video card. I recommend an nVidia card, ATI can get hair pulling crazy to set up in Linux, and the Intel video chips and drivers leave a lot to be desired if you want a 3D desktop. If you have an Intel video chip for graphics, you might instead try 3ddesktop

```
sudo apt-get install 3ddesktop
```


2. Read and learn about xorg.conf. It can get confusing, but if you pay attention to the details and follow the directions well, it can be a breeze.

3. Once you get the driver installed and the xorg.conf file configured, THEN DL Beryl and start up your new pretty desktop.

4. Beryl is BETA software. It can break and possibly trash your desktop to the point that you can't log back in. Make another user on your PC that has admin (root) permissions just like your regular log in name just in case you need to fix something and you can't get back on.

5. Become comfortable with the CLI. You will be in that environment a few times before you get everything running properly. either write down the commands you will need perfectly, or print them out. 

6. Be patient. 

Good Luck

EDIT:

I have had good luck in the past with running an nVidia PCI video card with 128 MB RAM and it did the Beryl thing very well. Remember that the video card will need as much memory as you can afford. A 64mb card will do the job, but doubling that to 128mb will make the 3D desktop thing a little funner for you.

If you are going to install a PCI video card, please search the forums about "blacklisting" video hardware.

---

### Post by L14UX_1NS1D3 on 2007-06-19
I'm glad to see someone that is new to linux so interested in beryl because beryl is problably why he switched. Anyway about beryl, try using compiz if you still want some compositing goodness. I have a 32 mb nvidia graphics card and I was able to run compiz with almost no latency. You could even try try using Xfce, it has built it compositing so you can still get transparent windows and do some other cool things and help-wise you could there are always experienced people that you can talk to in irc rooms if you need help. There's a room dedicated to ubuntu. I think it irc.ubuntu.com. you can also browse the web for advice. Linux has such a large community that you are bound to get some answers. 
good luck with your further journeys into linux. ;) :p

---

