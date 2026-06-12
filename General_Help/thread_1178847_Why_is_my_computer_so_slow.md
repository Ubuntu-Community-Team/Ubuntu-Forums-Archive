---
title: "Why is my computer so slow?"
date: 2009-06-04
forum: General Help
---

### Post by creperum on 2009-06-04
Ever since I upgraded to Hardy, I have noticed a significant drop in the speed of my system.  Firefox and gmail seem to be the biggest culprits -- I basically can't do *anything* else while I have the gmail window open -- but in general, having more than one program running that requires *any* amount of system resources slows things down incredibly.  

Before upgrading (when I was using I think Feisty), occasionally things would slow down a bit when I ran gmail together with a couple of other programs, but since upgrading it's been much worse, to the point where I can never do more than one thing at a time, and sometimes not even that.  (Some websites that have e.g. a lot of animation take minutes to load, even if it's the only page open and nothing else is running.) 

If I run top while I have Gmail open in Firefox, there is very little (~4M) system memory listed as free, and Firefox is listed as taking up ~40% of the memory.  I am running Hardy on a Compaq Presario 2100.  I have 256M of RAM and a 20G drive, which has about 700M of free space on it.

Is this a system problem, or a Firefox problem, or something else?  ( According to [www.mozilla.com](www.mozilla.com), 256M should be adequate to run Firefox.)  Do I simply not have enough memory to run Hardy?   I realize my computer is pretty old, by computer standards, but is it too old to run the latest Ubuntu?  I have seen threads on the forums here about installing lighter systems on older computers, and I may go that route, but I want to find out if there is something wrong, or if it's just a case of "Your computer is too old and slow, you need to use a lighter system."  Because if that's the case.... well, Breezy worked pretty well, and it seems like I lose at least one feature with every upgrade.  Maybe I should have stayed back there.

Can anyone help me out?

---

### Post by dcstar on 2009-06-05
> **creperum said:**
> Ever since I upgraded to Hardy, I have noticed a significant drop in the speed of my system.  Firefox and gmail seem to be the biggest culprits -- I basically can't do *anything* else while I have the gmail window open -- but in general, having more than one program running that requires *any* amount of system resources slows things down incredibly.  

Before upgrading (when I was using I think Feisty), occasionally things would slow down a bit when I ran gmail together with a couple of other programs, but since upgrading it's been much worse, to the point where I can never do more than one thing at a time, and sometimes not even that.  (Some websites that have e.g. a lot of animation take minutes to load, even if it's the only page open and nothing else is running.) 

If I run top while I have Gmail open in Firefox, there is very little (~4M) system memory listed as free, and Firefox is listed as taking up ~40% of the memory.  I am running Hardy on a Compaq Presario 2100.  I have **256M of RAM** and a 20G drive, which has about 700M of free space on it.

Is this a system problem, or a Firefox problem, or something else?  ( According to [www.mozilla.com](www.mozilla.com), 256M should be adequate to run Firefox.)  Do I simply not have enough memory to run Hardy?   I realize my computer is pretty old, by computer standards, but is it too old to run the latest Ubuntu?  I have seen threads on the forums here about installing lighter systems on older computers, and I may go that route, but I want to find out if there is something wrong, or if it's just a case of "Your computer is too old and slow, you need to use a lighter system."  Because if that's the case.... well, Breezy worked pretty well, and it seems like I lose at least one feature with every upgrade.  Maybe I should have stayed back there.

Can anyone help me out?

Turn off Compiz, you just cannot run fat graphic apps on that hardware.

---

### Post by easybake on 2009-06-05
Changing desktop environments can drastically improve your use of system resources. You should look into trying either fluxbox or openbox. 

Everything is started by a right click menu on the desktop. I guarantee you will be surprised at the life left in your system.

You can install fluxbox in terminal

```
sudo apt-get install fluxbox
```

At your login screen choose fluxbox session.

---

### Post by Megrimn on 2009-06-05
They probably mean that 256M is *just enough* to be able to run firefox.  

Is that a laptop or a desktop?  because I think my dad has the same one, and it's a laptop...

