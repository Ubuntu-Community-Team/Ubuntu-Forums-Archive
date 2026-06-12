---
title: "Double Problem: Wrong resolution at log in and IMPOSSIBLE change session"
date: 2009-01-31
forum: General Help
---

### Post by jofre on 2009-01-31
Hi everbody,

As the title says, I have two problems, and not sure which one is more awkward...

1.- Each time I log in the resolution of the screen is wrong. I am using the nvidia driver. Funny enough, with the proprietary driver disables, I do not have problems. The issue is that I work often with an external monitor, so it is very handy to use nvidia-settings. 
I have tried to:
 $ sudo nvidia-settings 
change to the correct values, save to file, merge to existing file. log out, log in. Wrong resolution. I have been looking in google all morning but I could not find anything that work.

2.- This second problem I suspect it is related to the first one, but not sure. I can change session. I work sometime with xfce and with Openbox. When I change session from the GDM login window, write my pasword, and click enter, it just goes to gnome (with the wrong resolution), even if I tried putting openbox as default.


Any ideas?
Thanks in advance,
Jofre

I have to add another problem: I just realize that when I insert a cdrom, it get the message:
Cannot mount volume
Details: mount: must be superuser to use mount

If I this would not be Linux, I seriously start thinking about a virus... What the hell is going on!??

---

### Post by jofre on 2009-01-31
No ideas?

---

### Post by bsmith1051 on 2009-01-31
You could try waiting more than 1 hour for a reply...

re #1, login resolutions, the default behaviour is to auto-detect everything but it doesn't have consistent results.  The workaround is to manually specify which resolutions you want the system to use and the login will default to the highest available.

Here's a previous post I did that has details,
 [http://ubuntuforums.org/showpost.php?p=6639105&postcount=12](http://ubuntuforums.org/showpost.php?p=6639105&postcount=12)
My example is with the ATI driver but I'm pretty sure the Nvidia driver is the same.

re #2, sorry, I have no idea.  I stick with Gnome.

---

### Post by jofre on 2009-02-01
Thanks bsmith1051 for the reply.

You are right, I should be more patient when waiting for a reply, but I was a bit annoyed with my laptop ;-)

About your suggestion, I already have tried that, and it does not work. It is like GDM is loading the configuration from somewhere else, that is the reason I posted as a single problem. My feeling is that there is something wrong with GDM, but I am far from being a linux geek, so, I did not want to state this on the initial post.

Thanks for the try anyway.
Jofre

---

### Post by jofre on 2009-02-01
I just edited the first message, but just in case:


I have to add another problem: I just realize that when I insert a cdrom, it get the message:
Cannot mount volume
Details: mount: must be superuser to use mount

If I this would not be Linux, I seriously start thinking about a virus... What the hell is going on!??

---

### Post by bsmith1051 on 2009-02-02
> **jofre said:**
> I am far from being a linux geek
Yet you swap window managers???  

Without providing any details of your configuration there's no way to troubleshoot your CD-mount problem.  And if you're juggling window-managers I hate to think what else you've tweaked.

Quick suggestion: Does everything work if you boot from a LiveCD, or better yet from a flash-drive?  Flash drive would let you test the auto-mount for CDs.

(I think the most common problem with CD mounting is the way the CD drive is listed in fstab.)

---

### Post by Neural oD on 2009-02-02
If u don't have too much tweaked, and have your data on a different partition or hard drive, I would suggest a re-install. Some may think this slander - but for an average user - it's often the best advise - especially if some strange configs have been changed along the way. The reason for the re-install is this: I used to be a purist - but pragmatism just has to enter the equation - thus I'm now a pragmatic purist! Looking at when u posted this - it would have been far quicker just to do that re-install. 
Just so that I don't get too flamed - I suggest that one doesn't tinker too much with one's primary os - unless they are totally confident. Set up another os - even in a vm - and tinker and learn from that one! 
Anyways - just my 2c!

---

### Post by jofre on 2009-02-02
Hi,

I do not consider to hard to go to synaptic and install a desktop environment. So in my definition of geeky, everything that is just done through synaptic does not count ;-)

Second, the only configuration file I have changed by hand has been xorg.conf, and always did a backup of the original file. When I put back the original xorg.conf the problem remained.

I do not like too much the idea of a reinstall as this is suppose to be Linux (I think I would get into your definition of purist).

Nevertheless, thanks for posting a reply, it is always nice :)
Jofre

Regarding the CDrom, I did not happen with a normal music CD... weird...

---

### Post by Neural oD on 2009-02-02
jofre - have u installed the latest nvidia drivers. Go to the nvidia website and download - they will also have instructions on how to install. You can then get the packages nvidia-xconfig and nvidia-settings from the repositories.
This should sort your display issues out.

---

### Post by Neural oD on 2009-02-02
about the cdrom - let the forums know if there is still a problem

---

### Post by jofre on 2009-02-13
Hi, I have started a new thread as I found the origin of the problem, but still not the solution. 
The link is:
[http://ubuntuforums.org/showthread.php?p=6727056#post6727056](http://ubuntuforums.org/showthread.php?p=6727056#post6727056)

---

