---
title: "Trouble installing adobe flash player"
date: 2009-06-12
forum: General Help
---

### Post by scatmandude on 2009-06-12
I'm running a new hard drive tower(new for me, not brand new), it's running Gutsy Gibbon and Firefox and I've been having lots of problems, but let's start here. When I try to install Adobe flash it gives me a choice of YUM, tar.gz, or rpm. I've tried all three and all three fail to install. The system tries to install it with the archive manager.

Which one should I use and what's the problem?

Any ideas?

---

### Post by synapsys on 2009-06-12
Open up synaptic and install package flashplugin-nonfree.

Or open up a terminal and type:

```
sudo apt-get install flashplugin-nonfree
```

Or if you insist on installing from flash website, you can download the .rpm and convert it to .deb using alien. Then install. You will be better off using the package that comes with Ubuntu.

---

### Post by hansdown on 2009-06-12
Hi scatmandude.

I think the support for gutsy gibbon has ended.

You would be better off to download, and install a newer version

of ubuntu.

8.04 is very stable. [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

8.10 seems good.  [http://releases.ubuntu.com/intrepid/](http://releases.ubuntu.com/intrepid/)

9.04 is the newest.  [http://releases.ubuntu.com/jaunty/](http://releases.ubuntu.com/jaunty/)

---

### Post by scatmandude on 2009-06-12
I did what you said in terminal. It seemed to be doing fine, but ended with this error notice:

"WARNING: The following packages cannot be authenticated!
  flashplugin-nonfree
Install these packages without verification [y/N]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse flashplugin-nonfree 9.0.48.0.2+really0ubuntu12
  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_i386.deb)  404 Not Found [IP: 91.189.88.140 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
"

What next?

---

### Post by scatmandude on 2009-06-12
Thanks. I think I'll try 8.04

---

### Post by synapsys on 2009-06-12
Make sure you have an internet connection.
Do what it tells you:

```
sudo apt-get update
```

Try again.

If that doesn't work:

```
sudo apt-get --fix-missing
```

Try again.

If that doesn't work:

Download Ubuntu 9.04
Burn to cd/dvd
Backup important files
Install

---

### Post by hansdown on 2009-06-12
8.04 is working beautifully on my machine. Post back if you need anything

else.

---

### Post by scatmandude on 2009-06-12
Hi, hansdown.

So, I follow the link to install 8.04 and follow the procedure and my machine uses a CD burner program to install, which is odd because this tower doesn't have a CD burner. So, it gets to the end and then announces that it can't find a CD or DVD to burn the OS to.....Yeah, no kidding. It then asks if I want to burn it to the disk. I say yes, it does and.....

Now what?

P.S. I turned off my computer at that point and have just come back to it.

---

### Post by hansdown on 2009-06-12
Ouch! Sorry scatmandude, I guess I just assumed you had a CD burner.

Errrr.... I don't suppose you have a system that can boot from USB?

(Please say yes).

You can order a "FREE CD" from canonical,but please be sure

of the architecture, and processor type.

Some systems work much better with the "alternate install disk"

---

### Post by scatmandude on 2009-06-13
> **hansdown said:**
> 

Errrr.... I don't suppose you have a system that can boot from USB?

(Please say yes).

Hmm, well I don't even know what that means really, so.....

I don't know.

---

### Post by hansdown on 2009-06-13
You can order a "FREE CD" from canonical,but please be sure

of the architecture, and processor type.

Some systems work much better with the "alternate install disk"

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

### Post by scatmandude on 2009-06-13
This is probably a dumb question, but, if I use another computer that has a CD burner on it to make a CD copy of 8.04 could I use that burned disk to install 8.04 on this computer then, rather than waiting for a disk to come in the mail?

---

### Post by sailthesea on 2009-06-13
> **scatmandude said:**
> This is probably a dumb question, but, if I use another computer that has a CD burner on it to make a CD copy of 8.04 could I use that burned disk to install 8.04 on this computer then, rather than waiting for a disk to come in the mail?

 Sure Make an image of Hardy Heron 8.04 but be careful to make a faithful copy and you should be fine That is a supported distribution and if you have internet can you can easily upgrade a bit later
 Go to to the "get ubuntu" bit on the forums its very simple
 After that its just a case of installing media support (a few lines in terminal) and your off!
 Good luck!

---

### Post by scatmandude on 2009-06-13
Thanks to you, hansdown and synapsys for all the help.

I'll post back when I get it installed to let you all know how it went.

Thanks again.


                                 S.

---

### Post by hansdown on 2009-06-13
I've been trying to edit my last post, but it's not working too well,

ergo; this addendum.

Please don't take this wrong, but it is in your best interests to "not"

shut down with the power button.It can result in the loss of your 

important data.

This is the preferred method; 

[http://ubuntuforums.org/showthread.php?t=617349](http://ubuntuforums.org/showthread.php?t=617349)

---

### Post by scatmandude on 2009-06-15
Just an update for everyone. I managed to successfully install 8.04 "Hardy" by using the update manager. This approach apparently bypasses the lack of CD burner issue for some reason. Since I upgraded most of the OS problems I was encountering have disappeared and I've also been able to further install the necessary codecs for sound and video.

I still haven't completely resolved the issue I mentioned in another thread where I have to scroll sideways as well as up and down on most websites, I've improved it by adjusting the font size using CTRL +/-, and tinkering with the screen resolution, but that only improved it so much. It's at least workable and only mildly irritating now. A friend suggested to me that I might have the wrong monitor driver in my hard drive tower, I don't know.

But overall things have improved greatly since I upgraded to 8.04.

Thanks again for all the help, everyone.


                             S.

---

### Post by hansdown on 2009-06-15
Glad you fixed it up scatmandude.

---

