---
title: "LPIA 8.10 on Dell Mini 9"
date: 2008-11-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Dittohead on 2008-11-08
The version of a ubuntu that comes with the Mini 9 is built for the LPIA architecture. I know the i386 version will work but I'd rather use the LPIA version. Thanks!

Has anyone got it working? All the tutorials that I've seen use the i386 builds.

---

### Post by RichTJ99 on 2008-11-08
While this doesnt answer your question, I thought the standard 8.10 works on the mini 9?

---

### Post by jbloodwo on 2008-11-09
> **Dittohead said:**
> The version of a ubuntu that comes with the Mini 9 is built for the LPIA architecture. I know the i386 version will work but I'd rather use the LPIA version. Thanks!

Has anyone got it working? All the tutorials that I've seen use the i386 builds.
The LPIA works fine.... the tutorials you are seeing are either people that either orderd the windows version with the intention of making it a Linux system.   or some people dont like the dell remix and in both cases you are seeing the instructions for the i386 build because that is the standard download ISO..

---

### Post by cohesion on 2008-11-10
I'm new to ubuntu, but the 8.10 update doesn't show up from the dell repositories, when you change to the normal ones the url for the repositories includes an invalid architecture I guess

```
http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz
```

And other similar.

I'm confused. :\

---

### Post by jmdh on 2009-01-07
> **cohesion said:**
> I'm new to ubuntu, but the 8.10 update doesn't show up from the dell repositories, when you change to the normal ones the url for the repositories includes an invalid architecture I guess

```
http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz
```

And other similar.

I'm confused. :\

I think you'll need to install from ports.ubuntu.com (which I believe includes the security updates too) for the lpia architecture.

---

### Post by armandh on 2009-01-07
8.04.1 and 8.10 while marked I386 will install fine to the low power mini9; earler ubuntu does not work out of the box. 
I know this first hand 

here is my understanding
8.04.1 and 8.10 include the necessary instruction sets and are used live and/or installed when low power chips are detected.

my conclusion
the dell 8.04 is a lite version striped of unneeded code
[some I wanted] with the low power instructions added

I am running regular 8.10 [much better features/support.]

---

### Post by entropic_existence on 2009-01-21
I noticed on the Ubuntu download page that under the alternate install discs is an lpia architecture image for 8.10. If you want the lpia custom kernel than I am sure this is the route to go as far as the install of 8.10. I know the i386 works fine but it is always nice to have your kernel customized for your architecture. There should be improvements in battery life with the lpia kernel because it will have better power management.

I'm waiting for my Mini 9 to arrive and I think I will try upgrading to 8.10-lpia after I get it and then install the netbook remix.

---

### Post by anjilslaire on 2009-01-21
I'm not seeing the 8.10 lpia ISO on ubuntu.com under the alternate install. Can you link?

Thanks

EDIT:
Ah, found it I think. Not an ISO, but an IMG:

ubuntu-8.10-mid-lpia.img

---

### Post by Ancalagon82 on 2009-01-21
What would be the cost/benefits of changing to 8.10 lpia from Dellbuntu?

---

