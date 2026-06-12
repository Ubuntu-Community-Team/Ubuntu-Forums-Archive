---
title: "Blank Screen w/sound ...so close to fixed"
date: 2007-04-23
forum: Desktop Environments
---

### Post by jimthegenius on 2007-04-23
This is the first time I have decided to use Linux, so I don't know much about it.

Anyways, here is my  symptom: The ubuntu load screen will appear, with the loading bar and all. But when it loads to what I have now learned is the login screen (I have seen nothing pas the loading screen) the screen goes blank. It doesnt go inactive though. It just displays black. Oh and the sound still works. So I was looking aroung for a solution and found this thing about the xorg.conf. To change the display properties. So I attempted to go there, only problem was is that it was a read only and I couldnt change the defaults.
That might not solve the problem so if you have any other suggestions.
Oh and Windows only has options of 32 and 16 for color options, the default in the xorg.conf is 24... that is what I was trying to change.

---

### Post by randell6564 on 2007-04-23
>  only problem was is that it was a read only and I couldnt change the defaults.
Did you use 'sudo'?
Try opening the file with:
```
sudo gedit <name of the file>
```  
This will give you root privileges and allow you to modify text.

---

### Post by leisuretime on 2007-04-24
I too am a new...to linux in general (just installed it today).  I had no problems..easy as cake..rebooted a bunch of times. Until...

I put in an harddrive that was already formatted for Win$#@p as a storage disc, no matter what i did..I kept getting bootdisk error...blah blah..anyways...there is a serious conflict my 'puter has with my old harddrive.

so i took it out and set everything back the way I had it when I had Ubuntu 6.1 running, and now I have the exact same problem as you're saying..however, every now and again...I will see a little bit o' graphics like a Super Nintendo game gone bad.

if there's not a quick fix for this..I'll just reinstall the OS and hopefully that will fix it.

anyone else got suggestions?:guitar:

---

### Post by leisuretime on 2007-04-24
I was able to reboot in ubuntu safe mode...restarted..and walah....self fix.

I know there's something squirrelly goin' on, but no time to mess with now...crash course101

owww
:lolflag:

---

### Post by jimthegenius on 2007-04-24
Thanks randell, Ill try using the sudo command, I didnt use it last time. I should have.

---

### Post by randell6564 on 2007-04-24
> **jimthegenius said:**
> Thanks randell, Ill try using the sudo command, I didnt use it last time. I should have.
Good!  That makes me even MORE sure that you will get it!  'sudo' gives you temporary root (Administrative) priviledges. Which allows you to modify files.  But, be VERY careful because when you have 'root' access to your OS, you can do ANYTHING!  So if you don't know what you are doing, you can COMPLETELY screw-up your system!:)

---

### Post by firecrow8 on 2008-03-11
I had the same issue, the blank screen after the loading bar, and I fixed it with

noapic nolapic

it's a monitor/graphics card issue and ubuntu must be detecting the wrong one.

once I found the above commands and added the to the end of my boot string

(pres f6 at the ubuntu boot options screen add "noapic nolapic" without "")

it's worked fine

---

