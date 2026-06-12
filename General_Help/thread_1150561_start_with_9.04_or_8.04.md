---
title: "start with 9.04 or 8.04?"
date: 2009-05-06
forum: General Help
---

### Post by trampintransit2 on 2009-05-06
IS 9.04 the place to start?
I ran 8.04 for a while on an OLD slow desktop and it was a joy, pretty much everything seemed to work. I've just put 9.04 on a family members ( up to date 'puter) and i seem to be struggling ( no flash at the moment, downloaded flash player from adobe , but still nothing) As a newbie, is it better to stick with a more established distro like 8.04 than jump in the deep end with a still being proven / written release like 9.04?

---

### Post by skymera on 2009-05-06
Jaunty has some bugs.

What is your hardware specs? (CPU, RAM, graphics card)

---

### Post by trampintransit2 on 2009-05-06
Er...foxconn kr52h, built in geforce 6150, 64bit cpu but cant remember which one? AMD athlon 64??. (I installed a 64bit version 0f 9.04) only a gig of corsair vs512mb667d2....when i say 'up to date' its all relative ;-)

---

### Post by Grenage on 2009-05-06
It'd opt for 9.04 unless you're having issues. I'm running several machines with 9.04_64 and find it to be much better.

---

### Post by bumanie on 2009-05-06
Since alpha 6, I have found jaunty to be very stable on amd 64 processor. It is quite quick too with the ext4 filesystem, which, thus far seems stable also. I have used jaunty since aplha 3 - no major issues. Of course, 8.04 has two more years of support on the desktop version - jaunty only has 18 months. I tend to think the latest versions have advantages in most cases.

---

### Post by b@sh_n3rd on 2009-05-06
Sources say that XFS is a good filesystem. There is supposed to be a bug with XFS and GRUB but my PC runs with 3 XFS partitions, /boot, /root and /home, on Jaunty. No problem so far and it's fast too. This is like the 2nd post I've read that cites Jaunty having bugs. I haven't noticed anything like that and it seems to be the best release so far, just as many others have said. The title of this post says "8.04 or 9.04", but what about 8.10? Even though it's not an LTS, It's newer than Hardy and older than Jaunty, isn't it like err...better to stay in between? But then while using it support might run out huh?...But then again Karmic would be out by October...

---

### Post by trampintransit2 on 2009-05-06
I guess its mostly cos im such a newbie. I come from windows, where things set up easily but break easily too. I find downloading and setting up a program hard. My 9.04 wont play flash content. I realised that to download from adobe, i dont even know which version to use ( .rpm, .deb, .tar.gz) how do we find these things out?

---

### Post by snowpine on 2009-05-06
> **trampintransit2 said:**
> 
I ran 8.04 for a while on an OLD slow desktop and it was a joy, pretty much everything seemed to work.

That pretty much answers the question. :)
8.04 is only 1 year old, so it is not ancient technology (compare with Windows XP which is 8 years old). So you aren't missing out on much.

Also if you stick with the "long term support" releases like 8.04, you only need to upgrade to a new release every 2 years instead of every 6 months. Less hassle.

---

### Post by snowpine on 2009-05-06
> **trampintransit2 said:**
> I guess its mostly cos im such a newbie. I come from windows, where things set up easily but break easily too. I find downloading and setting up a program hard. My 9.04 wont play flash content. I realised that to download from adobe, i dont even know which version to use ( .rpm, .deb, .tar.gz) how do we find these things out?

Actually it is much easier than that.

Open a terminal (Accessories->Terminal) and type:

```
sudo apt-get install ubuntu-restricted-extras
```

That will give you all the "non-free" stuff like flash player, mp3 playback, more fonts, etc.

---

### Post by trampintransit2 on 2009-05-06
Ok, learning slowly. But what of all this .deb, .rpm stuff , whats that all about then. Where can we idiots lear all this stuff without constantly asking questions?

---

### Post by LowSky on 2009-05-06
> **trampintransit2 said:**
> Ok, learning slowly. But what of all this .deb, .rpm stuff , whats that all about then. Where can we idiots lear all this stuff without constantly asking questions?

Google...lol

[http://ubuntuguide.org/wiki/Ubuntu:Jaunty](http://ubuntuguide.org/wiki/Ubuntu:Jaunty)

---

### Post by b@sh_n3rd on 2009-05-06
> **trampintransit2 said:**
> Ok, learning slowly. But what of all this .deb, .rpm stuff , whats that all about then. Where can we idiots lear all this stuff without constantly asking questions?

Hey now that's totally unnecessary...you don't have to call yourself an idiot for that. Even I didn't know about this stuff, but research did the job..To tell you the truth I find Linux/Ubuntu faster to learn than Winblows..:D And I'm only a linux user for 1 yr...started with Fedora which was kinda complicated. Can't even remember that stuff now :D.

Just remember, this...for Ubuntu and Debian or any other distro *based on* Debian (Ubuntu is a distro based on Debian), you need to use *.deb (see, the "deb" in "debian"?? easy! :D..rpm is tricky on the other hand...what did that stand for now??...[scanning filesystem for answers] :D)

For RedHat Linux/Fedora (as I understood, "Fedora" happens to be the desktop version for RedHat Linux), you need *.rpm (You get other distro's based on redhat too, for example: openSUSE is one)

*.tar.gz and *.tar.bz2 are archives and it's not *that* necessary to learn about those files unless you urgently wanna install a new program that isn't available in any other format.

Just in case you were hunting for a classification, I provided the above...Hope that helped...
In answer to your second question, I agree with LowSky, but you *could* also check out Wikipedia my fav. website :D.

---

### Post by snowpine on 2009-05-06
> **trampintransit2 said:**
> Ok, learning slowly. But what of all this .deb, .rpm stuff , whats that all about then. Where can we idiots lear all this stuff without constantly asking questions?

Don't be afraid to ask questions. :)

While you are learning about Ubuntu, your best bet is to install applications from the Ubuntu repositories. These are trusted applications that have been tested to work with your Ubuntu release. There are a few ways to do this--the command line terminal (using apt-get or aptitude), the Synaptic package manager, and the Add/Remove Programs application--but they all install from the same Ubuntu repository. 

Downloading random installers from the internet is kind of a "Windows" way of doing things. As you learn more about Ubuntu, you will get a sense for what is safe to install (.deb is usually okay) and what isn't. But always check the Ubuntu repositories first, because that is the safest and most reliable source for applications.

Good luck!

---

### Post by trampintransit2 on 2009-05-07
Ok guys, I'm getting better, just need to learn commands etc, just downloaded the 'ubuntupocketguide' a free PDF so hopefully its onwards and upwards. Ta muchly to snowpine and b@sh_n3rd

---

