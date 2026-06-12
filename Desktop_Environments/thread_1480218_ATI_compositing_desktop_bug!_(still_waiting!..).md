---
title: "ATI compositing desktop bug! (still waiting!..)"
date: 2010-05-11
forum: Desktop Environments
---

### Post by uprise on 2010-05-11
Well, I am new to linux and ubuntu, but it seems like this bloody bug has not been solved for years. There are many threads as i googled, back from years 2007, 2008... After lucid, i was hoping something (i do not know, if i should have) and googled recently. Found this:
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2251958.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2251958.html)
That xserver thing (which i have tried before for 9.10) does not work!
What am i going to do about this? I cannot even use* edge flipping* because of that bloody resizing/maximizing problem. I cannot use stuff like docky. No compositing! 

Until when should i wait?
Is there a possibility of this bug being solved?
Should i give my notebook to some windows user and get an nvidia one?
-----
--- Sony Vaio - FW
--- Ati Radeon HD 3400 series graphics
--- UBUNTU 10.04 64bit

---

### Post by uprise on 2010-05-12
anybody NOT having this problem? 
anyone who has ati and running compiz?

---

### Post by antenna on 2010-05-12
I have HD4200 with catalyst & compiz and everything works fine here. Not very helpful I know :???:.  You're using the driver directly from Ubuntu (hardware drivers dialog) I assume?

---

### Post by uprise on 2010-05-12
> **antenna said:**
> I have HD4200 with catalyst & compiz and everything works fine here. Not very helpful I know :???:.  You're using the driver directly from Ubuntu (hardware drivers dialog) I assume?
yes, the fglrx driver.

---

### Post by QIII on 2010-05-12
After you installed the driver, did you go to the terminal and issue

```
aticonfig --initial -f
```and then reboot?

I've had several ATI machines and have had little trouble since AMD bought ATI and started to get serious about Linux support.

---

### Post by dE_logics on 2010-05-12
Dude, there're no solutions; older ATI card support is getting worst with time, specially after mesa 1.6 and it wont be improved. I've talked about it in the freedesktop mailing list and reported a bug but the devs are least concerned.

The best show that you can do is use Gentoo, it will make things MUCH faster by compiling the drivers and all in a special way...but that wont enable compositing...the problem will remain the same.

---

### Post by 2hot6ft2 on 2010-05-12
> **uprise said:**
> anybody NOT having this problem? 
anyone who has ati and running compiz?
ATI on one machine that's not having any problems. Not sure what chip it is since I'm not on it right now and it's built in.

---

### Post by dE_logics on 2010-05-12
> **uprise said:**
> anybody NOT having this problem? 
anyone who has ati and running compiz?


No. :( Not with the older ones.

---

### Post by fbkarsdorp on 2010-05-13
check this thread:

[http://ubuntuforums.org/showthread.php?t=1470157](http://ubuntuforums.org/showthread.php?t=1470157)

should work.

---

### Post by QIII on 2010-05-13
> **dE_logics said:**
> Dude, there're no solutions; older ATI card support is getting worst with time, specially after mesa 1.6 and it wont be improved. I've talked about it in the freedesktop mailing list and reported a bug but the devs are least concerned.

The best show that you can do is use Gentoo, it will make things MUCH faster by compiling the drivers and all in a special way...but that wont enable compositing...the problem will remain the same.

His card should still supported, since it is an "HD". 

It should work with compositing. 

The driver is in the repos.

Here's a list of the legacy cards, per ATI's website:

ATI Radeon 9500 Series
ATI Radeon 9550 Series
ATI Radeon 9600  Series
ATI Radeon 9700 Series
ATI Radeon 9800 Series
ATI Radeon  X300 Series
ATI Radeon X550 Series
ATI Radeon X600 Series
ATI  Radeon X700 Series
ATI Radeon X800 Series
ATI Radeon X850 Series
ATI  Radeon X1050 Series
ATI Radeon X1300 Series
ATI Radeon X1550  Series
ATI Radeon X1600 Series
ATI Radeon X1650 Series
ATI  Radeon X1800 Series
ATI Radeon X1900 Series
ATI Radeon Xpress  Series
ATI Radeon X1200 Series
ATI Radeon X1250 Series
ATI  Radeon X2100 Series

Supported cards in Catalyst 10.4:

[http://www2.ati.com/drivers/linux/catalyst_104_linux.pdf]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_104_linux.pdf")

His card is in there under "Desktop Family"

---

### Post by QIII on 2010-05-13
uprise --

Remember that neither Canonical nor the Linux community in general writes the proprietary drivers of any OEM's hardware.  The OEM does that.  The community does provide open source drivers, but they often do not provide many of the "nice" things you would get with the proprietary driver -- if that driver works.

If you read the material at the URL you listed and go to the links  provided, it appears that the issue is with the fgrlx driver itself and  not anything in Ubuntu.  Since the driver is proprietary, nobody at  Canonical can do much about it (it even says something to that effect  when you install the driver through Hardware).

There are some work-arounds given, which means that someone clever has  figured out a way to mitigate the effects of the bug.  Alternatively,  you can use the open source driver, but that will still leave you with  no special bells and whistles.

The AMD representative in one of the links (to a phoronix forum) states  that the bug does not appear to have been reported or, if it has, it is  not complete enough for them to reproduce the error.

Until the bug is properly reported (and often enough) and a patch is  issued by AMD/ATI, the best solution for the time being is using the  ppas suggested or use the open source driver.

And, by the way as I said before, none of my ATI machines has  encountered this particular behavior.

---

