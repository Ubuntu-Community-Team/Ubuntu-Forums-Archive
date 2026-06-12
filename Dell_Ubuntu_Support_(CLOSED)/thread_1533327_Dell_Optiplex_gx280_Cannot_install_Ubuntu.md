---
title: "Dell Optiplex gx280 Cannot install Ubuntu ?"
date: 2010-07-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by grahamz on 2010-07-17
Hello I hope I can get some help Iv been searching the forums to find a resolution for this, I have found many but none work. 

I have a DELL OPTIPLEX GX280 
320 Sata 
512
pentium 4 cpu 2.80hz

OK, here we go. 

1. I disabled the networking option in bios
2. Ubuntu cd i have does load when the pc is started , I get the Purple screen and the main install menu 
3. I have done the 

[http://ubuntuforums.org/showthread.php?t=299802](http://ubuntuforums.org/showthread.php?t=299802)

[http://ubuntuforums.org/showpost.php?p=1782230](http://ubuntuforums.org/showpost.php?p=1782230)

but i cannot get it to work still...

What I do get is, it says ubuntu for a bit then goes black with mouse visible. the pc makes a little tune 1 or 2 times then it goes to the purple screen and the mouse goes from a pointer to a clock or some sorts, back and forth back and forth.

This is driving me nuts , I am also very new to ubuntu I love it so far on my acer5070z laptop that installed like a breeze. 

Thanks in advance 

Jason

---

### Post by sidzen on 2010-07-18
Sorry, grahamz, but I know 512 MB is not enough RAM.  I have several of the same Optiplex 280 machines and recommend going to this site [http://www.mepis.org/](http://www.mepis.org/) and checking out the distro antiX-M8.5-i686.  It is a Debian-based distro and works great with our older hardware.  The forum associated is outstanding, too.

---

### Post by James78 on 2010-07-18
On a more technical note, I agree with sidzen. The only difference between your computer and mine is that I run a 3.40GHz processor, and have 4GB of RAM. Other than that there's absolutely no reason for your machine not to work with Ubuntu.

That being said, there is an alternative. You see, it takes ~700MB of RAM to bootup in a LiveCD, which is obviously more than 512MB. Because of that reason, you could download the alternate text based installer CD, and install from there, and you should be able to get your system installed that way. I however, do not guarantee your systems speed after you install it, because of the amount of RAM you have. But it should worth nonetheless.

[Alternate Download]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download"), or if you are still running Windows, you could download the regular standard CD image, stick the CD in while running Windows, and install from Windows using the [Wubi installer]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer"). I always prefer clean methods of installation, because installing from Windows puts your Ubuntu hard drive image under C:\ somewhere, and you can have problems because of Windows file fragmentation.

---

### Post by grahamz on 2010-07-18
Hey thanks for the info.....

Since yesterday i upgraded it to 1gig and still nothing ? 

I am doing a memory test now 50% done i will try the txt based system in a bit IL keep this updated..

I have seen a lot of people on the web not being able to install ubuntu on the dell 280 and its bothering me to know why. 

I really like ubuntu and the movement. Id like to help as much as possible, once i get these going..


Thanks again

J

---

### Post by grahamz on 2010-07-18
Ok.....

As i said before I have 1 GIG of memory now

I also installed a raid ata controller and hooked up a 320 serial ata 
The pc is seeing the cd drive and the drive, 
When i install ubuntu it goes well until the screen goes black and i get some music then purple screen ( the background in ubuntu desktop ) and the cursor just blinks 

So the memory isn't the problem id guess. 

so maybe might it have to do with the on board video ? 

Im just trowing things out there maybe to figure this out don't heckle me yet lol 

can somebody maybe tell me what i need set in bios maybe that's an issue ? 

j

---

### Post by grahamz on 2010-07-18
LOL the whole time, the problem was a bad write. Its the same cd I used on my laptop so I figured it work on here I guess there was a scratch on it.... Wow i feel like an idiot 

Thanks again for the help !!!!!!!

Talk to ya soon


Regards 

Jason

---

