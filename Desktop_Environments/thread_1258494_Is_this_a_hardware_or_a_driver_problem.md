---
title: "Is this a hardware or a driver problem ?"
date: 2009-09-05
forum: Desktop Environments
---

### Post by tuxolero on 2009-09-05
Hi there,

I have a strange effect on my desktop:
When I move the mouse over a link or an image, a colored bar appears, hiding most of the screen. Below the colored bar, there is a black bar, hiding the rest (see attachment).
The position the bars moves with the the mouse position, where the colored bar has always the same height. So, sometimes the black bar disappears when the position of the colored bar is too near the bottom of the screen.
The color of the colored bar depends on the color under the mouse.

Note on the attachment:
It is a photograph of the screen, where the colored bar appears like it has a color gradient. But in reality, it has one plain color. 

My graphics chip is a NVIDIA GeForce 8200 on-board a MSI K92GM-FIH mainboard with currently 256M shared memory.
I am using the recommended NVIDIA driver version 180, but I also tried the other available driver version 173 without change.

Although I am using Kubuntu, I specified "all variants" because I do not think it depends on the desktop.


Has anyone seen this or a similar effect too (on any hardware) ?

Does anyone use the same graphics chip or even the same mainboard and is the effect there too ?

What was the cause, how could it be fixed ?

Thanks in advance,
Markus

---

### Post by QIII on 2009-09-05
Is this a persistent problem between shutdown and the next startup?

---

### Post by tuxolero on 2009-09-05
The effect occurs always and all time, from login to logout.

---

### Post by QIII on 2009-09-05
If you are not worried about the use of a little more disk space, and can stomach having to choose between Gnome and KDE at login for a while, it might be worth installing Gnome to see if it happens there, too.

Rule that out.

I don't remember having issues uninstalling KDE or Gnome when I experimented around with using each -- but I can't guarantee there won't be issues.

---

### Post by ckonestroh on 2009-09-05
This is the short answer..... To a long problem....  Note this is not my experience or due I take credit for this post....


I feel all your pain.
I went through endless fixes with ubuntu, none of which either lasted or worked at all.
Then I ran mint for a couple of months, which is similar to ubuntu but has more options and less problems.

A couple of months ago I got a sabayon dvd from ebay and finally installed it yesterday.
The install was flawless, the screen resolution is PERFECT, no hassles, VIOLA!!!!!!

All this time I thought the issue was biostar and nvidia, but the issue was ubuntu.
My recommendation is to get a sabayon dvd, and use sabayon for your os.





following data came from this post on the last page.....


