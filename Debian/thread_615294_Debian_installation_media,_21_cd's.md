---
title: "Debian installation media, 21 cd's?"
date: 2007-11-16
forum: Debian
---

### Post by Perpetual on 2007-11-16
Yeah, seems like a stupid question but this is my first attempt at installing Debian.  I see there are 21 cd's or 4 dvd's, are all needed to install or just the 1st cd/dvd and the balance have all of the additional available packages?

Looking at installing Debian Etch.

---

### Post by disturbed1 on 2007-11-16
I usually just grab the net install iso. It contains just enough on disc to set up a basic system, then prompts you for the type of install (Desktop, Server, Laptop etc). It will then ask you to choose a mirror from a list, and download only the needed packages.

The CDs and DVDs contain the complete repositories. This is nice if the system you're installing to won't have internet access at the time of installation. But is not needed for a system that will have internet access at installation time.

---

### Post by Perpetual on 2007-11-16
Thanks for the response.  I think for the moment I have scared myself by reading too much/being too new to linux/being spoiled by ubuntu and other distros that work out of the box.  Looks like with Debian nothing works out of the box, wireless, video cards, modifying kernel parameters...

I didn't realize how in depth it would be, how much other distros do for you.

---

### Post by disturbed1 on 2007-11-17
I don't know about wireless, doesn't fit into my scheme of current computers. Means we don't need it, but I can see why how and when others would.

Video works out of the box, VESA will work with 99% of the video cards out there :). If you need binary nVidia or ati drivers, then they are available through synaptic. My Debian server uses an Intel graphics card, but I did manage to install the nVidia driver when I needed to. It wasn't as straight forward as Ubuntu's install/reboot. There's a wiki out there just for Debian and binary video drivers, I'd read through it and print it out if needed.

Here's a couple of links I gathered about nVidia and Debian

[http://www.debianhelp.co.uk/nvidia.htm](http://www.debianhelp.co.uk/nvidia.htm)
[http://wiki.debian.org/NvidiaHowTo](http://wiki.debian.org/NvidiaHowTo)
[http://technowizah.com/2006/11/debian-how-to-nvidia-drivers.html](http://technowizah.com/2006/11/debian-how-to-nvidia-drivers.html)
[http://www.debianadmin.com/envy-ati-and-nvidia-drivers-installation-made-easy.html](http://www.debianadmin.com/envy-ati-and-nvidia-drivers-installation-made-easy.html)

In my opinion, Debian has better doccumention compared to Ubuntu, by shear number of articles, technical indepthness, and up-to-dateness. Once in a while it can fall victim of TMI (too much information)

---

### Post by public_void on 2007-11-17
> Looks like with Debian nothing works out of the box, wireless, video cards, modifying kernel parameters...Debian may seem complicated, but I found it easy, and very similar to Ubuntu (No surprise really). Everything that worked in Ubuntu worked in Debian, with the same problems occurring in both. I read this [article]("http://adventuresinopensource.blogspot.com/2007/10/another-day-another-distro-part-5.html") recently that confirmed my experience with Debian. Once up and running its as solid as a rock.

---

### Post by Perpetual on 2007-11-19
Thanks for your responses guys.  I am actually posting from Debian Lenny at the moment and other than spending couple hours and pulling some hairs, I was able to get wireless running and a few other things I needed.

So, I got over my intimidation and learned a few things.  Dunno yet if I will keep it as my laptop OS or go back to Gutsy.  Big decider is this community vs. the Debian community.  I don't feel at all like I would fit in there, not being a Real Debian User.

---

### Post by kerry_s on 2007-11-19
> **Perpetual said:**
> Thanks for your responses guys.  I am actually posting from Debian Lenny at the moment and other than spending couple hours and pulling some hairs, I was able to get wireless running and a few other things I needed.

So, I got over my intimidation and learned a few things.  Dunno yet if I will keep it as my laptop OS or go back to Gutsy.  Big decider is this community vs. the Debian community.  I don't feel at all like I would fit in there, not being a Real Debian User.

don't sweat it, i use debian and i'm here all the time. :)
it doesn't matter what you use, help is help, whether you need it or are giving it, this forum has a section for everyone.
for example, i'm using windows xp right now, do you care about what i'm using?

---

### Post by Perpetual on 2007-11-19
> **kerry_s said:**
> don't sweat it, i use debian and i'm here all the time. :)
it doesn't matter what you use, help is help, whether you need it or are giving it, this forum has a section for everyone.
for example, i'm using windows xp right now, do you care about what i'm using?

Yeah, I know where you're coming from and appreciate the response.

---

### Post by disturbed1 on 2007-11-20
I read the Debian forums and mailing lists, but post on Ubuntu's. Agree that the Debian world is a bit different. The good news is, if there's an issue you have in Debian someone from Ubuntu might know the answer.

Even if you decide not to keep Debian, your knowledge of how Ubuntu works under the hood will be much greater.

---

### Post by tjagoda on 2007-11-25
I use Debian on all my servers, but Ubuntu on my desk/laptop, and I post on both forums.

Dont worry about which Distro you use - a community is a community is a community.

---

### Post by angryfirelord on 2007-11-26
> **tjagoda said:**
> Dont worry about which Distro you use - a community is a community is a community.
Unless it doesn't have apt. :D

---

