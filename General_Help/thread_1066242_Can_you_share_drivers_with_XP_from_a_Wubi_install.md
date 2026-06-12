---
title: "Can you share drivers with XP from a Wubi install?"
date: 2009-02-10
forum: General Help
---

### Post by ERoe on 2009-02-10
First off, this is my first post, so hello to everyone and thanks in advance for any help you might be! Actually, I have found this forum extremely useful in the past just by browsing it, so many people here really have it together and know their stuff.

Also, a warning in advance, this will be a bit lengthy. I'm sorry, but I like people to know the whole story, and after the last three days I've just been through, venting a little doesn't hurt either.

Anyway, here's my my situation. Apologies if this is the wrong place to post, but I think it's right. I have an HP Pavillion dv6604nr (laptop), which came with Windows Vista. I decided I'd had it with Vista, and tried Ubuntu with Wubi. I really really liked it (it was my third time checking it out, but my first time really diving into it and dedicating lots of time to making myself comfortable with it, learning terminal commands, etc.), and decided I wanted to make it my primary OS.

So I back up all my data, repartition, reformat, and install it, and it works great. I love it. No problems whatsoever (that I couldn't find resolutions to here). Then it dawns on me; I use a line 6 Gear Box and Mixcraft for my home studio recording. I don't know why this wasn't something that was more important to me earlier, I think I just got caught up in Ubuntu fever. Besides, there were things like Virtualbox and Wine, and it shouldn't be a problem, right?

Well, it was. I couldn't even get my XP guest in virtualbox to see my usb devices, and even if I could have, there is enough lag that I would most likely end up with latency issues that would make recording impossible. As for Wine, same thing, latency... and that is supposing that I could get Ubuntu to see my Gear Box, which I don't think I can, despite the rumored existence of a linux driver for it. But again, even if I could, there would be latency through Wine.

Ok, I know there are possible work arounds and recording alternatives for linux users, but that's not the point. The point is as much as I love Ubuntu, I love my Gear Box and Mixcraft more, and am not willing to give them up. So I needed to reinstall Windows, and fortunately I have an old XP disc. Most UNfortunately however, the CD/DVD drive that came with my Laptop does not work, and the External usb drive I am using absolutely WILL NOT boot, no matter what the BIOS settings say. No problem. There's a way to decompile the disc image and recompile it on a bootable USB stick. Awesome.

To my point... and I know, I'm taking a long time getting there, for which I apologize, but like I said, I like people to know the whole story, not just "A+B no work, fix please." Besides, it's more entertaining this way, right?

I am now running XP as my primary OS. I have Ubuntu installed via Wubi (yes, getting relevant to the thread now), but the Nvidia driver I used while in Vista won't even install on XP. It detects XP and rolls back. What this means is that my resolution goes no higher than 1024x768, which isn't SO bad, but the reason for that is that my video card is not installed, and I am using on-board graphics, which IS really bad. Just moving a window creates trailing artifacts, and since I use a widescreen monitor, everything is out of proportion. You get the idea.

So I do a lot of searching Windows XP forums, I check out youtube (learned about XP on usb from there), and I contact both HP and Nvidia. I end up installing numerous drivers and chipsets, none of which make a damn bit of difference. I find out that because my computer was "built for vista", that my video card hardware just may not work properly with XP, even with the recommended drivers, which I find suspect, as my videocard is STILL uninstalled on windows, no matter which drivers I download and install, and Ubuntu installs and renders my video card beautifully. I haven't made up my mind whether or not I'm willing to go back to Vista or not just for that. I will pretty much only use XP for recording and mixing, so it's not THAT important, other than having less viewable work area at a time, which is a pain. But even if I DO want to go back to Vista, I pretty much can't. I deleted the recovery partition from my drive when I installed Ubuntu the first time, and the recovery discs won't run on the laptop's drive, and can't boot from the usb drive.

So after all of that... my question is, is there a way to make windows XP see, install and use the driver that Ubuntu is using? Or are they completely incompatible, since they work under different Operating Systems, even though the driver handles the same hardware?

Again, sorry for the length of my post. It IS my first post, so consider it an introduction of sorts. :)

Thank you so much for your time and for any help!!!!

---

### Post by gameover129 on 2009-02-11
potiskanje, tako lepo temo dobro delovno mesto

---

### Post by nigrunze on 2009-02-11
> **ERoe said:**
> First off, this is my first post

...
...
...

Again, sorry for the length of my post. It IS my first post, so consider it an introduction of sorts. :)

Thank you so much for your time and for any help!!!!

That is quite a lengthy first post. :o

Short answer. Windows and Linux drivers aren't compatible with each other. Otherwise, we'd be playing Linux games with Direct X and more likely OpenGL with much higher performance. There are some cases like with wireless networking drivers where you can use the windows driver in linux using ndiswrapper, but I don't think you can go the other way.

It would probably help if you told us what chipset or video card your computer has. I think there's a pretty good chance that you'll be able to find a working video driver (unlike what HP would lead you to believe since they want you to use Windows Vista which was included with the computer.

EDIT: HP's website says that your computer has a GeForce 7150M. NVIDIA has the driver for it on their website. The driver was updated today, so I don't know if the compatibility for your card came with this update or a previous one. [http://www.nvidia.com/object/geforce_notebook_winxp_179.48_beta.html](http://www.nvidia.com/object/geforce_notebook_winxp_179.48_beta.html)

Either way, if that doesn't work, you can probably still get a driver from laptopvideo2go.com . That was the old way to get up to date NVIDIA notebook drivers, but now NVIDIA provides them on their website.

---

### Post by ERoe on 2009-02-12
Thanks nigrunze, I'll try that if I end up with XP again--I got so frustrated with the whole thing that I ended up installing the Windows 7 beta and installed my drivers in Vista mode. So far, that's working out great! I had so many driver issues running XP that it's performance was actually worse than Vista, so 7 beta is a major improvement. I hate losing the space to it though, so once I learn more I might go back to XP, or try it on a new partition before getting rid of anything else, so your suggestion will be very useful then. And for anything other than recording, Ubuntu is running swimmingly :)

Thanks again, much appreciated!

---

