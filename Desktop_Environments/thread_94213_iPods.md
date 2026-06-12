---
title: "iPods?"
date: 2005-11-23
forum: Desktop Environments
---

### Post by MegaMoose on 2005-11-23
Hey, everyone. I'm a complete newbie to Linux, and I just got an iPod Nano. I do, however, know some about computers, including that a commercial product probably won't work with open-source stuff. I got gtkpod, but I'm guessing there's some extra steps to get an iPod working. Could someone give me a step-by-step guide to making my iPod Nano work like I have an Apple or Windows machine? Also, I  tried working with it a little bit, and I have a few questions. Some files just wouldn't write to the iPod. After I put some files on the iPod, gtkpod put almost a gig of random crap in a hidden folder (I believe they were in a folder called Music which was in a hidden folder). Finally, after I right click the iPod icon on the desktop and unmount it, it still says "Do not disconnect" on the iPod screen and I was forced to pull it out. Nothing bad seemed to happen, but it bothers me. Could someone help me out with all this?

And also, I have been using the iPod on iTunes on Windows as well as trying to use it with Linux (I used it on Windows before and after Linux), so it might have created some files that created compatibility problems.

---

### Post by 23meg on 2005-11-23
From the GTKPod site: > The new iPod nano is supported as well, but you need to call 'File->Create iPod's Directories' once before syncing.Do you do this?

It's not a good idea to use both GTKPod and iTunes. Choose one and stick to it. Or choose neither and use Banshee / Amarok, which is what I do.

---

### Post by aysiu on 2005-11-23
[QUOTE=MegaMoose]Finally, after I right click the iPod icon on the desktop and unmount it, it still says "Do not disconnect" on the iPod screen and I was forced to pull it out. Nothing bad seemed to happen, but it bothers me. Could someone help me out with all this?[/QUOTE] I don't know about your Gtkpod problems, but [this thread](http://www.ubuntuforums.org/showthread.php?t=56515) may help for the Do not Disconnect. I would not, by the way, disconnect if it says "Do not Disconnect." If you absolutely can't get it to work, it's better to shut down the computer (or reboot it) before disconnecting.

Generally, older iPods (G3 and before) tend to work better with Ubuntu's current release (newer ones, like the Nano) tend not to work as well.

---

### Post by DeathOnJuice on 2005-11-23
Why is it bad to alternate between iTunes and gtkpod? Does it have to do with the iPodDB thing (I don't know much about it, but I've heard the term). MegaMoose says he used both programs and it apparently still works (except that it put those weird files on)...

By the way, I think I might have found out why some of your files wouldn't copy. The version of gtkpod in the repos doesn't support AAC (*.mp4 and *.m4a). You can get a version that does, but it is on the debian-marillat repos. Also, for everyone else's information, this guy must be using Hoary.

On a side note, when reading about iPods, I heard about them being ejected after you unmount them. I have a USB external harddrive, and when I plug it in, an icon for it appears on the desktop. Whenever I unplug it, I always right click the icon and hit unmount first. Every time I do that, it brings up a box that says it failed to eject the media because of an invalid argument. I never thought much of it until now and it still works, but now I'm a litle worried. Can anyone help me out?

---

### Post by 23meg on 2005-11-23
I have the same unable to eject message in Breezy as well; didn't have it in Hoary. I also have my ipod showing up as two different partitions, one being a 30mb one, and the other a 5.7gb one. The first one is unmountable. This also didn't happen in Hoary.

I think the rationale behind using the ipod with one program is that each program writes the extended info block (generated with md5 sums I think) in a different way. No matter what the theory is, it's certain that in practice this is the thing to do. Don't mix and match, especially with iTunes. Choose one app to manage your ipod with and stick with it. And start with a clean format if possible.

---

### Post by aysiu on 2005-11-23
[QUOTE=DeathOnJuice]Why is it bad to alternate between iTunes and gtkpod?[/quote] It's not bad, just inconvenient. If they're integrated, as they are in iTunes, you can just drag and drop songs from your library to your iPod.

> 
On a side note, when reading about iPods, I heard about them being ejected after you unmount them. I have a USB external harddrive, and when I plug it in, an icon for it appears on the desktop. Whenever I unplug it, I always right click the icon and hit unmount first. Every time I do that, it brings up a box that says it failed to eject the media because of an invalid argument. I never thought much of it until now and it still works, but now I'm a litle worried. Can anyone help me out? This is [a different issue altogether](http://www.ubuntuforums.org/showthread.php?t=84262).

---

### Post by 23meg on 2005-11-23
[quote=aysiu]It's not bad, just inconvenient. If they're integrated, as they are in iTunes, you can just drag and drop songs from your library to your iPod.
[/quote]Not really; a lot of extended info problems arise from doing this and eventually ipods get full of "ghost files" that don't appear as playable tracks.

---

### Post by DeathOnJuice on 2005-11-23
Wait, what? I still don't see what the problem is, Asyiu, unless it's what the other person said.

Also, for future reference in case I get an iPod and use it on Linux, if it becomes corrupted in any way, how can you format it and get it all back to normal?

EDIT: I just saw 23meg's post, and I guess that's what those extra files were on Moose's iPod. Maybe you should go ahead and tell him how to format it/reset it back to factory settings (if possible) so he can have a clean start?

---

### Post by RAOF on 2005-11-23
[QUOTE=DeathOnJuice]Wait, what? I still don't see what the problem is, Asyiu, unless it's what the other person said.

Also, for future reference in case I get an iPod and use it on Linux, if it becomes corrupted in any way, how can you format it and get it all back to normal?[/QUOTE]
You can run one of the iPod firmware upgraders (from windows, or possibly wine).  One of the options is "restore to factory settings" - this will format the iPod & rebuild the default stuff.

---

### Post by 23meg on 2005-11-23
> **DeathOnJuice] 

Also, for future reference in case I get an iPod and use it on Linux, if it becomes corrupted in any way, how can you format it and get it all back to normal?[/quote]Best bet: Windows ipod updater. People say it works with Wine said:**
>  
EDIT: I just saw 23meg's post, and I guess that's what those extra files were on Moose's iPod. Maybe you should go ahead and tell him how to format it/reset it back to factory settings (if possible) so he can have a clean start? I always suggest a reformat to those who seem to be having unresolvable ghost file / extended db errors. Same goes here; clean starts have solved all problems I've seen people encountering.

---

### Post by DeathOnJuice on 2005-11-23
OK, I guess that will pretty much solve his problem. Just curious, though; what is all this "extended info block" and "extended info" amd "extended DB" stuff?

---

### Post by aysiu on 2005-11-23
[QUOTE=23meg]Not really; a lot of extended info problems arise from doing this and eventually ipods get full of "ghost files" that don't appear as playable tracks.[/QUOTE] I don't doubt this could happen, but I've never seen it happen with my wife's iPod.

---