[http://ubuntuforums.org/showthread.php?t=822315]("http://ubuntuforums.org/showthread.php?t=822315")


Good luck...

You don't need to Sabayon Dvd just head over to distrowatch.com

Its a sexy desktop Based off of Gentoo...

Gentoo has been around for ever... Install can be a bit tricky...


download here...

[http://sabayon.linuxfreedom.com/download.html]("http://sabayon.linuxfreedom.com/download.html")

---

### Post by QIII on 2009-09-05
That poster may not have been aware that Mint is a variant of Ubuntu, so that may begin to rule out Ubuntu as the culprit...

That said, the issue of drivers is not a ding on Ubuntu or any other Linux distribution.

Hardware OEMs write drivers.  Windows doesn't write drivers.  The various distributors of Linux do not write drivers.

OEMs do.  

If a Linux driver is not available from the OEM (which is becoming less and less common), the best that any Linux distributor can do is depend on the open source community to make the best attempt possible to create a driver in the absence of a proprietary one.

Clearly, it doesn't always work.

However, nVidia has been doing a bang-up job of providing Linux drivers, but with all the flavors of Linux out there, they can't produce something that will work in every one of thousands of combinations of Linux and user configurations.

And even the much-maligned AMD/ATI cards are getting better and better Linux support.

So let's not go blaming Ubuntu out of hand.  Are there other distros that will work for the OP?  Probably.  Until he adds a different card that, unfortunately, does not work for his tailor made configuration.  Simply saying "I had a problem and I was running Ubuntu, so Ubuntu is bad" does not address the root cause.  It is a hasty generalization based on an experimental sample size of one.  Nobody comes on a forum to say they aren't having problems, so the argument also has the element of the logical fallacy of the Argument from Ignorance/Silence.

Rather than jumping from distro to distro, it would benefit ALL distros for those using each one to attempt to fix the issue, make the fix available in forums like this and report bugs as appropriate in each community.

Switching to a new distro doesn't help anyone solve the problem.

It simply avoids it.

(However, I'm not an Ubuntu apologist so I don't fault anyone for going to a new distro based on their preference or needs.  Whatever works for a user works, and that is what having so many choices is all about.)

---

### Post by ckonestroh on 2009-09-05
Look after 15 years of using Linux/Windows/Mac/Unix/Novell all I was trying to do is introduce a solution to the immediate problem which is the video card is out of range....

This problem could lead to video card burning up and motherboard taking a dive... Then it goes from a 80 dollar fix to a 300 dollar fix... 


Bye the Video Card overheating this could cause electro magnetic build up numerous other electronic parts...

QIII I find what you say to be very disturbing 

1. Ubuntu and Mint are based off of Debian...
2. Gnu --- free license to take the code make it free allows you to make it better for your use just need to make reference to original code...

3. You make it sound as if all research I did was based off of one thread no I looked up NVIDIA forums to see numerous posts on same or similar problems with Geforce 8200 both in laptop and desktop....

4. You pounding your chest about Ubuntu is not resolving the issue...

THE ISSUE IS A OUTRAGE VIDEO CARD.....

Not which Linux Flavor is better.....

Now after a bit of research I found there are problems with 7600, 8200, 8400 and 9200 nvidia video cards running under Ubuntu... That is a small range of video card issues for a OS....  

What a programmer needs to do is look at why those video cards and motherboards are having issues...

I found some issues were with sata hard drives which really don't have anything to do with Ubuntu ,but the type of sata hard drive the individual was using....

Final thought you didn't even consider the following...

Hardware --- motherboard maker, video card maker, network card maker, sound card maker or hard drive maker.....


I went futher with this motherboard reviews....


[http://www.itreviews.co.uk/hardware/h1674.htm]("http://www.itreviews.co.uk/hardware/h1674.htm")

Now if you look at issues it states that with a Nvidia setup it needs lots of air blow in across the gpu to run within limits...

I read Amazon review that stated his board failed out right...


Conclusion maybe you should consider if this motherboard, video card has issues even before running Linux?


The last post I answered about a 7600 nvidia card hand 20 or 30 posts on nvidia forums stating it was having a hard time running under windows...

What makes anyone think that changing OS'S will resolve the issue?????

Windows is bad ,but not based on hardware support!!!!!

---

### Post by QIII on 2009-09-06
> **ckonestroh said:**
> This problem could lead to video card burning up and motherboard taking a dive... Then it goes from a 80 dollar fix to a 300 dollar fix... 

 QIII I find what you say to be very disturbing 

1. Ubuntu and Mint are based off of Debian...
2. Gnu --- free license to take the code make it free allows you to make it better for your use just need to make reference to original code...

3. You make it sound as if all research I did was based off of one thread no I looked up NVIDIA forums to see numerous posts on same or similar problems with Geforce 8200 both in laptop and desktop....

4. You pounding your chest about Ubuntu is not resolving the issue...

Look.  After more than 20 years more than you have had using various operating systems...

1.  Ubuntu is a Debian derivative.   Anything derived from Ubuntu is also, therefore, derived ulitmately from Debian.  But Mint is directly derived from Ubuntu.  Read the documentation on Mint.  "Originally launched as a variant of Ubuntu with integrated media codecs..."

2.  Uh.  I know what the GNU GPL and the GNU LGPL are, thank you.  Please take a moment to take a look at my profile and see what I do for a living.  And please note that this comment has nothing at all to do with my post.

3.  No.  Actually, my comment was about the post you referenced.

4.  Not pounding my chest about Ubuntu.  See the last sentence of my post.  In fact, please re-read my entire post.  I often recommend other operating systems.  I even said in this post that there is probably a different OS that would work for the OP. In other posts, I have even recommended sticking with (cough, hack) Windows where appropriate.

Finally:  The reason that Microsoft has "hardware support" is not because Microsoft "supports" hardware.  It is because OEMs bend over backwards to make sure that their products work with the Wintel world.  Microsoft requires OEMs and software vendors to seek the vaunted compatibility certification.  (In case you were wondering, I hold several Microsoft certifications for just that reason.)  Canonical does not have the market share and the power derived from that to twist the OEMs into compatibility compliance with Ubuntu.  The open source community has no such power.  So what we are left with is what support the OEMs will give (remember that they are going for profits, not altruistic support of the Linux community) or the efforts of the open source community to provide what is not provided by the OEMs.

I've been at this game more than just a couple of days.

As for the OP's original post:  My suggestion was to try Gnome rather than KDE to rule that out as a potential issue.  The potential hardware issues may be known.  They are not necessarily the root causes of his difficulties.  Troubleshooting is more often a process of eliminating possible sources of undesirable performance than it is making assumptions.

---

### Post by tuxolero on 2009-09-07
I have just sent a bug report to NVIDIA directly.
I'm very curious for the reply.

---

