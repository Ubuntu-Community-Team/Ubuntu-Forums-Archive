---
title: "intel HD 2000 on 12.04 x64 beta 2...a novel"
date: 2012-04-14
forum: Desktop Environments
---

### Post by averageschmoe on 2012-04-14
Somehow I was recruited to be my unions go to IT guy. I'm currently responsible for the upkeep of 16 XP machines and 3 iMacs, all refurbished and connected to a Mac Mini OS X Server running -- I think -- Lion. The guy above me who set it up has no experience with Macs and didn't do so correctly so authenticating them to a domain with Open Directory has never fully worked. Why does such a small organization with simple needs have a niche server they don't understand? The former union president is an Apple zealot and when our Windows Server 2000 reached EOL he decided that we were upgrading to a Mac. That was over a year ago and everyone is fed up with it so we are changing over. Someone without any Ubuntu experience suggested it as an option so we will be putting a Ubuntu Server box together (hopefully running Ubuntu Server from the Mac Mini Server when we know roughly how to get things up and running in a stable condition).

So, my problem is I have no technical training although I do enjoy tinkering and my lmited exposure to Ubuntu has been overall positive. If I ever get around to being able to buy a laptop I will be making sure it's as Ubuntu compatible as I can find.

My issue is with Intel HD 2000 graphics. We have put together 2 computers with identical components:

ASRock H67M-ITX LGA 1155 Intel H67 UEFI
Intel i3-2100t
4 GB G.Skill Eco-Ram
Intel 520 60GB SSD
Mini-ITX case vesa-mounted to monitor.

99% of the time these computers are used for browsing the web. The one thing i wanted them to do well was internet video streaming so people could bring in headphones and watch Youtube, Netflix, hulu, etc. After a week of fiddling around I'm pretty sure I'm further from my goal than ever. I've tried Adobe Flash and Lightspark and enabled i916 RC6 in /etc/default/grub (which from this [website]("https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks") looks like it should have been done by default) which is also supposed to give a graphics performance boost. But in less than 2 minutes of 1080p youtube this computer sounds like a jet turbine and the picture starts to degrade. 

I know Flash is the bane of Linux but is it really this bad? Is Intel HD 2000 that inadequate? I find it easier to believe that my ineptitude is a more likely candidate which is why I wonder if I need to install anything related to Intel HD 2000. I can't find anything indicating so but when I click on system details 'Graphics' is listed as 'unknown'. 

Also, up until yesterday this box ran quiet unless I was viewing HD Flash content. The cpu fan is currently running at 3139rpm and the cpu shows 46C with nothing but 2 tabs in Firefox, an open Terminal, and Psensor running. I know it's beta but could I have simply botched something and need to start over? Please, if there is an Intel video driver I need to find, lead me to it. I can't seem to find it myself, if it even exists.

---

