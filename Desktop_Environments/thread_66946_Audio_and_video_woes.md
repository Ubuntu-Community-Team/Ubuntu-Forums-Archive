---
title: "Audio and video woes"
date: 2005-09-18
forum: Desktop Environments
---

### Post by chris86wm on 2005-09-18
well, i have tried many things but my audio and video doesnt seem to match up when i am playing movie files. its ok for the first ten minutes then it goes out of sync. i have to pause it and then hit play to get it back to normal. my computer is up to spec and shouldnt have any trouble at all handling this.
i have downloaded all of the codecs from ubuntuguide.org and i have tried many players (xine, mplayer, and totem)

what is going on?

---

### Post by chris86wm on 2005-09-19
common guys...any help?

---

### Post by oneybm on 2005-09-19
My big question, and I don't know much about this, would be rather or not you playing video clips streamed from the internet, ones that are saved on your hard drive or maybe CD/DVD or other media or is it a DVD?

I know that in the case of the disc based content that enabling DMA will fix that.  Otherwise you need someone with a bit more experience than myself.

Hope it gives you something to work with,

---

### Post by chris86wm on 2005-09-19
playing these clips straight from the harddrive. most are around 700mb.

---

### Post by chris86wm on 2005-09-21
bump ?help?

---

### Post by oneybm on 2005-09-21
I'm really out of ideas.  I'd go back to checking codecs and making sure they are installe and working.  Otherwise it may just be a problem with the files themselves.  I know some clips I have gotten on websites play faster than they should or just don't have sound.  Don't know why that is; however, of course they work in Windows.  Sorry I can't help ya mate.

---

### Post by Xiata on 2005-09-21
[QUOTE=oneybm]I'm really out of ideas.  I'd go back to checking codecs and making sure they are installe and working.  Otherwise it may just be a problem with the files themselves.  I know some clips I have gotten on websites play faster than they should or just don't have sound.  Don't know why that is; however, of course they work in Windows.  Sorry I can't help ya mate.[/QUOTE]
 First: make sure DMA is enabled for your hard drive. ```
hdparm -i /dev/hda | grep udma
```. If it is not enabled edit your /etc/hdparm.conf and edit the /dev/hda entry. For now, ```
hdparm -d1 /dev/hda
```

Now you didn't specify what KIND of movie you are playing. Codecs do make a big difference. WMV for one desyncs terribly using the native WMV1/2 decoder (libffmpeg?) anyhow, get the wmvdmod.dll from your windows installation and put it in /usr/lib/win32 (xine's default win32 codec folder), or wherever you wish to put it. MPEG/other issues, update your video driver, use Xv or change its output method (Xine Setup (make sure you are in advanced or higher mode), video tab, Video driver to Use), and experiment. You WILL have to restart xine everytime you change that setting.

Course, there is always updating your video driver to the latest nvidia/ati driver. That generally helps out a lot.

---

### Post by chris86wm on 2005-09-21
thanks for the help guys, this problem is with pretty much every type of movie file i am playing (wmv, mov, mpeg, etc)
here is where i am at:
1)DMA is enabled
2)took the file from the windows box and put it in the folder
3)I am playing around with the settings tonite with a couple of videos but i do have a question.

How do i go about updated the video driver? I used the ubutu guide to help me out the first time to install it, so do i just follow the same thing and install it again?

thanks so much for helping me out here, really appreciate it.

---

### Post by TristanMike on 2005-09-22
What video card do you have, if it's nVidia, the one from the repos should be sufficiant enough. If they're Ati, you need to read [this](http://www.ubuntuforums.org/showthread.php?t=65276&highlight=ATI+drivers) among others I'm sure.

---

### Post by chris86wm on 2005-09-22
nvidea is what i have. btw it was still messing up last night :(
im going to get a new sound card tonite. maybe that will help.

---

### Post by chris86wm on 2005-09-22
this is starting to get me angry. i got a soundcard today and its having problems installing too. its a soundblaster live 24bit and its supposed to be supported but doesnt seem to work. also mplayer freezes when i have audio enabled. something is very wrong here.

---

