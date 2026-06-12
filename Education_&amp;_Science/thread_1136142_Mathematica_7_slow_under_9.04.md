---
title: "Mathematica 7 slow under 9.04"
date: 2009-04-24
forum: Education &amp; Science
---

### Post by Buendia on 2009-04-24
Hi,

After upgrading to 9.04 from 8.10 mathematica notebooks run very slowly. Running 'math' from the command line is fine though.

When mathematica frontend is running, both MathKernel and Mathematica processes consume 15% - 20% of the cpu, while no notebook is running.

Anyone else having the same problem?

---

### Post by hpsch on 2009-04-27
Hello

I have the same problem. It was faster on 8.10 than on 9.04.
Thats especially a problem, because i am using a Netbook (Asus 1000H) and the Atom CPU isn't very powerful.
Its nearly unusable.

I tried to use the sun java jre too, but its no difference, its still very slow.

MathKernel, Mathematica and Java use 100% CPU power all the time. Also xorg seems to use more cpu when Mathematica is started and I click around in the window.
As far as i can remember, that wasn't the case with Ubuntu 8.10.

Any ideas?

br
HPS

---

### Post by neoflight on 2009-04-27
Try reinstalling the fonts. May be that will help.
Here is a [guide]("http://gears.aset.psu.edu/hpc/software/math/mathem/fonts.shtml") how to do this

---

### Post by hpsch on 2009-04-28
I've tried it. I haven't noticed any difference.

I tried a few other things:
Using the system libraries (moved all libQT* and other libs that are already installed out of SystemFiles/Libraries/Linux).
Also no difference, except, that the GUI now looks a bit more like Ubuntu (uses the system QT libs with the Ubuntu style now).

But it also makes no difference...

On my desktop PC i can use it, but only because it has enough power. Mathematica uses also much CPU power there. So its definitly no hardware or graphics driver thing (but maybe another xorg related problem?)

Hope someone finds a solution.

br
HPS

---

### Post by Buendia on 2009-04-28
I thought this happened to me because fglrx is no more supported for my ati card and the xorg driver is too slow. Can you confirm that mmt is still slow when you have your GPU manufacture driver installed?

Mathematica notebook interface under linux has always been a mess anyway.

---

### Post by hpsch on 2009-04-28
Confirmed.

I am using Mathematica 7 on Ubuntu 9.04 with an Intel 945GME on my netbook with the xorg drivers shipped with Jaunty

and

I am using Mathematica 7 on Ubuntu 9.04 with an Radon 4870 on my pc with the fglrx drivers installed with the hardware driver thing in Jaunty.

br
HPS

---

### Post by Buendia on 2009-04-28
It should be reported to wolfram then. Please send us the link to the mailinglist post if you're planning to do so. Unfortunately, their mailinglist is moderated in an ancient way and it could take up to 24 hrs before your post appears to everyone.

---

### Post by atarisal on 2009-04-30
Hi All,

Using Mathematica 7 in Ubuntu 9.04 I have problems with charts created by Plot3D. After running this function, The plot is not displayed. Trying to rotate the plot, I can see it , but the fonts are unreadable. 2D plot woks very well. I try to reinstall the fonts, but it does not differences. I have a Intel 945GME on my Notebook. When run Mathematica, I get :

  Failed to initialize GEM.  Falling back to classic.

I have not noted so much differences about CPU Consumption. Any ideas??

Thanks to all!

---

### Post by crowlogic on 2009-04-30
I can confirm the same problem.. my system is


Description:    Ubuntu 9.04

Linux e510 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux


Mathematica 7.0 for Linux x86 (64-bit)

MathKernal, Mathematica, and java process all using about 15% continually.

Strace shows an insane amount of select/futux/kill systemcalls.

java version "1.6.0_13"
Java(TM) SE Runtime Environment (build 1.6.0_13-b03)
Java HotSpot(TM) 64-Bit Server VM (build 11.3-b02, mixed mode)

---

### Post by Buendia on 2009-04-30
Has anyone introduced this shame to wolfram? (the company not the person, you can go for the latter too if you feel like it)

Please send us the links to your posts if so.

---

### Post by Buendia on 2009-04-30
> **crowlogic said:**
> 

MathKernal, Mathematica, and java process all using about 15% continually.

Strace shows an insane amount of select/futux/kill systemcalls.

java version "1.6.0_13"
Java(TM) SE Runtime Environment (build 1.6.0_13-b03)
Java HotSpot(TM) 64-Bit Server VM (build 11.3-b02, mixed mode)


