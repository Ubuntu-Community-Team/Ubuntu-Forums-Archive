---
title: "digital camera"
date: 2005-12-26
forum: General Help
---

### Post by BruschiOnTap on 2005-12-26
Ok, I got a digicam for Christmas and I just switched to Linux over WinXP last week.  You probably already see my problem coming: it's only meant to work with Windows or Mac.  Do I download the drivers from the manufacturer's website?  And if so, how do I load them up via my terminal?  (I'm VERY green... Kyral's Terminal for Beginners thread has been very helpful)

thanks to all who can help!

---

### Post by Dr. Nick on 2005-12-26
I assume you mean a digital still camera, not a video camera? My still camera doesnt require any drivers (Olympus) The majority of them today seem to use the generic "Usb mass storage" which will work in any os that supports it, linux included even though not mentioned on the supported OS list all of the time.

Have you tried to use it yet? You may be surprised and have it work without any problems. The only brand of camera that may not work is kodak or sony, They may work as I have never used one so cant tell for sure. It wouldnt surprise me though if either of them made a propriteary method of picture transfer though.

If it doesnt work automatically post a brand and model number and you can probably get some help.

---

### Post by Zotova on 2005-12-26
[QUOTE=Dr. Nick]The only brand of camera that may not work is kodak or sony[/QUOTE]

My sony appears as a removable driver without the need for any tweaking or drivers. So I can confirm that sony cameras (well at least my model) work fine with Linux.

---

### Post by Dr. Nick on 2005-12-26
[quote=Zotova]My sony appears as a removable driver without the need for any tweaking or drivers. So I can confirm that sony cameras (well at least my model) work fine with Linux.[/quote]

Cool thats good to know, I know some kodak cameras and maybe others have some sort of docking station to plug the camera into for transfers, thats what would make me think that it could possibly be a propriteary method.

---

### Post by rfruth on 2005-12-26
My Canon A60 (read old) works fine no driver needed :)

---

### Post by BruschiOnTap on 2005-12-27
Thanks guys!  I'm gonna go give it a try later on today.  Although... my USB memory stick has to always be mounted manually.  I don't even remember the command line stuff for that (like I said, I'm green!).  Erego, I think I will have to mount the camera as though it were an external hardware device (which it technically is).  Anybody wanna give me a command line hint or two?  you can also email me at [email]porklife@gmail.com[/email]

Again, thanks and I hope you don't mind answering more of my questions in the future.

---

### Post by Dr. Nick on 2005-12-27
[quote=BruschiOnTap]Thanks guys!  I'm gonna go give it a try later on today.  Although... my USB memory stick has to always be mounted manually.  I don't even remember the command line stuff for that (like I said, I'm green!).  Erego, I think I will have to mount the camera as though it were an external hardware device (which it technically is).  Anybody wanna give me a command line hint or two?  you can also email me at [EMAIL="porklife@gmail.com"]porklife@gmail.com[/EMAIL]

Again, thanks and I hope you don't mind answering more of my questions in the future.[/quote]

It should just appear as a link on your desktop, If it doesnt then look under /media in nautius and maybe a folder called usbdisk. 
here is a thread talking about accessing if not auto mounted
[http://www.ubuntuforums.org/showthread.php?t=89854&highlight=mount+digital+camera](http://www.ubuntuforums.org/showthread.php?t=89854&highlight=mount+digital+camera)

I never have needed that though

---

### Post by 504harry on 2005-12-27
Before  you get too involved make a start with a filing system, so you can find those pics in a year's time.At least a folder: "Pictures_Jan_2006"
I agree with what others say - just connect it as USB and it should appear on desktop. click on the icon and I think you will see files. Copy Paste.
//
Gimp is a PhotoShop lookalike and although the icons are a tad odd (and small), once you load a picture, the tools appear. Just don't write files back to the camera.....that's why it's best to copy them to HDD first. Note too, that  true Gimp files can get quite large - 50MB is quite average. There is a Gimp manual available (from Gimp) which goes through the finer points.
I've never had any success with printing from Gimp - HP and Epson seem to be the best choice. Mine's Lexmark, sad.
Good Luck.

---

### Post by BruschiOnTap on 2005-12-28
Ok, I tried plugging it in and noting recognized it.  I tried mounting it as a USB drive in the terminal and it said it couldn't find any USB drives.  I looked around through my dev file for sda1 and there was nothing labelled sda at all.  I'm very confused.  digikam and gtkam could not find a camera although one had driver information for Oregon Scientific cameras, just not this model.  

I expected to have difficulties with it but even my friend who is quite familiar with ubuntu is baffled...

---

### Post by d11wtq on 2005-12-28
```

mkdir /media/camera
mount /dev/sda1 /media/camera   (Change "a" and "1" to the correct device)
ls /media/camera

```

---

### Post by tmeier on 2005-12-28
Have you installed GTKam?  I have a Kodal Z700 that I received about a week ago.  I installed gtKam using Synaptic Package Manager.  I hookedup my camera and it opened GTKam and asked what I wanted to do with the pictures on the camera.  

Find Synaptic in your Menus at "system-administration-synaptic package manager.  
You may have to add the multiverse or universe repositories to get gtkam to show up.  Do a search in the forums on how to add the multiverse or universe repositories.

---

### Post by BruschiOnTap on 2005-12-29
ok I tried that command line but I'm not sure what the device would be called besides sda1... you'll have to elaborate on that for me, I'm sorry... what else would it be?

I also tried GtKam and it can't find a camera even when it's there to detect it.  The camera is plugged in and turned on, receiving a charge through the USB but nothing else...

---

### Post by tmeier on 2005-12-29
Is the camera on in PLAY mode?  I know this is kind of basic and don't intend on insulting your intelligence, but also want to cover all the bases to make sure were not missing something easy.  I have had someone do that in the past, where they had the camera on in picture mode and not in play mode(so the pictures can be viewed on the little lcd screen).  Keep searching someone will find the answer yet.

---

### Post by BruschiOnTap on 2005-12-29
oh it's not video, it's a little stillshot camera made to the size of a credit card.  Now I have noticed that my computer doesn't seem to like mounting anything from the usb drive automatically which is really frustrating considering everyone tells me it's supposed to...

---

### Post by thespazzz on 2005-12-29
I also got a digital camera for christmass and it works fine in Ubuntu (Even though the documentation said it absolutly would not support anything other than windows).  Actualy what I want to know is is there anyway I can write a script or batch file that I can launch that will automaticly transfer photo's off the camera rename them something unique and maybe delete the pictures on the camera.  I keep loosing things because they're named the same when I transfer them and i'm a moron and keep hitting overwrite.

---

