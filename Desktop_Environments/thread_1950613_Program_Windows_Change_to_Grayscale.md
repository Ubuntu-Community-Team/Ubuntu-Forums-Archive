---
title: "Program Windows Change to Grayscale"
date: 2012-04-01
forum: Desktop Environments
---

### Post by Acharn on 2012-04-01
Probably I should wait until I get my new hard drive before I submit this question, but I have some free time now. A few months ago my Acer Aspire M1610, 1GB RAM, 250GB HDD, ATI Raydeon x1550 graphics card, started acting funny. At the time I had Windows XP Pro installed, but eventually I couldn't boot and in flailing around trying to fix the boot sector I trashed the partition table. Luckily I had a Live CD of Maverick Meercat (Ubuntu 10.10) that I downloaded in Feb 2011, and I was able to install that and then upgrade to 11.04 and then 11.10 and everything worked except I was getting constant messages "A Hard Drive Is Reporting Imminent Failure," and it kept losing sectors and then this month I couldn't boot from that any more, but was still able to use the Live CD and then discovered "persistent sessions," which allows a lot better experience.

Anyway, from the time I first upgraded to 11.04, I have noticed programs, especially the Firefox browser, will from time to time change from color to grayscale and stall for a while. I have also referred to this as "going dark," because the window looks much darker than when it is in color. This happens with all programs: Movie Viewer (pretty often), Firefox (constantly, I can't even run the program from Safe Mode), Transmission, Ubuntu Software Center, even the terminal. I thought it might be connected with odd signals coming from the failing hard drive, but I've removed it expecting to install a new one tomorrow. Another guy suggested it was tied to Firefox, and that the problem would go away when I upgraded to Firefox 11.0, but I have and it hasn't. I will say, however, that I wish I could stay with the Firefox 3.6 that's on the Live CD because it's so much faster than I've experienced for years.

It may have something to do with the graphics card. I wasn't able to get good graphics with most Windows games using Wine, even those programs that Wine evaluated as Platinum. Or maybe insufficient memory? Is 1GB a small RAM for Linux? I wouldn't have thought so. Some other component on the motherboard getting close to failure? It's had pretty constant use for 4-1/2 years.

I would have thought this problem was well known, but I haven't found anything in many searches, both in the forums and in Google generally. I haven't been able to figure out how to reproduce it, and it doesn't seem to be obviously tied to the number of programs I have running at once, although I hardly ever run as many as four, including a terminal.

---

### Post by mightyiam on 2012-05-30
Excuse me that I didn't read your entire message.

Generally, windows turning to grayscale is, according to my intuitive guess and experience, when the process that generates that window is not responding to input/signals. When it responds again, the window turns into color back.

Blessings,
Shahar

---

### Post by Acharn on 2012-05-30
Yes, that seems to be what's happening. I was finally able to get a new hard drive and installed it about ten days ago. Previously, this happened most often with Firefox, and also Chromium, and was sometimes associated with the error message "A script on this page is not responding..." It happened with other programs, too, but there didn't seem to be any pattern. Now it happens rarely with my browsers but frequently with other programs, like Movie Player, Fhythmbox, and Exaile (I just installed it day before yesterday because I can't get Media Monkey to work). What I would like to find out is why the programs have stopped responding. Usually it's only for a minute or two, but sometimes I lose patience and pull the plug -- since the whole desktop is frozen I can't shut down any other way.

---

### Post by mightyiam on 2012-06-06
Scripts on the web (javascripts) are quite heavy and CPU consuming these days. For example, Gmail can be quite heavy some times. But it is when these scripts enter into a loop or some kind of programming error that causes them to 'run' for too long that it hangs the browser and then you experience the grey window.

This shouldn't have any effect on the whole desktop. Whether this is a browser or another app that is hung. So if your whole desktop freezes then you have a problem with something else, as well.

When the Desktop hangs - can you please press Ctrl+Alt+F1 and see if you get a tty? This is something that's useful if you are experiencing complete desktop hangness.

Also, I would try running memtest (just select it from the boot menu).

If you get any errors from memtest then you have a hardware or hardware configuration issue.

Blessings,
Shahar

---

### Post by Acharn on 2012-06-08
Thank you for the suggestions. I was finally able to get a new hard drive last month, and it has helped a lot. I still get this behavior, but now it's rarely from the browser. I gety it a lot from Movie Player, Rhythmbox, Banshee, Firefox, and especially from Ubuntu Software Center. I'm leaning a little bit now to the idea it has something to do with my graphics card driver. I have an Acer Aspire M-1610, with an ATI Radeon x1550 card. I've been reluctant to install the ATI driver, which hasn't been updated since October 2009, and have started thinking about the open source fglrx (or whatever it is) driver. With the new hard drive my browser performance is (mostly) much better, so I can more easily research the potential pitfalls of that. 

The thing is, this seems to be correct behavior under some circumstances. I mean this behavior is obviously a programmed response, but I can't find out programmed by whom, in what part of the system, and triggered by what conditions. I thought it must happen to pretty much everybody, but nobody has replied saying it happens to them too, so for a while I thought it was due to the failing hard drive, and later the limited resources as I spent months working from the Live CD with an 8GB USB stick for a "persistent session." Well, I haven't solved the problem in the sense of understanding what's wrong and fixing it, but at least it has become a mere annoyance, rather than a serious handicap.

---

### Post by mightyiam on 2012-06-09
> **Acharn said:**
> Thank you for the suggestions. I was finally able to get a new hard drive last month, and it has helped a lot. I still get this behavior, but now it's rarely from the browser. I gety it a lot from Movie Player, Rhythmbox, Banshee, Firefox, and especially from Ubuntu Software Center. I'm leaning a little bit now to the idea it has something to do with my graphics card driver. I have an Acer Aspire M-1610, with an ATI Radeon x1550 card. I've been reluctant to install the ATI driver, which hasn't been updated since October 2009, and have started thinking about the open source fglrx (or whatever it is) driver. With the new hard drive my browser performance is (mostly) much better, so I can more easily research the potential pitfalls of that. 

The thing is, this seems to be correct behavior under some circumstances. I mean this behavior is obviously a programmed response, but I can't find out programmed by whom, in what part of the system, and triggered by what conditions. I thought it must happen to pretty much everybody, but nobody has replied saying it happens to them too, so for a while I thought it was due to the failing hard drive, and later the limited resources as I spent months working from the Live CD with an 8GB USB stick for a "persistent session." Well, I haven't solved the problem in the sense of understanding what's wrong and fixing it, but at least it has become a mere annoyance, rather than a serious handicap.

It is not necesarrily hard drive related. Although sometimes that happens too, especially when you have a slow HDD or working with large files or using encryption or a combination of these. It is usually more a CPU load issue. Is your CPU 100% when this happens? Does your HDD LED show a lot of activity when this happens? These can teach you where the "bottleneck" is.

The open source ATI driver is called "ati" and the proprietary closed source one is called fglrx. I'd go with the open source one if you don't have a good reason to go with the closed source one. They do cause a lot of headache sometimes, those closed source drivers.

I would assume that this functionality is implemented in the Window Manager. So either you're using Compiz or if you're on Unity 2D then you're using Metacity (that's how things are in Ubuntu). So if you want to know where this functionality is, where the code is, then check out Compiz. But it doesn't impress upon me that you're interested in diving into the code. You just want a faster computer, don't you? Well, what CPU do you have? That Acer Aspire M1610 can have various different Processors.

Thankts and Blessings,
Shahar

---

### Post by Acharn on 2012-06-16
Well, thank you for the suggestions, and the clarification about the ATI driver. I've been looking at the forums off and on, and there doesn't seem to be much consistency. Anyway, I'm currently using the default drivers installed with Ubuntu, but I had graphics problems with Windows programs under WINE when my hard drive was failing. I haven't had time to experiment with them since getting the new hard drive.

My Acer Aspire M-1610 came with an Intel Duo-Core running at 1800 MHz. I knew when I bought it that I really wanted a faster CPU, but my wife intervened and I settled for this. It also has only 1GB RAM and can only accomodate 1 hard drive. I got it five years ago but have to hope it holds up for a couple more years until I can afford a new one. Next time I'll make sure to get a faster CPU, more RAM, and a better graphics card (Nvidia).

It really seems ridiculous. I started programming 8080 and Z80 assembly language in 1976, and thought the IBM AT at 4.17 MHz was really something. In 1993 I was using the Internet over a 300 baud connection from a university here in Thailand, when we had to use WAIS and Gopher, and Usenet was still useful. I don't have the energy or the interest any more and I really don't want to spend my time digging into these kinds of problems, but sometimes it's still fun.

---

