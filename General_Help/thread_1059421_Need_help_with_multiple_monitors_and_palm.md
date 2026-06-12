---
title: "Need help with multiple monitors and palm"
date: 2009-02-03
forum: General Help
---

### Post by compdrmt on 2009-02-03
Although I support windows environemtns for a living and so must use that platform, I have set up Linux for my own use for a number of years, most recently having landed on Suse as a favorite.   Alsthough I have had some trouble with Suse for the most part it did what I needed.  I currently run a Suse server in my office. 

I decided to give Ubuntu a try for myself and as a possible offering to customers. At first i was quite impresssed withthe install etc.  Then i encountered issues with things that I thnk should just work  perhaps these have been answered here( i did not find them soved) sand someone can point me to the answers. 

First a possible bug. After making changes to try to et two monitirs working (see below) I rebboted the system and it would not boot into a graphic mode, after much trouble and undoing any changes and several othr things I discovered that it booted just fine into the onld kernel listed on Grub. It will boot 8.10 2.6.27-7 but still will not boot the newer 8.10. 2.6.27-11  into graphic mode weird don't know if anyone  else ha encountered this 

that aside tyhere are two things that must happen for me to be happy with Ubuntu   

1) multiple monitors
2-Sync my palm  

Also wireless to actually work but that one is secondary as this is a desk top and I suppose I can live with one workstation on a wire 

Any help getting the computer to work and do the two things mentioned would be greatly appreciated becasue alas until i can do at a minimum sync my palm I am forced to remain in Windows.

I have tried many things which i found here and all over the web including editing my xorg.conf file (which I though caused the boot problems it did not it just did not work) 

I have an ATI driver built on to the moboard and have several secondary cards which I have tried including an Appian four head card (ATI radeon chips)  No love.  BTW Windows finds the hardware and I can plug in five monitors there so I know th hardware works  I do not need 5 monitors here and would be fine with two.

For the Palm i have experience witthe trial of getting a palm to work in Linux on other distros so I trid all the trick but i am willing to assume I have done nothing if someone can point me toward a better set of steps 

Thanks

---

### Post by jimv on 2009-02-03
Multiple Monitors:

If it works in the old kernel, but not the new one, you may need to reinstall the drivers in the newer kernel.

Palm Syncing setup (for use with Gnome-Pilot):

[https://help.ubuntu.com/community/PalmDeviceSetup](https://help.ubuntu.com/community/PalmDeviceSetup)

---