we ended up buying a new HDD and some better RAM for it before I put Hardy on it, but I haven't been able to compile a driver for the beautiful dial-up modem, (linux is so wonderful about that) besides firefox, I could run practically anything else that came with the system.  I haven't had a chance to touch it since last summer, and my brother went and tried to put windows xp back on it, which didn't work of course.  

I digress, sorry.  If I remember correctly, Hardy alone takes up about 8gigs or more, so you really only have 12gigs left after that.  and 256M is not enough ram in this day in age.  1G is usually the lowest you want to go, 512M at the least.  

If you have the laptop I think you do, getting a cheap HDD should be no problem, just get one off ebay or newegg.com or a local store that's blowing out computer parts.  same thing with ram.  else you could save up for a new computer or volunteer to take an system off sombody's hands who decided to get a new computer...

---

### Post by markharding557 on 2009-06-05
unfortunately 256mb is not enough to run ubuntu.
you may find xubuntu a bit less demanding

---

### Post by creperum on 2009-06-05
Thanks for the replies....

> **Megrimn said:**
> If you have the laptop I think you do, getting a cheap HDD should be no problem, just get one off ebay or newegg.com or a local store that's blowing out computer parts.  same thing with ram.  else you could save up for a new computer or volunteer to take an system off sombody's hands who decided to get a new computer...

Yes, it's true.  (And yes, I have the laptop you think I do.)  I actually recently bought a new laptop, and I'm going to install Ubuntu on it as soon as I have the time.  I just hoped to be able to still use my old machine as well, since it's still in fine working condition.  (I realize this goes against computing mentality, but I see no reason to get rid of my old machine, since it still works fine.:-?)  But it sounds like I'll have to either upgrade the RAM and/or HD, or else switch to a more lightweight system.  I was thinking about switching, but wasn't sure if it was necessary...

Thanks very much!

---

### Post by boof1988 on 2009-06-05
> **creperum said:**
> Thanks for the replies....



Yes, it's true.  (And yes, I have the laptop you think I do.)  I actually recently bought a new laptop, and I'm going to install Ubuntu on it as soon as I have the time.  I just hoped to be able to still use my old machine as well, since it's still in fine working condition.  (I realize this goes against computing mentality, but I see no reason to get rid of my old machine, since it still works fine.:-?)  But it sounds like I'll have to either upgrade the RAM and/or HD, or else switch to a more lightweight system.  I was thinking about switching, but wasn't sure if it was necessary...

Thanks very much!

If you are up for a little challenge... You could start from the Ubuntu command line installation and put a lighter-weight desktop/window-manager (such as lxde) on it.  [Edit: LXDE is in the repos for Jaunty but I don't think it is in the repos for Hardy and earlier].

**To use the Ubuntu Alternate Installer CD:**
If you have an the Ubuntu Alternate Installer CD, you can choose to install (only) a command line system.  IIRC you press <F4> or one of the other "F" keys and you can choose the "Install Command Line System" option.

**To use the Ubuntu Minimal CD image:**
Get the mini.iso from one of the links [here](https://help.ubuntu.com/community/Installation/MinimalCD).  And type (IIRC)...
```
cli
```
...at the boot prompt.

Once you have installed the cli system, (and you have logged in) you can install lxde and xinit by using the following...
```
sudo apt-get install lxde xinit
```

Now type...
```
startx
```

... and you should be good to go.  This system will (should) already have:

[LIST]
[*]Network already configured
[*]A file manager installed
[*]A terminal emulator installed
[*]And some other basic necessities
[/LIST]

It can take some time to pick and install each of the additional packages that you want, but the system (when you're done) will only have the things that you want/need.

HTH

For Reference:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
[https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=003883529982892832976%3Ae2vwumte3fq&ie=UTF-8&q=minimal&sa=Search](https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=003883529982892832976%3Ae2vwumte3fq&ie=UTF-8&q=minimal&sa=Search)
[http://www.lxde.org/](http://www.lxde.org/)
[http://wiki.lxde.org/en/Main_Page](http://wiki.lxde.org/en/Main_Page)

---

### Post by mkvnmtr on 2009-06-05
Another 256Mb stick of ram will allow you to run Ubuntu just fine. It will probably cost around $20 American. You can google your unit and find a tutorial on how to install it.

---

