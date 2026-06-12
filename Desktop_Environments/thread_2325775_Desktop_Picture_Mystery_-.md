---
title: "Desktop Picture Mystery -"
date: 2016-05-25
forum: Desktop Environments
---

### Post by electroconvulsive on 2016-05-25
I'm having a problem with my desktop that started when sometimes after coming back from suspend there would be a desktop picture I haven't seen before and not the type I would download or choose myself. The picture's origin and location are a complete mystery. I first noticed them when I installed ubuntu-tweak from the PPA and everytime it comes up dconf-editor tells me that the desktop picture is the one that is supposed to be there rather than this mystery picture. When I try to change the desktop background via its preferences nothing changes. This time I restarted my computer to see if it will fix it after logging out and back in changed nothing and now I have no desktop picture at all. Just a black screen with the same symptoms. 

I have also purged ubuntu-tweak from my system since so I am not sure if it originally caused the problem.

Also I have noticed that whatever is causing it is hijacking the picture at the login screen a tenth of a second after you see the original login picture. Checked my startup applications as well but there was nothing suss there either.

I have also logged into unity and the mystery desktop picture is there so the problem is not isolated to cinnamon. I have attached the desktop picture.

So does anyone know what is going on here? Have I been hacked? How do I fix it and make sure it doesn't happen again? Please help.:(

---

### Post by grahammechanical on 2016-05-25
Alternative desktops always brand the OS and override the original splash screens, greeter screens and wallpaper. And you have installed Cinnamon desktop environment. I do admit that that image does not look like a Cinnamon themed image.

Ubuntu keeps its background images at usr/share/backgrounds. I am not sure that simply deleting the image will necessarily bring a substitute image in its place. There might also be a backup copy of the file that is hidden because it has the tilde character ( ~ ) prefixed to the file name.

Regards.

---

### Post by electroconvulsive on 2016-05-25
Thanks for your response. I have narrowed it down a bit but only that. I have unhidden the hidden startup items and found nothing suspicious there. I have logged into Unity and was able to change the desktop repeatedly and logged in and out with everything behaving normally there. I also created a test user and logged into both Unity and Cinnamon and no problems there either. So whatever this is it is in my user folder or user settings somewhere to do with Cinnamon somehow. More investigating needs to be done I guess.

---

### Post by electroconvulsive on 2016-05-25
Well I managed to solve it in the end. I haven't logged out and back in to see if my changes stuck or not. So I found a left over folder hidden in /home which had the offending wallpaper in it. I reinstalled ubuntu-tweak so I could check out the problem's cause. Here it is ubuntu-tweak is being maintained very poorly. Th tweaks section points back at the maintainer's website for starters (Check attachment). It has a section called Admins which has a program called Love Wallpaper HD in it and nothing else that I think I may have clicked on and downloaded the offending wallpaper from their website. Why exactly did my wallpaper revert to this from time to time is anyone's guess still. Anyway this also disables your cinnamon desktop's ability to set its own wallpaper or at least that is what my experience was. This can be fixed by going into dconf-editor and navigating to org.cinnamon.settings-daemon.plugins.background and checking "active" again.

If you do not have dconf-editor installed go to the terminal and type in```
sudo apt install dconf-editor -y
``` That will install it for you.

I hope this solves this problem for anyone who comes across it.

My Advice: don't use ubuntu-tweak to start with.

---

### Post by Frogs Hair on 2016-05-26
> ubuntu-tweak is being maintained very poorly The developer just didn't have time anymore and noted this on the now defunct website at least two years ago.     [https://launchpad.net/ubuntu-tweak](https://launchpad.net/ubuntu-tweak)

---

