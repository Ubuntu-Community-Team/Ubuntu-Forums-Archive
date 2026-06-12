---
title: "Mini 9 - Memory 100%"
date: 2009-06-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sdwinslow on 2009-06-07
I have also had a huge issue with the latest updates.  I am a total noob when it comes to ubuntu so I have no clue what to do.

We have the Mini9 (which of course Dell has now stopped making).  It worked like a dream until last weeks updates.  It updated to 9.04 as well as numerous other updates.  

Now we can't do anything on it.  It will not connect to our wireless network anymore.  It says our memory is at 100%.  It won't shut down unless we do the power button shut down.

We do have the 8.04 LTS disc but since the Mini9 has no drive, this puts us in a bit of a jam.  

Any suggestions on how to either a) reinstall 8.04 or b) get the contents of the disc to a jump drive and go from there.

Any help is appreciated deeply.  This was purchased as an easy way to write short stories while on the go.  Now we can't.

---

### Post by ugm6hr on 2009-06-07
If your memory use is at 100%, nothing will work.

It is likely that the updates filled your HD.

From Terminal

```
df -h
```

Post the output here.

---

### Post by sdwinslow on 2009-06-07
OK, here is what I get:

filesystem          Size      Used     Avail    Use%    Mounted on
/dev/sda2           3.4G     3.3G         0      100%      /
varrun                501M     72K     501M      1%        /va/run   
varlock               501M      0         501M     0%       /var/lock
udev                   501M      36K      501M      1%      /dev
devshm               501M       0        501M      0%      /dev/shm
lrm                      501M      1.9M    499M       1%     /lib/modules/2.6.24-24-lpia/volatile
overflow              1.0M       20K    1004K     2%     /tmp
gvfs-fuse-daemon  3.4G     3.3G        0     100%   /home/'name'/.gfvs


I hope this helps you a bit in assisting me.  I guessed that being at 100% was why things stopped working.  Also, this mini is just for writing (in open office) and internet so some things could probably go away, like the audio & video programs if they are taking up unneeded space.  Thanks already for your help.  This is my first go at an open source OS so I certainly need that leraning curve and lots of help.

---

### Post by ugm6hr on 2009-06-07
> **sdwinslow said:**
> filesystem          Size      Used     Avail    Use%    Mounted on
/dev/sda2           3.4G     3.3G         0      100%      /

That's the problem.  You have a 4GB Mini, which I think is too small for realistic use, and was a mistake to be sold by Dell like that.  The UK minimum was 8GB.

Anyway, that comment doesn't help you much.... So...

Your options:

