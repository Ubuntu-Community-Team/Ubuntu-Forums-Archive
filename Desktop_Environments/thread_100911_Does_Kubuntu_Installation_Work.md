---
title: "Does Kubuntu Installation Work?"
date: 2005-12-08
forum: Desktop Environments
---

### Post by Ingla on 2005-12-08
Hello.

I've been using Ubuntu without too many problems except that I need a lot of programs which seem to be available only for KDE. Therefore, I installed Kubuntu to try it out.

However, it doesn't seem to work properly. I've been unable to get my USB modem connected (it works OK on Ubuntu). I might still be looking for the solution to that, but I'm encountering all kinds of buggy problems which remind me more of a corrupt Windows installation than Linux.

A couple of examples:

I wanted to edit a file as root, so I tried to open Kate as root from the terminal. I got weird error messages saying Kate can't be opened...probably has crashed. When I rebooted, the system had apparently saved the session and Kate popped up with a request for my password. Then it worked.

I tried to eject a CD from the desktop CD icon (right click menu). It wouldn't go out...nothing happened. So I went to the CD icon in Konqueror and it worked.

The next time I got the sound of glass breaking and an error notice...no way to eject the CD.

If I reboot, it's OK...for a while.

Thinking I had a corrupted installation, I downloaded a couple of other ISO's from different servers. Same kinds of problems.

My computer is not particularly low end. I have 2.4 CPU and 512 RAM. Ubuntu works, as does Windows XP. The video card memory is a bit low, but I'm not trying to run Windows games...just normal activities as described above.

Is Kubuntu functional?

Anyone familiar with this?

---

### Post by linbetwin on 2005-12-08
Kate didn't work for me either. There is a thread in this forums were many people complain about Kate not working. I don't know if there is a fix for that, as I went back to GNOME.

---

### Post by GeneralZod on 2005-12-08
Kubuntu generally tends to be far less polished than Ubuntu, alas.

I'm not sure why your modem would work in Ubuntu but not Kubuntu, though, as they should be the same in this regard.  Is kppp configured correctly?

Kubuntu works rather poorly with sudo, and kate is one application that doesn't seem to want to work at all with it :) Use kwrite instead:

```

sudo kwrite

```

or maybe even

```

kdesu kate

```

might work.

You can eject the CD from the command-line if all else fails:

```

man eject

```

The initial 5.10 release of Kubuntu had a load of troubles with removable media, which were fixed up somewhat by a later update - which I guess you can't actually download yet :/

So far, I'd bet that this isn't a corrupt install, although the fact that your modem doesn't work it odd.

By the way, you could have installed KDE side-by-side with your (working!) Ubuntu install simply by using 

```

sudo apt-get install kubuntu-desktop

```

but I guess it's too late now :/

---

### Post by Ingla on 2005-12-08
Thanks.

**No, it isn't too late.** Ubuntu is on another hard drive. It's still working although Firefox loads very strangely lately....about half the screen comes up until everything loads oh so slowly. Then it works.

Kubuntu generally runs like a slug...very slow to load anything. I think they have too many cute visual effects. In Windows, I turned most of those off but have yet to learn how to do that in KDE (or Gnome).

Also lots of streaming issues (have to get some audio streams from the desktop programs...Firefox plugins seem messed up..video mostly doesn't work).

And a couple of buggy looking things here and there, but not like Kubuntu.

**The question is** what do I have to install besides Kubuntu Desktop. I notice a lot of KDE things for download in Synaptic. Do I just install the desktop or will KDE programs need all kinds of infrastructure?

[B]Also, can this install screw up anything...like my modem.
[/B]
Maybe the safest thing to do would be to make a fresh Ubuntu install on the disk currently hosting Kubuntu and then get the modem running and try installing KDE. I can always format that again and use it for Ubuntu.

Problem with the current Ubuntu install is mainly that the hard drive is very old and making noises sometimes. I want to actually work in Linux and would therefore prefer not to set up everything only to lose the hard drive. So, for now, the newer HD is open to a few experimental installations, if that's what it takes.

(By the way, the only difference I noticed in installing the USB modem driver was that in Ubuntu, I ran eciadsl-config-tk to configure. Kubuntu won't run it. First it looked like some dependency didn't exist. After a new install it said "This is not a tk file", which is nonsense. So I ran eciadsl-config-text, which is supposed to do the same thing. In the first install, the config program kept showing my previous settings for DNS servers, ALT synch and ALT pppoe as the default, no matter what I had set. This didn't happen after the second Kubuntu install, but then a used a more recent driver version. Who knows...weird.) 

Anyway, please let me know about installing KDE items...which or all or just the desktop?

Thanks.

---

### Post by Ruskie on 2005-12-08
Hi. Kubuntu-desktop is a package that is built on top of all other packages/applications that you would find on KDE. That is, for example, Kate, KsCD, Konqueror, etc. etc. In other words, if you select Kubuntu-desktop, you will download and install all the package you need to have KDE 3.4 with its applications up and running.
What you get if you do so is that at login, where you have the option to choose your session type, you can enter Gnome, console and now also KDE. That is all.

About this question:
> Anyway, please let me know about installing KDE items...which or all or just the desktop?

and this worry:
> Also, can this install screw up anything...like my modem
They all go round the same thing: KDE (like Gnome) is only the "visual" aspect of your Linux system; and they're the sum of all of their packages, simply putting it. So, to install KDE you have to install all its packages, and this is easily got selecting Kubuntu-desktop for import. After that, you can strip out applications you don't use, like Kate (you have Gedit), or Adept (a package manager I don't like: I use Synaptic as well), or... whatever.
And, no, it shouldn't *normally* break your modem setup, for the simple reason that the Desktop has nothing at all to do with your modem. Modem management is part of core linux, so intalling a visual interface shouldn't harm it. I used conditional because, actually, that part of the installation should be the same you get in Ubuntu, because there is no difference between the 2 systems in that area.

Curious you find KDE slow. I find Gnome much slower: sometimes I launch an application and have time for a tea before it is running. And I have handles in KDE to turn off unwanted/heavy visual effects, but don't have in Gnome to make it display windows faster. :)
That, and your weird problem with the modem, can lead to only one conclusion: computers are alive!!! :)

---

### Post by Ingla on 2005-12-08
Thanks.

I guess I'll start trying things. You're right about computers. I've always known that they are actually possessed by undetected, sinister beasties who manage now and then to do wondrous strange things. Like now.

By the way, I downloaded a checksum checker to check my ISO. It claims all is well and this is a faithful Kubuntu installation. So it must be *them*!

---

