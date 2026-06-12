---
title: "All browsers completely broken"
date: 2009-05-07
forum: General Help
---

### Post by dunkirk on 2009-05-07
What's going on with 9.04? I can't keep a web browser running on it to save my life. Not Firefox, Epiphany, or Shiretoko, and not even binary versions of Firefox or Opera. There are lots of threads about this, but no solutions. The one that claims success (removing wins from nsswitch.conf) doesn't apply to my setup.

I'm running on a netbook. Running a browser is 90% of my use. Heck, it's the majority of use on ANY computer any more. This ought to be taken for granted, and it's busted.

People have suggested that it's flash. I've tried removing flash; that doesn't work.

I've run firefox in a debugger. Without loading about a hundred different .dbg deb's (that I wouldn't know how to group, specify, and load), I get pretty limited information, but the backtrace pointed to javascript. I've tried the java6, java5, and the icedtea plugins. None of that has made a difference.

And please don't suggest that I just turn OFF flash or js. The current situation is that you simply need these things to "use the internet" these days. They have to work on any modern OS.

I've been using Linux since '94, and I've been using it as my main desktop both at work and at home for over 10 years now. I've used lots of distros over that time, and I'm currently a Gentoo fan. What I'm trying to say is that this ain't my first rodeo. I'm not doing something stupid. Something is fundamentally broken, and I wish I could find out what it is. Doesn't anyone here know what I could do to fix this?

Obviously, lots of people are having this problem. But equally obvious is that most people don't. I'm brand new to Ubuntu. How do I help track this down? What sort of steps do I need to take, what sort of information do I need to gather, and where do I need to post it to shed some light on this?

---

### Post by krishna_iyer on 2009-05-07
ok here is a suggestion... since i use the v8.1 and you are on v9.04

try uninstalling the default FF browser installation and install a fresh downloaded copy from mozilla.org..

That will isolate the problem.. to run flash you will need additional files from adobe. the v10 works fine on my v8.1 64bit

hope it helps.

---

### Post by salvachn on 2009-05-07
You can try another version, 8.10 works great.

---

### Post by dunkirk on 2009-05-07
When I said "binary versions," I meant ones I had downloaded. They exhibit the same behavior. So it must be something deeper than just firefox or even xulrunner.

No offence, but I don't want to try anything earlier. I came to UNR because it would be easy to install and get all the power management and such working, right out of the box. I could put Gentoo on it, but it would take 3 days of compiling, and then a week of twidling, and I don't want to hammer the SSD with all that compiling.

At this point I'm even considering trying the Win7 RC. I hate Windows as much or more than the average Linux user, but I HAVE to have a browser that works on this thing. That's what I bought it for.

So can anyone tell me how to setup debugging so that I can get to a layer LOWER than xulrunner?

---

### Post by BslBryan on 2009-05-07
Hello, dunkirk. :-)

I'm really sorry that everything I was planning on suggesting seems to have already been attempted.

I will say, though, that 8.10 is still relatively new.  It will be five months before it's even been around for a year.

8.10, simply due to the passage of time, is much more stable for more people than is 9.04.  

I really think that if you'd go so far as saying that you hate Windows, downgrading one version would certainly be the better option.  

That's just my two cents.  

I've also spent the last twenty minutes trying to find *anyone* with your problem, to see if there were any untried potential solutions, but no luck.

Keep us posted, please? :popcorn:

Good luck.

---

### Post by dunkirk on 2009-05-08
In trying to get a USB memory stick configured to install another operating system, I tried to format it with NTFS. But the `mkntfs' command wasn't available. I double-checked, and, sure enough, the ntfsprogs package was installed. However, the files WERE NOT THERE. So I marked it for reinstallation, and that went fine. However, THEN I found out that libntfs wasn't installed either, and it also was shown as being on the system.

What's going on here? Debian/Ubuntu is supposed to have great package management. In 3 years of using Gentoo, I've never seen anything like that. (Sure, it's got it's own problems, but I've never seen it think there was a file that didn't exist.) Perhaps this is part of my problem with trying to get a web browser to work? I'm really still just a Debuntu noob. Is there any way I can run a "self-check" to make sure that everything's installed correctly?

---

### Post by dunkirk on 2009-05-08
OK, I'm still considering moving to Ubuntu 8.04 or 8.10 with UNR packages bolted on, but while I'm still sorting this out, I wanted to post what I found. I did a miniscule amount of Googling and didn't find anything promising, so I brute-forced a check against what apt thought I should have, and what I actually had on the filesystem. It went something like this:

for i in `cat installed`; do echo $i >> errors; for j in `dpkg-query -L $i`; do ls $j >> /dev/null 2>> errors; done; done

Looking over the results, I found the following packages were missing files on the filesystem. So I reinstalled:

dictionaries-common
epiphany-extensions (!)
gnome-system-tools
keyutils
libdebconfclient0
libdebian-installer4
libecryptfs0
libparted1.8-10
linux-firmware
localechooser-data
notify-osd
os-prober
rdate

A follow-on check after reinstalling shows that there are still packages that give me problems about "too many levels of symbolic links." Specifically, for instance, epiphany-extensions. /usr/share/gnome/help/epiphany-extensions/C/figures/epi-ext-action-use.png is a link that points back to itself. There are a handful in several packages. I can't imagine that this is a problem that's causing crashing of the browser, since the problem exists in a directory called "help," which I take to mean that it's a problem when accessing the help pages, but I could be wrong.

---