### Post by entropic_existence on 2009-01-21
I found the iso here:
[http://cdimage.ubuntu.com/ports/releases/8.10/release/ubuntu-8.10-alternate-lpia.iso](http://cdimage.ubuntu.com/ports/releases/8.10/release/ubuntu-8.10-alternate-lpia.iso)

---

### Post by Ancalagon82 on 2009-01-22
How does one go about getting an upgrade?


What's the different between an ISO and an IMG?

---

### Post by armandh on 2009-01-23
an .iso is what makes a standard optical disk image
[http://en.wikipedia.org/wiki/ISO_image](http://en.wikipedia.org/wiki/ISO_image)

---

### Post by fedleo on 2009-01-23
> **entropic_existence said:**
> I found the iso here:
[http://cdimage.ubuntu.com/ports/releases/8.10/release/ubuntu-8.10-alternate-lpia.iso](http://cdimage.ubuntu.com/ports/releases/8.10/release/ubuntu-8.10-alternate-lpia.iso)
And how did you install it? Installation ends with an error because it can not find the correct kernel architecture for mini 9. I can continue without a kernel but... after?

---

### Post by entropic_existence on 2009-01-23
> **Ancalagon82 said:**
> How does one go about getting an upgrade?


What's the different between an ISO and an IMG?

Just different disk image formats. .img is also a type of disk image format used by Macs. ISO's are an open standard disk image format so basically all burning software can use it.

---

### Post by entropic_existence on 2009-01-23
> **fedleo said:**
> And how did you install it? Installation ends with an error because it can not find the correct kernel architecture for mini 9. I can continue without a kernel but... after?

I haven't tried to install it. I am still waiting on my Mini 9 to arrive but I had come across that source for an ISO in my research on what to do with my Mini after it arrives. Although if it is an lpia ISO there should already be an lpia architecture kernel on the disc. Not sure why there are errors.

You could always custom compile a kernel.

---

### Post by fedleo on 2009-01-23
> **entropic_existence said:**
> You could always custom compile a kernel.Isn't simple as you may think. There's a [well know bug]("https://bugs.launchpad.net/ubuntu/+source/base-installer/+bug/291670") on this iso. And compiling for lpia is really difficult. Trust me. :(

---

### Post by entropic_existence on 2009-01-23
> **fedleo said:**
> Isn't simple as you may think. There's a [well know bug]("https://bugs.launchpad.net/ubuntu/+source/base-installer/+bug/291670") on this iso. And compiling for lpia is really difficult. Trust me. :(

Yeah I actually just came across that after I posted. Many people seemed to have had success with the work around posted in the thread linked to that bug report.

---

### Post by Ancalagon82 on 2009-02-22
So any update on this?   How hard is it to put 8.10 lpia on a Dell Mini9?

---

### Post by skunkbad on 2009-02-22
I'm using the std 8.10 on my mini, and it works great. I really don't know what all of the benefits of LPIA would be, but I've heard other people in this forum say that std 8.10 is optimized for SSDs. By the time I need a new SSD, they'll be so big and cheap I'll want to upgrade anyways.

---

### Post by entropic_existence on 2009-02-22
> **skunkbad said:**
> I'm using the std 8.10 on my mini, and it works great. I really don't know what all of the benefits of LPIA would be, but I've heard other people in this forum say that std 8.10 is optimized for SSDs. By the time I need a new SSD, they'll be so big and cheap I'll want to upgrade anyways.

I have the LPIA version installed and running on my mini, one of the main reasons to use it is that it is optimized for these low power processors and from what I have heard does give you an improvement on battery life.

It was a little tricky to install, I found that it didn't work exactly as laid out in the how-to thread I used (I think linked further up this thread) but that worked as a general guide. Just be prepared for there to be a bunch of apparently broken packages, which somehow resolve themselves when you install GRUB and then do an apt-get upgrade.=

If you aren't comfortable with the command-line I wouldn't recommend it otherwise just go for it. I hear that the next version of Ubuntu the LPIA version is going to be much better put together.

---

### Post by skunkbad on 2009-02-22
> **entropic_existence said:**
> ...one of the main reasons to use it is that it is optimized for these low power processors and from what I have heard does give you an improvement on battery life....

I'm getting about 4 hours battery life on a full charge. My mini is only about a week old, so the battery is new, and that might be why it seems long to me. What are you getting?

---

### Post by entropic_existence on 2009-02-23
> **skunkbad said:**
> I'm getting about 4 hours battery life on a full charge. My mini is only about a week old, so the battery is new, and that might be why it seems long to me. What are you getting?

I'm getting pretty similar, somewhere between 4-5 hours typically.

---

### Post by Arndtwe on 2009-02-23
> **skunkbad said:**
> I'm getting about 4 hours battery life on a full charge. My mini is only about a week old, so the battery is new, and that might be why it seems long to me. What are you getting?

I've had my Ubuntu mini9 for about three months now and I get almost 4 hours battery life out of it. I am running 8.04, not 8.10

---

### Post by entropic_existence on 2009-02-23
> **Arndtwe said:**
> I've had my Ubuntu mini9 for about three months now and I get almost 4 hours battery life out of it. I am running 8.04, not 8.10

If it is the 8.04 that shipped from Dell that is the lpia architecture and not i386. Of course you may have replaced Dellbuntu with the standard i386 flavour of Ubuntu.

---

### Post by Arndtwe on 2009-02-23
> **entropic_existence said:**
> If it is the 8.04 that shipped from Dell that is the lpia architecture and not i386. Of course you may have replaced Dellbuntu with the standard i386 flavour of Ubuntu.

It is the Dell shipped i686 version not i386...

---

### Post by entropic_existence on 2009-02-23
> **Arndtwe said:**
> It is the Dell shipped i686 version not i386...

The Dell Shipped 8.04 is lpia not i686 so far as I am aware.

---

### Post by Seq on 2009-02-23
> **entropic_existence said:**
> Just different disk image formats. .img is also a type of disk image format used by Macs. ISO's are an open standard disk image format so basically all burning software can use it.

The .img file is a USB disk image. It is likely available as most LPIA machines can be assumed to not have an optical drive. According to the description on my [randomly chosen mirror]("http://ubuntu-releases.wallawalla.edu/8.10/"):

"MID USB image for Low-Power Intel Architecture computers (USB image)"

(Also, the OS X disk image format is .dmg)

---

### Post by entropic_existence on 2009-02-23
> **Seq said:**
> The .img file is a USB disk image. It is likely available as most LPIA machines can be assumed to not have an optical drive. According to the description on my [randomly chosen mirror]("http://ubuntu-releases.wallawalla.edu/8.10/"):

"MID USB image for Low-Power Intel Architecture computers (USB image)"

(Also, the OS X disk image format is .dmg)

You're absolutely right, the .img format was originally for floppy disks so it makes sense that USB drives appropriated it. And yes .dmg is the Mac OSX one.

---

### Post by Arndtwe on 2009-02-24
> **entropic_existence said:**
> The Dell Shipped 8.04 is lpia not i686 so far as I am aware.

My machine is 2.6.24-19-lpia on i686. This is what Conky reports. If this is incorrect then I do not know what else to tell you.

---

### Post by entropic_existence on 2009-02-24
> **Arndtwe said:**
> My machine is 2.6.24-19-lpia on i686. This is what Conky reports. If this is incorrect then I do not know what else to tell you.

Exactly, it's an LPIA architecture. The i686 in this case is because the intel processor does do hyperthreading (which emulates having two processors). Usually if someone just says something is the i686 kernel I would think that it is a standard i686 kernel install.

---

