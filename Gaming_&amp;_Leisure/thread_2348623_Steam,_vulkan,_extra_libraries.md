---
title: "Steam, vulkan, extra libraries"
date: 2017-01-05
forum: Gaming &amp; Leisure
---

### Post by The Cog on 2017-01-05
My son gave me a cast-off nVidia GTX 670 graphics card, and I thought I'd try some Vulkan stuff on it.
I'm using Xubuntu 16.10, and the proprietary nVidia 367.57 driver which I gather supports Vulkan.

I downloaded and installed the steam-installer .deb from their web site. Then the first time I tried to launch steam, it gave me the following message:
```
Steam needs to install these additional packages: 
        libgl1-mesa-dri:i386, libgl1-mesa-glx:i386, libc6:i386

```
I see no mention of Vulkan there. Does that mean that this steam install will not use the Vulkan drivers?

---

### Post by #&amp;thj^% on 2017-01-05
I found installing Steam from the Repos a better experience.
Just a heads up with Steam and Vulkan:
>  There is a known issue on Linux with NVIDIA GPUs where tearing can be observed even when vertical sync is enabled. NVIDIA is aware of the issue and it will be fixed in the future through a driver update.
Source: [http://store.steampowered.com/news/22000/](http://store.steampowered.com/news/22000/)
I have noticed a better experience using 375.26 though IMHMO
```
apt policy nvidia-375
nvidia-375:
  Installed: 375.26-0ubuntu0~gpu16.04.1
  Candidate: 375.26-0ubuntu0~gpu16.04.1
  Version table:
 *** 375.26-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status


```


When launching DOOM (Or a Vulkan Supported Game) from Steam, you'll be prompted with a new menu to choose either OpenGL or Vulkan. To play with Vulkan, select the second menu option. You can also switch between OpenGL and Vulkan in game via the Settings > Advanced > Graphics API options menu.as of Jul 11, 2016
Hope this is useful.

---

### Post by The Cog on 2017-01-05
That is useful, thank you.

I looked in the repos first using synaptic to search for "steam", but the only match was steam-devices with drivers for the Vive etc. 
So I guess the 16.10 repos don't contain steam itself. 
Correct me if I'm wrong - I would prefer to use repo packages.

---

### Post by #&amp;thj^% on 2017-01-05
> **The Cog said:**
> That is useful, thank you.

I looked in the repos first using synaptic to search for "steam", but the only match was steam-devices with drivers for the Vive etc. 
So I guess the 16.10 repos don't contain steam itself. 
Correct me if I'm wrong - I would prefer to use repo packages.

Hummm? very odd....what happens if you try from the terminal:
```
sudo apt install steam
```
You may very well be right I have not tried yet on 16.10...but it is supposed to be there.
Yep I was right:
> The package versions that were published when the distribution release was made.                  
[LIST]
[*]                     [steam 1:1.0.0.52-5ubuntu1]("https://launchpad.net/ubuntu/+source/steam/1:1.0.0.52-5ubuntu1")                     (multiverse)
[/LIST]
               
[https://launchpad.net/ubuntu/yakkety/+source/steam](https://launchpad.net/ubuntu/yakkety/+source/steam)

---

### Post by #&amp;thj^% on 2017-01-05
Well you got me curious now...so I fired up 16.10 Yakkety: 
And:
```
sudo apt install steam
```
And this is what I got:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  gcc-6-base:i386 libbsd0:i386 libc6:i386 libdrm-amdgpu1:i386
  libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386
  libedit2:i386 libelf1:i386 libexpat1:i386 libffi6:i386 libgcc1:i386
  libgcrypt20:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:i386
  libglapi-mesa:i386 libgpg-error0:i386 libllvm3.8:i386 libpciaccess0:i386
  libstdc++6:i386 libtinfo5:i386 libtxc-dxtn-s2tc0:i386 libudev1:i386
  libx11-6:i386 libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386
  libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386 libxcb-sync1:i386
  libxcb1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386
  libxinerama1:i386 libxshmfence1:i386 libxss1:i386 libxxf86vm1:i386
  zlib1g:i386
Suggested packages:
  glibc-doc:i386 locales:i386 rng-tools:i386 steam-devices:i386
The following NEW packages will be installed:
  gcc-6-base:i386 libbsd0:i386 libc6:i386 libdrm-amdgpu1:i386
  libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386
  libedit2:i386 libelf1:i386 libexpat1:i386 libffi6:i386 libgcc1:i386
  libgcrypt20:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:i386
  libglapi-mesa:i386 libgpg-error0:i386 libllvm3.8:i386 libpciaccess0:i386
  libstdc++6:i386 libtinfo5:i386 libtxc-dxtn-s2tc0:i386 libudev1:i386
  libx11-6:i386 libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386
  libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386 libxcb-sync1:i386
  libxcb1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386
  libxinerama1:i386 libxshmfence1:i386 libxss1:i386 libxxf86vm1:i386
  steam:i386 zlib1g:i386
0 upgraded, 43 newly installed, 0 to remove and 0 not upgraded.
Need to get 22.4 MB of archives.
After this operation, 190 MB of additional disk space will be used.
Do you want to continue? [Y/n] 

```
I would also think these might be needed :
```
Suggested packages:
  glibc-doc:i386 locales:i386 rng-tools:i386 steam-devices:i386

```
And now I show:
```
apt policy steam
steam:i386:
  Installed: 1:1.0.0.52-5ubuntu1
  Candidate: 1:1.0.0.52-5ubuntu1
  Version table:
 *** 1:1.0.0.52-5ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu yakkety/multiverse i386 Packages
        100 /var/lib/dpkg/status

```
Best Regards:)

---

### Post by The Cog on 2017-01-05
That's really odd. On this laptop (steam not installed) I can see steam there with "sudo apt search steam" and "sudo apt install steam" but I cannot get synaptic to show steam in its search results. Some kind of hiccup with synaptic perhaps.

I'll go back to my desktop tomorrow, try to uninstall the downloaded steam package and then install the repo version.

---

### Post by #&amp;thj^% on 2017-01-05
Yes I agree with synaptic on 16.10...a bit buggy here also.:(
I hope they are not trying to gradually do away with it.
I had to change this to make it work from the unity launcher
```
sudo -H gedit /usr/share/applications/synaptic.desktop
```
And Change line "Exec=synaptic-pkexec" to "Exec=gksudo synaptic"
Maybe useful to future visitors.

---

### Post by The Cog on 2017-01-06
I'm on Xubuntu, and no problems launching synaptic. 
I removed the downloaded steam installer and installed steam using apt instead. That seemed to go OK. 
I installed one free game (Sigils of Elohim) but it won't start. There's a small "Preparing to start..." window for maybe quarter of a second and that's it.
I don't know if there are logs anywhere or any way to find out what went wrong.
I'm not going to buy a game if steam can't start anything, so I guess that's Game Over. Oh well.

---

### Post by The Cog on 2017-01-06
I'm on Xubuntu, and no problems launching synaptic. 
I removed the downloaded steam installer and installed steam using apt instead. That seemed to go OK. 
I installed one free game (Sigils of Elohim) but it won't start. There's a small "Preparing to start..." window for maybe quarter of a second and that's it.
I don't know if there are logs anywhere or any way to find out what went wrong.

When I try to run steam from the command line, I get this:
Unable to remove /home/steve/.steam/CONFIG/SteamAppData.vdf!
Hardly surprising, as /home/steve/.steam does not contain a CONFIG folder.
Anyway, it carries on, and when I try to launch the game it says:
```
Found path: /home/steve/.steam/steam/steamapps/common/Sigils of Elohim/Sigils.x86
Mono path[0] = '/home/steve/.steam/steam/steamapps/common/Sigils of Elohim/Sigils_Data/Managed'
Mono path[1] = '/home/steve/.steam/steam/steamapps/common/Sigils of Elohim/Sigils_Data/Mono'
Mono config path = '/home/steve/.steam/steam/steamapps/common/Sigils of Elohim/Sigils_Data/Mono/etc'
```
That's all.

I'm not going to buy a game if steam can't start anything, so I guess that's Game Over. Oh well.

---

### Post by #&amp;thj^% on 2017-01-06
This looks promising if you have not grown weary of steam: [https://github.com/ValveSoftware/steam-for-linux/issues/4559](https://github.com/ValveSoftware/steam-for-linux/issues/4559)

The Post by LexBarringer
It starts out:
> The folder and file in question isn't really the issue here, I use Ubuntu 16.04 (Xubuntu desktop). First off, the reason why it can't delete it as you stated the file doesn't exist in that folder, which is actually nothing more than a soft error; a warning.

The CONFIG folder doesn't exist; this is because, "CONFIG" and "config" and "Config" on Microsoft Windows are all the same folder but on the *NIX and Linux they're completely separate folders. This is just an oversight and remnants from a Microsoft Windows build that should have been omitted for the Linux and Apple OS X.

Now, I will speak to the problem as to why your system may not bootstrap Steam due to the stdc++.so.6 files from within the Steam path. The symbolic links that are in the directory are wrong for anything beyond Ubuntu 12.04 (or forks) and especially for the x86_64 edition and beyond.

This is what I do anytime I have to do a new install on the computers with Steam.

```
cd $HOME/.steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu
rm libstdc++.so.6
cd $HOME/.steam/ubuntu12_32/steam-runtime/amd64/usr/lib/x86_64-linux-gnu
rm libstdc++.so.6
```

This is actually a very well known problem in the Ubuntu and forks communities as is the fix. All the above does is get to the directories in question and delete (remove) the symlink file and then Steam will use the system libraries under the same name.
Fingers Crossed

---

### Post by The Cog on 2017-01-11
Thanks for the advice to remove those links. 
I found the links in a different place, but removing (actually, renaming them) did the trick.

My actual commands to fix it were:
```

cd ~/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/usr/lib/x86_64-linux-gnu
mv libstdc++.so.6 ZZlibstdc++.so.6
cd ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu
mv libstdc++.so.6 ZZlibstdc++.so.6

```

---

### Post by oldrocker99 on 2017-01-11
Since the problem is solved, please use the Thread Tools in the upper right-hand corner to mark this thread as [SOLVED.]

Thanks.

---

### Post by oldrocker99 on 2017-01-11
By the way, The Cog, both your URLs are bad; the first gives an "Account Suspended" result, and the second gives a "Video is unavailable."

Just sayin'.

---

### Post by The Cog on 2017-01-11
> **oldrocker99 said:**
> By the way, The Cog, both your URLs are bad; the first gives an "Account Suspended" result, and the second gives a "Video is unavailable."

Just sayin'.

Shame. I hadn't heard anything of them for a while. I guess they've disbanded. 
Students. They were very good.

---

### Post by #&amp;thj^% on 2017-01-12
> **The Cog said:**
> Thanks for the advice to remove those links. 
I found the links in a different place, but removing (actually, renaming them) did the trick.

My actual commands to fix it were:
```

cd ~/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/usr/lib/x86_64-linux-gnu
mv libstdc++.so.6 ZZlibstdc++.so.6
cd ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu
mv libstdc++.so.6 ZZlibstdc++.so.6

```
Hey that's great...Happy gaming.;)
BTW have you had a chance to test the Vulcan option yet?
Just curious.

---

### Post by The Cog on 2017-01-12
> **1fallen said:**
> Hey that's great...Happy gaming.;)
BTW have you had a chance to test the Vulcan option yet?
Just curious.
No. The only 2 Vulkan + Linux games I know about are Dota2 and The Talos Principle. 

Dota2 is free but is really not my kind of thing at all. It's a big download and I have to play (terribly incompetently) against someone else just to see if the game works. And I know I would uninstall it again within minutes of trying it.

The Talos Principle looks interesting, but it's anything but free (I'm sure when I first read about it, it was free), and I don't want to spend that much just to find out it doesn't work on my machine after all. A demo version would have been a comforting starter.

---

### Post by #&amp;thj^% on 2017-01-12
> **The Cog said:**
> No. The only 2 Vulkan + Linux games I know about are Dota2 and The Talos Principle. 

Dota2 is free but is really not my kind of thing at all. _**It's a big download and I have to play (terribly incompetently) against someone else just to see if the game works.**_ And I know I would uninstall it again within minutes of trying it.

Oh Brother do I understand that....for me I have not been much of a Gamer (through the years) so I get frustrated at my lack of skills here. :lolflag:
Best Regards

---

