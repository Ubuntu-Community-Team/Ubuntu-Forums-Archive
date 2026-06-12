---
title: "Sony Giga Pocket TV tuner + MythTV?"
date: 2006-08-09
forum: Desktop Environments
---

### Post by srunni on 2006-08-09
Does anyone know if you can use Sony's Giga Pocket TV tuner with MythTV? Is the setup similar to the method used for the Hauppage TV tuners?

---

### Post by Jagot on 2006-08-09
I would also like to know.  I've done lot's of browsing through these forums and on Google but haven't been able to get it working, not sure if it is possible - evil things like proprietary drivers, etc.  I have tried MythTV and it didn't work for me.

So I'd be grateful also if someone else can tell us how if it is possible - it's currently the only thing keeping me from wiping Windows from my hard disk.

---

### Post by srunni on 2006-08-09
Yeah, the main reason I want to use MythTV instead of Windows Media Center is the DRM.

---

### Post by innactpro on 2006-09-26
I contacted Sony and got this...

"Thank you for contacting Sony Online Support.

The SONY VAIO desktop computers are designed specifically to work with the Windows operating system with which they ship. While we have heard that Linux will work on the PC by SONY, SONY has not tested Linux on our VAIO computer systems.

SONY has not designed and is currently not in the process of developing Linux drivers for the hardware components of our VAIO systems. If you intend to install the Linux operating system on your PC, you will need to contact your Linux distributor for any available Linux hardware device drivers, software applications or system utilities. A few websites that may prove helpful to you are:

[http://www.linux.org/](http://www.linux.org/)

[http://www.cs.utexas.edu/users/kharker/linux-laptop/](http://www.cs.utexas.edu/users/kharker/linux-laptop/)

[http://sunsite.unc.edu/mdw/linux.html](http://sunsite.unc.edu/mdw/linux.html)

[http://linux.about.com/compute/linux/](http://linux.about.com/compute/linux/)

NOTE: The internal modem is designed to work with the Windows
operating system only.

NOTE: The installation of a "Dual Boot" hard drive format may
disable several Windows advanced features and utilities.
We do not assist in, or support our VAIO systems in a
Linux "Dual Boot" configuration.

The VAIO Customer Information Services Center is unable to support any operating system or configuration other than the one originally shipped from SONY.

Thank you for the opportunity to be of assistance."

](*,) 

The provided links weren't very useful. It looks like we won't be able to use Giga Pocket in an linux environment. There are two other threads about this and they are having the same problem.

---

### Post by srunni on 2006-09-26
Well, this is from a blog ([http://redefine.dyndns.org/~andyr/blog/archives/2005/11/](http://redefine.dyndns.org/~andyr/blog/archives/2005/11/) - scroll down to November 20th) which talks about someone using the exact same model Sony VAIO as my computer for MythTV: > The machine also includes an ATI X300 PCI-Express video card (which can probably be made to work in Linux), and a Sony "Giga Pocket" video capture card. This card doesn't appear to be supported under Linux, but I found that it has a Conexant CX23416-22 chip on it, so getting it to work under Linux might just be a possibility. I am encouraging Kevin to work with the folks behind the ivtv project to see if this can be made a reality. I think it would be a nice story to take a piece of hardware that initially only worked with Sony's proprietary TV capture software, and now has been expanded to work with Windows Media Center Edition, work in Linux. I may talk to the MythTV people and see what the deal is with this type of stuff, and if it's possible.

---

### Post by mtiffany on 2007-02-06
I don't know if anyone is even checking this anymore, but has anyone actually got MythTV to work with the Sony Giga Pocket TV tuner?  I am planning an install of Ubuntu 6.10 instead of upgrading the RC210G I have to Windows Vista, but I want the TV tuner to work otherwise it makes the Media Center functionality useless.

---

### Post by srunni on 2007-02-11
I don't think it works. I have an RC110G, and from what I know, the Giga Pocket is drastically different from the Hauppage TV tuners recommended for MythTV. I'd suggest either dual booting or getting a Hauppage TV tuner (they're only about $60).

---

### Post by innactpro on 2007-04-03
Has anyone tried using Wine or some other windows emulation? I still haven't made the switch to Linux and I am aware that emulating windows in a Linux environment isn't always the most stable approach.

---

### Post by innactpro on 2007-04-04
.

---

### Post by innactpro on 2007-04-04
From another forum I came across.

"In my experience, the only piece of hardware that didn't have a driver in Linux was the Sony Mpeg Gigapocket, and I wrote a driver for that so that I could use it with MythTV."

[http://www.msforums.com/index.php?showtopic=262&view=findpost&p=714](http://www.msforums.com/index.php?showtopic=262&view=findpost&p=714)

Maybe if we ask this guy for help...

---

### Post by srunni on 2007-04-06
Well, the problem I've been having is that I can't even find the driver for it on Sony's site. I've scoured the internet, and so far, there has been no sign of a download location for the Giga Pocket driver. However, I do have the Windows XP MCE restore DVDs on hand, and I may be able to use nLite to extract the driver from them. As for that guy on the MSForums, I'll try to contact him and see if I can get the Linux driver. If I manage to get it, I'll upload to RapidShare, etc. and link it here.

---

### Post by srunni on 2007-04-14
Update:
The author of the driver replied as follows:
> You are now the second one to ask me for this, however I will give the same response to you, as I gave to the other person.

Unfortunately, due to some legal issues, I will not be able to share my driver. You can blame that one on one very disgruntled user.

I used to share all of my software freely, but after the legal problems, I'm afraid to give any softwares to anyone.

What I can do, is give "Warmer/Colder" advice on whether or not you are going in the right direction. I can also tell you that most of the driver code already exists online, only a few modifications and a little bit of new code, are needed to get it working.

Sorry for the cryptic response, I just don't want to get into any more trouble.

Any ideas as to where I might find this driver code online?

---

### Post by sr59899 on 2007-05-12
Any luck getting this driver?  I'm very interested in it as well.

---

### Post by srunni on 2007-05-30
> **sr59899 said:**
> Any luck getting this driver?  I'm very interested in it as well.

From what I can tell, you can't just "get" the driver - someone has to write it, and the one person that has done so won't distribute it. Since I know very little about actual programming, someone else would have to do this. Any volunteers? ;)

---

### Post by tgalati4 on 2007-05-30
Wow, now I'm interested in hearing more of the story about the disgruntled user!

---

### Post by srunni on 2007-05-30
> **tgalati4 said:**
> Wow, now I'm interested in hearing more of the story about the disgruntled user!

I doubt he will share that either, in fear of legal repercussions ;)
In all seriousness, one of the people he shared the driver with probably had system issues after installing his driver. They threatened legal action (which shouldn't be possible as long as he made it clear that there was no guarantee for the code) and he found it easier to just pull the code than deal with these issues.

---