Java? I thought they just use QT for the frontend?

---

### Post by mi.kop on 2009-05-01
> **atarisal said:**
> Hi All,

Using Mathematica 7 in Ubuntu 9.04 I have problems with charts created by Plot3D. After running this function, The plot is not displayed. Trying to rotate the plot, I can see it , but the fonts are unreadable. 2D plot woks very well. I try to reinstall the fonts, but it does not differences. I have a Intel 945GME on my Notebook. When run Mathematica, I get :

  Failed to initialize GEM.  Falling back to classic.

I have not noted so much differences about CPU Consumption. Any ideas??

Thanks to all!

Plot3D works on my intel945. (ubuntu9.04).
Try using the new UXA as acceleration method. (this should at least solve the GEM issue...)
To do so change your xorg.conf "Device" section to:

```
Section "Device"
    Identifier    "Configured Video Device"
    Option        "AccelMethod"            "uxa"
EndSection
```...oh and the Mathematica FrontEnd is terribly slow :(

HTH
mi.kop

---

### Post by rofman on 2009-05-01
Same problem, however,
Mathematica 6 seems fine.
Also Mathematica 7 with Ubuntu 9.04, kernel 2.6.27-11-generic 
seems OK.

I have x86_64.

---

### Post by Buendia on 2009-05-03
> **rofman said:**
> Same problem, however,
Mathematica 6 seems fine.
Also Mathematica 7 with Ubuntu 9.04, kernel 2.6.27-11-generic 
seems OK.

I have x86_64.

Thanks, that worked for me on 32 bit 9.04, as a temporary solution.

---

### Post by kaspar_silas on 2009-05-04
Hi Guys,

I have mathematica 7 running fine on the most recent 9.04 on a dell opltiplex (64bit) and An Asus 900 (jaunty netbook remix). I find it a bit locky (very annoying as it never recovers work if it locks) but it's definitely not worse or slower than under 8.10. 

Sorry this isn't more helpful but I thought I would mention it in case it's useful in fault chasing.

---

### Post by correaa on 2009-05-05
same here. The frontend of Mathematica 7 is very slow in 9.04.
Also I noticed that the "theme colors" of the front end, do not adapt to ubuntu colors as Mathematica 7 did in 8.10. (e.g. selections are blue and not orange).

EDIT: the frontend crashes frequently, for example on printing or after quiting the kernel from the menu.

---

### Post by Michael Knap on 2009-05-06
I also have the same problem; and one consequence of this is that my laptop gets too hot very quickly. I generally shutdown Mathematica after 15-20 minutes of use because the temps on both of my cores skyrocket to what I think is an unhealthy level for extended use. As other replies have mentioned, I too have suspected Java, but I do not know for sure. 
I would also love to get the interface more Ubuntu-like, but I understand that Mathematica uses a different widget library (QT i think) than the standard Ubuntu's Gnome DE (GTK).
I've never had sound in Mathematica, but would love to hear it. 

Ubuntu 9.04, kernel 2.6.28-11-generic (64)
Mathematica 7.0.0 (64)
HP Pavillion dv2000
Intel Core 2 Duo w/ nVidia

---

### Post by Buendia on 2009-05-07
> **Michael Knap said:**
> I also have the same problem; and one consequence of this is that my laptop gets too hot very quickly. I generally shutdown Mathematica after 15-20 minutes of use because the temps on both of my cores skyrocket to what I think is an unhealthy level for extended use. As other replies have mentioned, I too have suspected Java, but I do not know for sure. 
I would also love to get the interface more Ubuntu-like, but I understand that Mathematica uses a different widget library (QT i think) than the standard Ubuntu's Gnome DE (GTK).
I've never had sound in Mathematica, but would love to hear it. 

Ubuntu 9.04, kernel 2.6.28-11-generic (64)
Mathematica 7.0.0 (64)
HP Pavillion dv2000
Intel Core 2 Duo w/ nVidia

Install, if required, kernel 2.6.27-11-generic, and boot into it to use mathematica normally.This solution should work until the bug is resolved.

---

### Post by Michael Knap on 2009-05-07
Thank you for the reply, but I can't seem to find that package. Is it in a certain repository? It doesn't seem like you compiled that yourself..

---

### Post by Buendia on 2009-05-07
> **Michael Knap said:**
> Thank you for the reply, but I can't seem to find that package. Is it in a certain repository? It doesn't seem like you compiled that yourself..

Since I upgraded from 8.10 the kernel image was already installed. Installing the debian on 9.10 *might* help:

[https://launchpad.net/ubuntu/intrepid/i386/linux-image-2.6.27-11-generic/2.6.27-11.31](https://launchpad.net/ubuntu/intrepid/i386/linux-image-2.6.27-11-generic/2.6.27-11.31)

---

### Post by Michael Knap on 2009-05-08
Thank you for your information. I haven't yet tried to regress to the 2.6.27 kernel, though. I am looking for a documented way to do this or thinking about trying the pre-release repo for jaunty... it has a 2.6.28-12 kernel available. It likely doesn't address what is happening here, but you never know.

---

### Post by hpsch on 2009-05-10
I am going to try Mathematica 7.0.1 now and see if it helps.

Because you noticed a difference with kernel 2.6.27, it can really be a problem with the kernel. I noticed, that the newer kernels (>=2.6.28 ) cause a lot more wakups from time to time than the older ones (tested with powertop). I found a few reports about that and it seems to be a regression in the newer kernels. Maybe thats somehow connected.
But anyway, i am going to try 7.0.1 and report back here.

Maybe i am going to try the last 2.6.30er rc too and look if something changed.

@correaa:
Because of the colors, you can delete (or better move away) the libQt* files from /usr/local/Wolfram/Mathematica/7.0/SystemFiles/Libraries/Linux (or  Linux-x86-64) and use the system libraries instead.
Of course libqt4 and related packages (sudo apt-get install libqt4-svg should be doing the trick) have to be installed.

---

### Post by kimyoungil on 2009-05-10
Seems to work. I've switched back from kernel 2.6.28.11 to kernel 2.6.27.11 now, and the first impression is good. (still not very fast, but now it's usable on AMD 64 3500+)

:popcorn:

edit: hmm, processor activity was due to tracker, while typing processor-activity is now aroung 10%. (was 100%) so now it works fine. No lag.

Thnx bro.

---

### Post by Michael Knap on 2009-05-17
How did 7.0.1 turn out on newer kernels? Are there other differences? Noticable?

---

### Post by hpsch on 2009-05-17
Didn't notice any differences. Its still slow.

---

### Post by Michael Knap on 2009-05-17
Wow! What a quick reply! Thank you; did you try the later kernels too (2.6.30rc, I think you mentioned)?

---

### Post by hpsch on 2009-05-17
No not yet sorry. I hope i get the time to try it in the next few days.

---

### Post by ArchDefector on 2009-05-17
I experienced the same problem with 2.6.29 kernels on Arch Linux: Mathematica 7.0.1 was unusable due to the constant cpu load of above 80%, even when doing nothing.

Apparently this problem only occurs when using the GUI (i.e. Mathematica). When I use the console interface (math) instead, everything is fine and there is no cpu load at all when idling.

Today I finally tried an 2.6.27 kernel and the problem disappeared. So it seems that Mathematica has a problem with kernels newer than 2.6.27 and that this problem is not Ubuntu specific.

---

### Post by Michael Knap on 2009-05-18
Well, at least we seem to be getting to the bottom of this:

This appears to be a linux_kernel-mathematica_gui problem. And from other browsing, perhaps it is related to excessive wake-up.

Thanks everybody; I for one, would love to see this worked out pretty soon.

---

### Post by Buendia on 2009-05-18
> **Michael Knap said:**
> Well, at least we seem to be getting to the bottom of this:

This appears to be a linux_kernel-mathematica_gui problem. And from other browsing, perhaps it is related to excessive wake-up.

Thanks everybody; I for one, would love to see this worked out pretty soon.

This is not a linux issue, it's a mathematica issue and it should be reported to wolfram research.

---

### Post by Michael Knap on 2009-05-18
So, how do we go about making a concerted effort to supply a little noise to Wolfram? The squeeky wheel gets the grease.

---

### Post by Buendia on 2009-05-18
> **Michael Knap said:**
> So, how do we go about making a concerted effort to supply a little noise to Wolfram? The squeeky wheel gets the grease.

I see you have already written to them [here]("http://groups.google.com/group/comp.soft-sys.math.mathematica/browse_thread/thread/d039ced03fde30d5/58a6614473e129ae?lnk=gst&q=ubuntu+jaunty#58a6614473e129ae"). The answer you got is irrelevant, you may want to describe it with a more clear topic, or simply send them a link to this thread.

---

### Post by ArchDefector on 2009-05-18
> **Michael Knap said:**
> So, how do we go about making a concerted effort to supply a little noise to Wolfram?

How about a bug report at[ http://support.wolfram.com/submitabug.cgi]("http://support.wolfram.com/submitabug.cgi") ?

I tried this today but it didn't seem to work. Maybe somebody else has better luck than me.

---

### Post by Buendia on 2009-05-28
any news? any luck? anything at all? anyone heard back from wolfram?

---

### Post by dox_drum on 2009-05-28
> **rofman said:**
> Same problem, however,
Mathematica 6 seems fine.
Also Mathematica 7 with Ubuntu 9.04, kernel 2.6.27-11-generic 
seems OK.

I have x86_64.

I'm sorry, but I'd like to know how to do such `downgrading' of the kernel. 

Thanks a lot.

---

### Post by Michael Knap on 2009-05-29
I haven't been able to do it via ubuntu's package management. *However*, if you upgraded from Intrepid, you may be able to it. You may also be able to do if you add the Intrepid repositories to your apt-get sources in /etc/apt/sources.list either by hand or by using the GUI menu item System | Administration | Software Sources. 

Either way, I have not done so. Though the excessive processor usage is hard on my laptop, Mathematica 7 and Ubuntu Jaunty have been stable and usable, albeit a little warm. 

I have not heard anything from Wolfram about the issue. I am hoping a new kernel from ubuntu will perhaps address the issue.

---

### Post by ch3n3t0 on 2009-05-29
-- Wolfram Research Technical Support --

This is a response to your email.
The reply to your question can be found at the bottom of this message.
Our classification number for this message is: [TS 21421]
Please give this number in any future correspondence
related to this question. If you leave this number in
the Subject: header in the form [TS 21421], it will
automatically be reassigned to the original technician.

From: xxxxxxxxxxxxxxxxxxxxxxx
Date: Wed, 27 May 2009 00:09:37 -0500
Subject: Support Suggestion or Bug Form
To: [email]support@wolfram.com[/email]

Name:         xxxxxxxxxxxxxxxxxxxxxxx
Email:        xxxxxxxxxxxxxxxxxxxxxxx
Organization:
License:
Version:
OS:           ubuntu 9.04

Suggestion or Bug:
Mathematica 7.0.1 has a problem with linux kernels newer than 2.6.27, it runs so slowly

look [http://ubuntuforums.org/archive/index.php/t-1136142.html](http://ubuntuforums.org/archive/index.php/t-1136142.html)

----------------------------------------------------------------------------

Dear Elias Pizarro,

Thank you for the email.

Thank you for reporting this issue to us. We have been able to reproduce
this problem and are working on resolving this with a very high priority.
We will keep you fully posted on the progress regarding this issue.

It is reports like yours that makes our product great. Thank you for your
efforts in reporting this matter.

Please let me know if you have any questions.

I can be reached directly at:

217-373-3443
[email]vminer@wolfram.com[/email]


Sincerely,

Vincent Miner
Technical Support Supervisor
Wolfram Research, Inc.
[http://support.wolfram.com](http://support.wolfram.com)


----------------------------------------------------------------------------

If this issue is resolved, please consider taking a few minutes
to give us some feedback on your experience. Please visit
[http://support.wolfram.com/survey/?trackingnumber=21421](http://support.wolfram.com/survey/?trackingnumber=21421)
and give your honest answers to these three short questions.
Thanks for taking the time to help us improve.

Are you at the latest version of Mathematica? The latest version
of Mathematica is 7.0.1.  For more information:
[http://www.wolfram.com/products/mathematica/latestversion/](http://www.wolfram.com/products/mathematica/latestversion/)

Join us June 7-19, 2009 at the Advanced
Mathematica Summer School. Find out more
at [www.wolfram.com/summerschool](www.wolfram.com/summerschool)

---

### Post by Michael Knap on 2009-05-30
Wow. Thank you for communicating to Wolfram Research, and thank you for communicating with us.

---

### Post by Buendia on 2009-06-04
Any updates from wolfram?

---

### Post by Michael Knap on 2009-06-04
None here.

---

### Post by correaa on 2009-06-05
[QUOTE=kimyoungil;7250230]Seems to work. I've switched back from kernel 2.6.28.11 to kernel 2.6.27.11 now, and the first impression is good. (still not very fast, but now it's usable on AMD 64 3500+)

great, can you explain with more detail how to install an old kernel in Jaunty. I added 

  deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe 

to the repository list (/etc/apt/sources.list) but the old kernels do not appear.

Thank you,

---

### Post by Troffi on 2009-06-05
Hello all.
I have some problem with using Mathematica 7.01 on Ubuntu 9.04.
My native language is Russian. Often there is a need to use the records to insert in Russian. In the normal typing is no problem, but if you bring the document to print, instead of the letters appear obscure characters.
Can anyone suggest how to fix it?
Thanks in advance.

---

### Post by nutu on 2009-06-10
Any recent news as to how to make Mathematica 7.0 run faster on Ubuntu 9.0.4?

---

### Post by cbaltar2 on 2009-06-13
Ok guys, I'm glad I found this thread and I'm not the only person experiencing this with Mathematica 7. I'm getting the same problem on Ubuntu 9.04, and Fedora 11 (the latter has the 2.6.29 32-bit kernel). Basically, both systems show a 30% increase in CPU use with every Mathematica GUI window. With 3 windows open and nothing running, both CPUs run flat at 100%. I wasn't getting this problem on Intrepid and Mathematica 7. I'm also seeing a java process with each Mathematica window, which is strange. Killing the java process doesn't lower CPU use, but closing Mathematica does...

I'm kind of annoyed with the new kernel problems, and xorg issues on this latest Ubuntu 9.04 (I have an Intel chipset) and now I can't even do my work (my living has a lot to do with Mathematica programming). Very frustrating...

---

### Post by ch3n3t0 on 2009-06-19
From: jmartinez
Date: Fri Jun 19 15:25:16 2009
Subject: High CPU usage for Mathematica on recent linux kernel
To: [email]support@wolfram.com[/email]

----------------------------------------------------------------------------

Hello,

Thank you for the email. Sorry for the long delay on a solution to the CPU
usage problem on the latest Linux kernels.  Here is the patch instructions:

First download the file here:

[http://download.wolfram.com/?key=61JJHE](http://download.wolfram.com/?key=61JJHE)

and place it in
/usr/local/Wolfram/Mathematica/7.0/SystemFiles/Libraries/Linux

Then download these files:

[http://download.wolfram.com/?key=MK4ZR8](http://download.wolfram.com/?key=MK4ZR8)
[http://download.wolfram.com/?key=YHDAH4](http://download.wolfram.com/?key=YHDAH4)

and place them in
/usr/local/Wolfram/Mathematica/7.0/SystemFiles/Libraries/Linux-x86-64

That should solve the problem.  Let me know if you have any further
problems.

Sincerely,

Jason Martinez, Ph.D.
Technical Support
Wolfram Research, Inc.
[http://support.wolfram.com](http://support.wolfram.com)

---

### Post by correaa on 2009-06-19
I decided to attach the files to message in case wolfram decides to break the links.

First download the file here:

[http://download.wolfram.com/?key=61JJHE](http://download.wolfram.com/?key=61JJHE)

and place it in
/usr/local/Wolfram/Mathematica/7.0/SystemFiles/Libraries/Linux

Then download these files:

[http://download.wolfram.com/?key=MK4ZR8](http://download.wolfram.com/?key=MK4ZR8)
[http://download.wolfram.com/?key=YHDAH4](http://download.wolfram.com/?key=YHDAH4)

and place them in
/usr/local/Wolfram/Mathematica/7.0/SystemFiles/Libraries/Linux-x86-64

---

### Post by correaa on 2009-06-19
the situation is much better now, although java still uses 16% of my cpu all the time.

---

### Post by ArchDefector on 2009-06-22
> **correaa said:**
> the situation is much better now, although java still uses 16% of my cpu all the time.

The replacement of [FONT=Courier New]libML32i3.so[/FONT] dropped the idle cpu usage of Mathematica on my machine to ~16% too.

As I don't have any use for the Java integration of Mathematica, I then deactivated the JLink library by making its files unreadable, using some command like:

```

chmod a-x /usr/local/Wolfram/Mathematica/7.0/SystemFiles/Links/JLink

```Now Mathematica is usable under recent kernels and doesn't hog any cpu time at all when idle.

It's really a shame that Wolfram still doesn't provide a public fix for this issue. Especially considering the fact that Mathematica is a rather expensive piece of software.

---

### Post by correaa on 2009-06-22
> **ArchDefector said:**
> 

As I don't have any use for the Java integration of Mathematica, I then deactivated the JLink library by making its files unreadable, using some command like:

```

chmod a-x /usr/local/Wolfram/Mathematica/7.0/SystemFiles/Links/JLink

```


confirmed, 0% usage of the frontend. I am wondering what things stop working (if any) when disabling JLink in this way.

---

### Post by ch3n3t0 on 2009-06-22
From: jmartinez
Date: Mon Jun 22 13:51:52 2009
Subject: Further Information
To: [email]support@wolfram.com[/email]

----------------------------------------------------------------------------

Hello,

Thank you for the email.  I discovered I missed part of the
solution. I left off the link to the corrections to the java
part of the issue.  Replace
/usr/local/Wolfram/Mathematica/7.0/SystemFiles/Links/Jlink
with the folder
from here:

[http://download.wolfram.com/?key=GM5YM4](http://download.wolfram.com/?key=GM5YM4)

Let me know if you still have problems.

Sincerely,

Jason Martinez, Ph.D.
Technical Support
Wolfram Research, Inc.
[http://support.wolfram.com](http://support.wolfram.com)

---

### Post by dmonkey on 2009-06-23
I tried replacing the folder, and while it does seem to reduce the CPU usage, it does not eliminate it altogether. For the moment I've simply renamed the JLink folder (to JLink_old) to stop Java from running the programs inside.

---

### Post by hpsch on 2009-06-24
If i do this, the documentation center stopps to work. Thats not an option for me (as i am started to learn mathematica only a few months ago).
But i can live with the java process. At least Mathematica is useable again on my Netbook.

br
HPS

---

### Post by therealbrewer on 2009-06-24
The Wolfram provided solution mostly works, although Java seems to hover around 7% CPU even while doing nothing.

However, it does not address the Plot3D problem mentioned earlier...

---

### Post by jgrauer on 2009-06-24
still slow after new files.

---

### Post by Michael Knap on 2009-06-24
Thank you for the updates. Can we make a sticky top post on this thread to offer the other users a description of the problem and the solution with the instructions? This is typically done in other threads, almost like a HOWTO format? I will be happy to write it up, if someone can tell me how to make it a top, sticky post.

---

### Post by ArchDefector on 2009-06-25
BTW: The files inside the JLINK.zip archive, provided at [http://download.wolfram.com/?key=GM5YM4](http://download.wolfram.com/?key=GM5YM4) are exactly the same files that were installed by the 7.0.1 installer. There is no need to replace them if you have Mathematica 7.0.1 installed.

So there are currently two options to use Mathematica:

[LIST=1]
[*]For 32 bit machines replace the file[URL="http://download.wolfram.com/?key=61JJHE"]:
http://download.wolfram.com/?key=61JJHE[/URL]

Or for 64 bit machines replace the files:
[http://download.wolfram.com/?key=MK4ZR8](http://download.wolfram.com/?key=MK4ZR8)
[URL="http://download.wolfram.com/?key=YHDAH4"]http://download.wolfram.com/?key=YHDAH4 

[/URL]This way you have a fully functional Mathematica, but still an idle cpu load of ~16%.
.
[*]In addition, you can rename or "chmod a-x" the directory "SystemFiles/Links/JLink" to disable the Java support. This way you cannot use Java and the integrated help center anymore, but on the plus side there is no cpu load at all when Mathematica is idle.
[/LIST]
Currently I use option 2 and instead of the integrated help center I simply use the documentation at [http://reference.wolfram.com]("http://reference.wolfram.com/") which I prefer anyway, because the integrated help window performs rather sluggishly.

---

### Post by nike984 on 2009-06-25
> **therealbrewer said:**
> The Wolfram provided solution mostly works, although Java seems to hover around 7% CPU even while doing nothing.

However, it does not address the Plot3D problem mentioned earlier...


For Plot3D problem, use the following command to start mathematica.
```
mathematica -mesa
```

I tried uxa method, but this is the only method that actually worked for me.

---

### Post by wilsonkins on 2009-08-04
I too have found success with the above instructions from Wolfram.  I also renamed the java file, but I found that I need to give the folder its original name if I want access to the internet functions, like ChemicalData[].  I then re-rename it for better performance when outside access is not needed.  I should write a script for this.

Wilson Kinscherf

---

### Post by gmcauley on 2009-08-30
Thanks!

Point 1 of post [56]("http://ubuntuforums.org/showthread.php?t=1136142&page=6#56") worked for me for 32 bit.

---

### Post by stringkarma on 2009-09-04
Perhaps someone should update the ubuntu mathematica page [https://help.ubuntu.com/community/Mathematica](https://help.ubuntu.com/community/Mathematica) that seems to be quite outdated. It could include this new fix.

---

### Post by Michael Knap on 2009-09-09
I would be happy to update that page, or make a new HOWTO / nice wiki with instructions and explanations of the problems at hand, but I don't know how to get access to it. Could we make a nice sticky post on this thread with a SOLVED title ?
The bottom line is that this information should be more accessible, rather than tucked away in a deeply threaded conversation.

---

### Post by hoeltgman on 2009-09-13
Not sure if this has already been mentioned, but it's useful to know.
The solutions mentioned here for the CPU usage also work for Mathematica Player 7.0.1

---

### Post by Hatchetfish on 2009-10-07
Unfortunately, the fixes don't seem to work with 2.6.31 (using the 9.10 beta*) 

It isn't the 100% pegged cpu from before applying the library and java fixes, but it is 25-30 minimum for  at all times after the upgrade to 2.6.31.  It was 0-3% at an idle after the fixes with a 2.6.28 kernel.

* Yes, I know this isn't the 9.10 testing forum, but as this is nothing ubuntu will be fixing I didn't see the point in starting a new thread over there and losing the history.

---

### Post by correaa on 2009-10-07
this is sad, as circumstantial Mathematica follower (since mma4) I have seen the mathematica product decay in quality an stability.
I have 9.04, I have to solve the library problems and now it crashes frequently for no reason.
I think its closed philosophy is taking it too far a not being able to run in up-to-date systems.

---

### Post by tjevans on 2009-10-17
> **mi.kop said:**
> Plot3D works on my intel945. (ubuntu9.04).
Try using the new UXA as acceleration method. (this should at least solve the GEM issue...)
To do so change your xorg.conf "Device" section to:

```
Section "Device"
    Identifier    "Configured Video Device"
    Option        "AccelMethod"            "uxa"
EndSection
```...oh and the Mathematica FrontEnd is terribly slow :(

HTH
mi.kop

This solution works on my inspiron running 9.04. Thank you.

---

### Post by gmcauley on 2009-11-02
Fyi, I started a thread for MM7 and 9.10 [here]("http://ubuntuforums.org/showthread.php?p=8224090#post8224090").

---

### Post by drforbin on 2009-12-22
can anyone post the Jlink.zip file Wolfram has delinked it..

you can also email it to me if anyone has it....thanxs
[email]drforbin6@gmail.com[/email]

---

### Post by sunahm on 2009-12-28
I would also appreciate if anyone could send the files mentioned in the thread post No. 56 to my personal e-mail address: [EMAIL="nalim.sunah@gmail.com"]nalim.sunah@gmail.com[/EMAIL] (or post a link to them). I mean the 64-bit patches originally available under  
[COLOR=Black][http://download.wolfram.com/?key=MK4ZR8](http://download.wolfram.com/?key=MK4ZR8)
[http://download.wolfram.com/?key=YHDAH4](http://download.wolfram.com/?key=YHDAH4)
(but unfortunately not anymore...), since I'm still experiencing 10% CPU usage on both MathLink and Mathematica processes even after chmoding JLink to be non-executable (Ubuntu 9.10 on 2.26 GHz Core2Duo machine).
Thank you very much in advance and best wishes for the new year 2010!
[/COLOR]

---

### Post by dox_drum on 2009-12-28
> **sunahm said:**
> I would also appreciate if anyone could send the files mentioned in the thread post No. 56 to my personal e-mail address: [EMAIL="nalim.sunah@gmail.com"]nalim.sunah@gmail.com[/EMAIL] (or post a link to them). I mean the 64-bit patches originally available under  
[COLOR=Black][http://download.wolfram.com/?key=MK4ZR8](http://download.wolfram.com/?key=MK4ZR8)
[http://download.wolfram.com/?key=YHDAH4](http://download.wolfram.com/?key=YHDAH4)
(but unfortunately not anymore...), since I'm still experiencing 10% CPU usage on both MathLink and Mathematica processes even after chmoding JLink to be non-executable (Ubuntu 9.10 on 2.26 GHz Core2Duo machine).
Thank you very much in advance and best wishes for the new year 2010!
[/COLOR]

I'm sure that's a rather good behaviour of the CPU, as far as I remember mine blows up to 140%... so the OS almost freeze.

---

### Post by correaa on 2010-01-13
@sunahm: see my post in page 5, it has the files attached. I am glad I did upload them.

---

### Post by mikelito on 2010-02-03
I found a workaround for the java process problem which does not require saying goodbye to the documentation center (kind of, at least you do not need to restart mathematica to have it).

Quite simply, in a notebook you have open type and execute

Needs["JLink`"]
UninstallJava[]

This will kill the "java" process altogether.
It will be automatically restarted if you open or browse the documentation, but you can kill it again after you are finished by re-running UninstallJava[].

I am now working on a solution to have UninstallJava called automatically say every minute, so that java will hog your CPU just when it's needed.

Let me know if this works for you!

---

### Post by LeoL on 2010-03-11
Hi, I saw that some of you have "mathematica 7.0.0"... I have same version...
In this thread is said that we need some patches... Ok, user 'correaa' attached almost all of them but I can't find "Jlink.zip" because it was delinked from [http://download.wolfram.com/?key=GM5YM4](http://download.wolfram.com/?key=GM5YM4) 

Maybe a lot of users have "7.0.1" version so they don't use "Jlink.zip" (because it's said that are same files that 7.0.1 installation) But I have "7.0.0" and I think some of you could have a copy of "Jlink.zip". Please, could you attach or send me a copy of "Jlink.zip" or a copy of your '/SystemFiles/Links/JLink' folder?

my email is [email]wxxuxxw@yahoo.com.ar[/email]

Thanks, very much

---

### Post by Azrael3000 on 2010-05-06
I also experienced this problem under Lucid. Downloading the files from the post here: [http://ubuntuforums.org/showpost.php?p=7486232&postcount=46](http://ubuntuforums.org/showpost.php?p=7486232&postcount=46) and applying the chmod mentioned below solved everything.

> **ArchDefector said:**
> The replacement of [FONT=Courier New]libML32i3.so[/FONT]  dropped the idle cpu usage of Mathematica on my machine to ~16% too.

As I don't have any use for the Java integration of Mathematica, I then  deactivated the JLink library by making its files unreadable, using some  command like:

```

chmod a-x /usr/local/Wolfram/Mathematica/7.0/SystemFiles/Links/JLink

```Now Mathematica is usable under recent kernels and doesn't hog  any cpu time at all when idle.

It's really a shame that Wolfram still doesn't provide a public fix for  this issue. Especially considering the fact that Mathematica is a rather  expensive piece of software.

---

### Post by Caterpillar00 on 2010-07-07
Thank you correa, I'm a Fedora user, I found out this topic by searching on Google "Wolfram Mathematica cpu usage Linux".
You saved my work **_and my battery_**, before this fix I got 100% cpu usage, now max 15% with the java process.
God bless you!

---

### Post by correaa on 2010-09-03
Mathematica 7.0.2 fixes the problem all together, you can download it (yes, the full version) from:

[http://download.wolfram.com/?key=QNQKNV](http://download.wolfram.com/?key=QNQKNV)

BUT HURRY UP!, the link will expire Sun Sep 5 11:36:15 2010. After 2 years of problems it finally works. (It works in my Ubuntu 10.04.)

---

### Post by The_Eddster on 2010-09-16
> **correaa said:**
> Mathematica 7.0.2 fixes the problem all together, you can download it (yes, the full version) from:

[http://download.wolfram.com/?key=QNQKNV](http://download.wolfram.com/?key=QNQKNV)

BUT HURRY UP!, the link will expire Sun Sep 5 11:36:15 2010. After 2 years of problems it finally works. (It works in my Ubuntu 10.04.)

Damn, this is exactly what I need and now it's too late! Is there any other way to update to 7.0.2? I have a student licence of Mathematica 7.0.1 on Ubuntu 10.04.

---

### Post by churchyard on 2010-09-30
Anyone still having that file?
We use Mathematica in school, but version 7.0.1 really cooks my CPU.
Thank you.

---

### Post by Eckidna on 2010-10-08
> **churchyard said:**
> Anyone still having that file?
We use Mathematica in school, but version 7.0.1 really cooks my CPU.
Thank you.


It`s possible to download it from Russian bittorrent tracker rutracker.org.

[http://rutracker.org/forum/viewtopic.php?t=3175848](http://rutracker.org/forum/viewtopic.php?t=3175848)

---

### Post by churchyard on 2010-10-08
Thanks, but I don't want to download it this way :) I have contated a person from our school, who is in touch with Wolfram, so they should send us a new version around the November, and I will be able to download it from our school server legally, then. But thanks.

---

### Post by astro-swe on 2010-10-11
> **Eckidna said:**
> It`s possible to download it from Russian bittorrent tracker rutracker.org.

[http://rutracker.org/forum/viewtopic.php?t=3175848](http://rutracker.org/forum/viewtopic.php?t=3175848)

Thank you very much, it works almost perfectly! Checksum failed once, re-run and it went on to stop with "$ProductTitle not set" or something similar. Just had to rename the directory to get rid of a <space>.

It's running really smooth! Hopefully secure and safe too .. ;)

Thanks again (goes out to Wolfram as well)!

---

### Post by davidfuhrman on 2010-10-22
The link to the new Jlink directory is broken.  Can anybody post this file?

---

