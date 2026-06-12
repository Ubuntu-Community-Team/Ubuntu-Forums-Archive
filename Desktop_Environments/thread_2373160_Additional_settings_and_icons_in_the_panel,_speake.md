---
title: "Additional settings and icons in the panel, speakers don't work"
date: 2017-10-03
forum: Desktop Environments
---

### Post by lucask2 on 2017-10-03
Hi, my first post here :) I'm using xubuntu 16.04 I tried to fix a problem with my laptop speakers not working using the advice from what Google would come up with. The problem was that suddenly my built-in speakers stopped working but headphones or external speakers continued to work just fine. So the advice I found on the Internet was this: 
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get purge linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop
reboot
```
And since then in the top right corner I have an additional battery icon, a bluetooth icon and a cog icon and another clock. Also some of the settings are duplicated but have slightly different names. I am completely new to linux so I did not really know what I was doing, so I tried to fix it by removing gdm and ubuntu-desktop with sudo apt-get remove. It didn't fix the problem. Did I screw up? Do you know what happened and how can I fix it?
PS: The speakers still don't work XD

---

### Post by ajgreeny on 2017-10-03
O dear!  Welcome to the forum, and what a pity you did not start here first as I think we could have helped you a great deal quicker and with fewer repercussions.

You should have opened Sound Settings and used the **Output Devices** tab where headphones and speakers are shown separately and can be adjusted separately as well.

I would love to see that site that suggested all that, particularly installing ubuntu-desktop and gdm, just to do something that I suspect simply needed a change to the mute or volume settings in **Sound Settings**, which you get to by clicking the volume icon on the panel.

The problem now is that ubuntu-desktop will have brought with it a huge number of packages that are certainly not needed in Xubuntu; when I just went through the motions on my Xubuntu 16.04 system it would have installed 354 packages turning the system into a chimera of Ubuntu and Xubuntu.  If you can live with the system you now have, fair enough, and to remove all that was added and is not needed will be a fairly long process, but if you do wish to clean it all out come back again and I'll try to suggest what you may need to remove.

PS:
You can see all that was installed on your system on that date by running command ```
grep -i " install " /var/log/dpkg.log.1 /var/log/dpkg.log
``` The output of that will be a list by date of all that has recently been installed and by looking at the time and date yu will be able to see the long list of everything added at that time.

---

### Post by Autodave on 2017-10-03
"You should have opened Sound Settings and used the **Output Devices** tab where headphones and speakers are shown separately and can be adjusted separately as well."

As ajgreeny posted (in case you missed it) you should still be able to do that now and get your internal speakers working. You *may *have to install pavucontrol if it is not still installed.

---

### Post by lucask2 on 2017-10-03
Thank you for your answers! And, contrary to what you may think from what I did to my poor xubuntu, I am not THAT stupid not to try the simple sound settings first :D What I have in the output is "Speakers (unavailable)" and when I select it, nothing happens, it's unmuted and when I play some music the volume bars jump right and left, but no sound from the speakers. Also, I have the latest pavucontrol version installed. 
I'd love to clean it all out ajgreeny and I'm very eager to learn more about linux as it is my first distro ever so that would also help me in that.

---

### Post by ajgreeny on 2017-10-03
If you run that command I gave you in my post above you will get output similar to this but with different packages showing, of course.
```
/var/log/dpkg.log.1:1209:2017-09-18 22:05:37 install linux-image-4.4.0-96-generic:amd64 <none> 4.4.0-96.119
/var/log/dpkg.log.1:1213:[COLOR="#FF0000"]2017-09-18 22:05:40[/COLOR] install linux-image-extra-4.4.0-96-generic:amd64 <none> 4.4.0-96.119
/var/log/dpkg.log.1:1231:[COLOR="#FF0000"]2017-09-18 22:05:46[/COLOR] install linux-headers-4.4.0-96:all <none> 4.4.0-96.119
/var/log/dpkg.log.1:1235:[COLOR="#FF0000"]2017-09-18 22:05:50[/COLOR] install linux-headers-4.4.0-96-generic:amd64 <none> 4.4.0-96.119
/var/log/dpkg.log.1:1439:[COLOR="#FF0000"]2017-09-18 22:06:33[/COLOR] install linux-signed-image-4.4.0-96-generic:amd64 <none> 4.4.0-96.119
```
I have coloured the time stamps of those installations in red to make them clearer; you will need to look at the list of everything that was added at the time that you installed that list including ubuntu-desktop and try to remove as many of those as you can, but as there may be up to 354 of them it may be something that simply takes too long.  It may, thereore be easier to look at your menu, note where you have duplicate applications that you don't want, eg, gnome-terminal, nautilus (just called "files" in the menu), remove those applications and then run ```
sudo apt autoremove
```to clean out unnecessary dependency packages.

---

### Post by lucask2 on 2017-10-05
OK, thank you. I removed ones that sounded most likely to be causing my problems. Then I tinkered in the panel and it looks normal now. However, my speakers are still not working. They are still marked as unavailable in the output devices.

---

### Post by flocculant on 2017-10-12
> **lucask2 said:**
> Thank you for your answers! And, contrary to what you may think from what I did to my poor xubuntu, I am not THAT stupid not to try the simple sound settings first :D What I have in the output is "Speakers (unavailable)" and when I select it, nothing happens, it's unmuted and when I play some music the volume bars jump right and left, but no sound from the speakers. Also, I have the latest pavucontrol version installed. 
I'd love to clean it all out ajgreeny and I'm very eager to learn more about linux as it is my first distro ever so that would also help me in that.

what do you have in the configuration tab? 

What do you see if you use alsamixer in a terminal?

Have you managed to removed ubuntu?

Did sound work in the live session when you checked things worked before installing?

Finally - don't blindly follow people's howto's on the net, half the time if you look for 'sound +linux' you'll hit all the remove pulseaudio and kill it with fire posts from years ago ...

---

### Post by lucask2 on 2017-10-12
Actually, as I didn't disconnect my headphones over the last few days I didn't do anything about my speakers. But now that you mentioned it, I wanted to check them and suddenly they work! I have no idea what changed, because after I removed the unwanted packages, they weren't working and now they are. Absolutely no idea what happened.

---

### Post by flocculant on 2017-10-12
Ok - thanks for letting us know.

---