1. Just install the new 9.04 Netbook Remix instead; it is smaller than the Dell Ubuntu 8.04, and is similar, but you will have to manually install audio / video codecs (which it appears you don't need anyway).  You may still need to take a few precautions for future updates, but I suspect that you will have much fewer problems due to the more gradual release of updates (rather than in bulk).

2. Recover your 8.04 installation, and just take a few precautions in the future.

Let me know which you would prefer, and we'll take it from there.

Either way, I'd strongly recommend using an SD card for all personal files.

---

### Post by Cowchip7 on 2009-06-07
You can also add an SD card to store documents, etc. And, as you mentions, delete unneeded programs... like webcam stuff, etc.

---

### Post by sdwinslow on 2009-06-07
That's cool.  Really meant to get the 8G but, yeah, too late for that.  Also why Dell stopped that entry level netbook....after selling a lot of them.

The Dell mini has no drive so to install anything I will have to go at it from a jump drive since I can't do it from the web.

It is running 9.04 now but maybe it wasn't the right one.  This came from with the updates.  It had been running 8.04 perfectly till then.  Again, I have that disc but no drive on the mini.

I really appreciate the help.

---

### Post by ugm6hr on 2009-06-07
> **sdwinslow said:**
> It is running 9.04 now but maybe it wasn't the right one.  This came from with the updates.

I would be surprised if it actually upgraded to 9.04; Dell controls its repositories very tightly, and has been promoting 8.04.

You can install 9.04 from a USB flash drive easily (1GB or greater).

The following will help you identify which kernel (and hence which version of Ubuntu) you are actually running.
```
uname -a
```

This can be helpful (albeit not 100% reliable)
```
cat /etc/lsb-release
```

What did you want to do - retrieve existing or start new?

---

### Post by sdwinslow on 2009-06-07
Awesome.  It IS running 8.04 which would have been what shipped with it then.  Thanks for that help.

Whatever I can do to get this taken care of I will try whatever.  I have a 4G jump drive  ready to go with whatever I need to do to.  I have seen the 9.04 netbook revision on the website but not sure how to make it all happen.

---

### Post by ugm6hr on 2009-06-07
This will get you started with 9.04 NBR:
[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

It is pretty straightforward to install - just ensure you pick "Manual" and select the largest partition to format and mount as "/" (this will make sense when you get to the relevant install screen).

Once installed, it will just work.

---

### Post by anjilslaire on 2009-06-07
You can also clean out space in your existing install  by doing the following from a terminal:
```

sudo apt-get clean
sudo apt-get autoremove

```

However, I agree with the others. Install 9.04 netbook remix, and get an sdhc card to store your data. 
I recommend the following tutorial, except use 1 big partition as noted above
[http://www.ubuntumini.com/2009/04/user-guides-for-ubuntu-904-juanty.html](http://www.ubuntumini.com/2009/04/user-guides-for-ubuntu-904-juanty.html)

---

### Post by sdwinslow on 2009-06-07
Thanks a bunch!  The sudo apt.... cleared out almost a gig (maybe about .5), which rocks but I am still wanting to install 9.04 NBR.  I have downloaded it and saved it to a stick.  

When I use the stick in the Netbook it pops up the file but when double clicking it or opening it it says there is no application to run it.

I have gone to the PPA site suggested but couldn't find the USB imagewriter to download.

Your help has been tremendous thus far and appreciated more than you can imagine.  I'm almost there.....  any help on where to go from here?

And I have already told my wife to use the USB stick to save her writing.  Even before the memory fill up.

---

### Post by sdwinslow on 2009-06-07
OK.  So I took a deep breath and figured it out!!!  WOOT!  If it wasn't for you guys today I would not have had the guts to try this.  The new OS is up and running and is actually a LOT faster than what came with it.  

The layout is different but I'll just have to show her where everything is and how to get used to it.  One thing, that isn't major, is when we connect to our network the connection bars show nothing, but it works so whatev.

Thank you very much for the help.

---

### Post by anjilslaire on 2009-06-08
Awesome, glad you got it sorted.

I'm curious: How much space is free after a clean install on 9.04 on your 4gig drive? I have it installed on a 32gig drive, but it's since been loaded with more stuff, and I never really paid attention.

---

### Post by sdwinslow on 2009-06-08
The 9.04 freed up about a gig (+/-).  I was quite pleased.  Loads and runs a lot faster as well.  The help you both gave me was priceless.

---

### Post by ugm6hr on 2009-06-08
With 1GB free, you should be OK with future updates.

Nevertheless, worth ensuring all update packages are deleted after installation:

System -> Admin -> Synaptic Package Manager
Settings -> Preferences
Files tab
Mark the "Delete donwnloaded packages after installation" box

This is equivalent to running *sudo apt-get clean* automatically after each update.

You could also uninstall some of the default Gnome stuff (e.g. games etc), but I'm not sure you'd get back an awful lot of space.

---

### Post by sdwinslow on 2009-06-08
The games may come in handy for wasting time during writer's block.  :)  I will certainly check the Delete packages after install box.  I will get more comfortable with this but you guys really helped a noob yesterday.  I went from major panic to slight annoyance to feeling great.

---

