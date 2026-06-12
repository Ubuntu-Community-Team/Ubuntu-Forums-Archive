---
title: "Customising Gnome 3...suggestions please."
date: 2012-12-30
forum: Desktop Environments
---

### Post by oxf on 2012-12-30
Hi,

Yesterday after running Ubuntu 10.10 Maverick for some time on this laptop I did  a fresh install and switched to Precise 12.04 LTS because Maverick is no longer supported. I then installed Gnome Session Fallback because I don't like Unity. 

All went well except for one thing.... Gnome 3 does not not look anywhere near as good in my opinion. In particular the degree of customization available previously just isn't there. In fact the old Maverick installation looked much better.  I installed the Gnome Tweak Tool but that doesn't help that much. Previously I could customise all sorts of stuff under Gnome 2 like borders, here there and everywhere but not anymore. 

So is there anyway of customising this now? I'm open to any suggestions bearing in mind I'm not an expert. Unless I can come up with a significant improvement I'm giving serious thought to another DE or even another distro like Mint etc. As I said I feel this is a backward step at least in the appearance department!

Thanks

---

### Post by ibjsb4 on 2012-12-30
Here's a start

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

---

### Post by Horbo on 2012-12-30
Go back to Gnome 2? (i.e. MATE)
:p

```
sudo add-apt-repository "deb http://packages.mate-desktop.org/repo/ubuntu quantal main"
sudo apt-get update
sudo apt-get install mate-archive-keyring
sudo apt-get update
sudo apt-get install mate-core
sudo apt-get install mate-desktop-environment
```

---

### Post by zombifier25 on 2012-12-31
I'll say I prefer the GNOME 3 Classic session to MATE. MATE is unstable, and does not seem to have a very bright future.

---

### Post by oxf on 2012-12-31
> **zombifier25 said:**
> I'll say I prefer the GNOME 3 Classic session to MATE. MATE is unstable, and does not seem to have a very bright future.

But the problem is I can do very little in the way of customization, I mean when I first ever used Linux which was Hardy Heron I think, I could do more, way more than I can now. Maybe this is partly my fault for not liking Unity but I just don't.

I'm thinking of trying XFCE or LXDE but then I might as well just install Xubuntu or Lubuntu and be done with it. 

On a side note I had a older laptop that I gave to someone back in the fall. Since they were a Windows person I reformatted it and put that on it for them. But for a few weeks I ran Lubuntu on it from a flash and was rather impressed by it. A bit simple design wise perhaps but very functional and super fast.

---

### Post by zombifier25 on 2012-12-31
Have you read the link provided in the second post?

---

### Post by oxf on 2012-12-31
> **zombifier25 said:**
> Have you read the link provided in the second post?

Yes I have and I'm still digesting it. All the CLI stuff is a little advanced for me at this point bearing in mind I'm not a ubuntu geek. That said it does give me some option and hope so I'll get there in the end.

What i don't see (and yes I might be missing it) is the option to change the theme within a given window. E.G. If I open the file browser, "Places>Home> " etc the top bar of that window where the home folder/back arrow and search options are is particularly icky. I'd like to change the background colour and if at all possible the file folder/back arrow theme. Previously there was a nice up a level arrow and the whole layout was much better. I can't seem to do that now.

Maybe I am asking too much .......................................:confused:

Caitlin

---

### Post by ibjsb4 on 2012-12-31
Take a look here

[http://ubuntuforums.org/showthread.php?p=11980373](http://ubuntuforums.org/showthread.php?p=11980373)

[https://launchpad.net/nautiluspatchtogglelocationbar/+download](https://launchpad.net/nautiluspatchtogglelocationbar/+download)

---

### Post by Frogs Hair on 2012-12-31
Classic will be replaced by Gnome Shell extensions and it was never intended to be improved.The shell extensions that allow a classic look were to appease those who like the Gnome 2 look and will be included in new versions of the Gnome Shell.   

You can try the XFCE session without committing to the Xubuntu desktop. It does include its own compositing and is customizable once you know your way around . ```
sudo apt-get install xfce4 
``````
sudo apt-get install xfce4-goodies  
```  

I use currently Unity the Gnome shell and XFCE. :o

---

### Post by ibjsb4 on 2012-12-31
> **Frogs Hair said:**
> Classic will be replaced by Gnome Shell extensions

Gnome Classic will be around for the life of 12o4 (5 years of support), then maybe we move on.

---

### Post by aspergerian on 2013-01-02
I went from Ubuntu 10.04 to 12.04. Didn't like, didn't need Unity. Unity & fallback made my macine too slow. Tried Mint, then went to Xubuntu, which is working well for me, especially after I reclaimed my desktop to be much more like 10.04. [Thread here.]("http://ubuntuforums.org/showthread.php?t=2098800")

---

