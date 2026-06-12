---
title: "Install Aleph One in 17.10"
date: 2017-10-30
forum: Gaming &amp; Leisure
---

### Post by tetsuo29 on 2017-10-30
I'm hoping someone out there will be able to tell me how to successfully build/install Aleph One (the open source version of Bungie's classic first person shooter from the 1990's) in Ubuntu 17.10.

I'm following the instructions on this web page:

[https://sourceforge.net/p/marathon/wiki/Linux%20Install%20Instructions/](https://sourceforge.net/p/marathon/wiki/Linux%20Install%20Instructions/)

This is something that worked just fine in 16.04.

It's during the "make" part of the process where the compiler barfs up errors and quits. I'd post the specific error but, I don't have access to my 17.10 machine at the moment. However, I hope that if you're reading this and you're on 17.10 you might take a moment to download and try and build Aleph One as part of figuring out how to successfully build it on 17.10. If you've never played the Marathon series of games, they're still a lot of fun. The graphics are what you'd expect from a game released in 1994 but, the story line, the fighting with aliens, and the 3D, walk through puzzle levels have stood up well in my humble or not so humble opinion. So, building the game for yourself might be worth your while if you end up enjoying the game. If not, I will post the specific error I'm getting once I'm back to my laptop.

Thanks in advance to anyone out there who has the skills and knowledge to troubleshoot this and provide a solution.

Also, is there somewhere where you can request that an experienced builder create a snap or flatpack (I forget which Ubuntu is using/promoting) of an app like this so that it's easier to install and run and doesn't get broken by future releases?

---

### Post by Kirboosy on 2017-10-31
Hopefully this works for you. I was able to compile it with the following.

```
sudo apt install git [COLOR=#24292E][FONT=SFMono-Regular]libboost-all-dev libsdl1.2-dev libsdl-image1.2-dev [/FONT][/COLOR][COLOR=#24292E][FONT=SFMono-Regular]libsdl-net1.2-dev libsdl-ttf2.0-dev libspeexdsp-dev libzzip-dev [/FONT][/COLOR][COLOR=#24292E][FONT=SFMono-Regular]libavcodec-dev libavformat-dev libavutil-dev libswscale-dev[/FONT][/COLOR] libsdl2-dev libsdl2-ttf-dev libsdl2-net-dev libsdl2-image-dev automake
```

```
git clone https://github.com/Aleph-One-Marathon/alephone.git
```
```
cd alephone
```
```
./autogen.sh && make -j 4
```
```
sudo make install
```

Hope that helps!
~Caboose

---

### Post by tetsuo29 on 2017-11-02
That recipe worked! Thank you so much!

---

