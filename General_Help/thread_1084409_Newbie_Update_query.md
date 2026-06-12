---
title: "Newbie Update query"
date: 2009-03-02
forum: General Help
---

### Post by satish_j on 2009-03-02
Does 'sudo apt-get update' _DOWNLOADS_ all the packages that needs updation??

---

### Post by zvacet on 2009-03-02
Command **sudo apt-get update** synchronize your source list with repos.For downloading new updated packages use** sudo apt-get upgrade**.You don´t want to write twice so you will do it like this

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by satish_j on 2009-03-02
Thanks for reply..
I have dial-up connection at home.So,upgrading the packages using apt-get upgrade is not possible for me.
Is it Ok if i periodically update my sources,but NOT upgrade the same.
Also,can we configure Upgrade to upgrade ONLY important packages (system-specific packages)AND NOT optional packages like 'Mozilla',RhythmBox,etc..
Iam a newbie to world of Linux and am disappointed with this feature that all the packages(for OS,additional sofwares,etc.) have been packed into repos has to rely heavily on a broadband internet connection..

---

### Post by zvacet on 2009-03-02
You can try [Keryx]("http://crashsystems.net/2009/01/keryx-tutorial/") to download packages from another comp and then install it offline at home.If you want some package to not be upgrade go to the synaptic and find that package and click on **lock version.**

---

### Post by satish_j on 2009-03-03
Thanks for the link.
Iam going to try Keryx today evening only.

---

### Post by satish_j on 2009-03-03
:(:(
Iam not even able to make the project in 2nd step:
Getting the foll error:
```

satish@TITAN:/media/disk/keryx-0.92/linux$ python keryx.py -create Offline-updates debian
Loading config: /media/disk/keryx-0.92/linux/keryx.conf
Traceback (most recent call last):
  File "keryx.py", line 105, in <module>
    import lib.wxkeryx
  File "/media/disk/keryx-0.92/linux/lib/wxkeryx/__init__.py", line 19, in <module>
    import wx
ImportError: No module named wx

```

any help on this..

---

### Post by oldos2er on 2009-03-03
If you check System, Administration, Software Sources, under the 'Updates' tab you can choose which updates you want.

---

### Post by EXCiD3 on 2009-03-03
> **satish_j said:**
> :(:(
Iam not even able to make the project in 2nd step:
Getting the foll error:
```

satish@TITAN:/media/disk/keryx-0.92/linux$ python keryx.py -create Offline-updates debian
Loading config: /media/disk/keryx-0.92/linux/keryx.conf
Traceback (most recent call last):
  File "keryx.py", line 105, in <module>
    import lib.wxkeryx
  File "/media/disk/keryx-0.92/linux/lib/wxkeryx/__init__.py", line 19, in <module>
    import wx
ImportError: No module named wx

```any help on this..

The problem is you have -create instead of --create. Just a little typo. :)

---

### Post by satish_j on 2009-03-03
> **EXCiD3 said:**
> The problem is you have -create instead of --create. Just a little typo. :)

WOW..that did the trick...Iam really feeling very confident now for i feel that there are masters out there to help me...
It may be a simple thing to you,but,for me,it was no less than a magic..
Iam now happily taking this project on Pendrive to office morrow..
:P:P:P

---

### Post by EXCiD3 on 2009-03-03
> **satish_j said:**
> WOW..that did the trick...Iam really feeling very confident now for i feel that there are masters out there to help me...
It may be a simple thing to you,but,for me,it was no less than a magic..
Iam now happily taking this project on Pendrive to office morrow..
:P:P:P

Hopefully it would be simple for me, I created Keryx. ;)

---

### Post by satish_j on 2009-03-04
Iam getting error on downloading packages as follows:
```

Downloading: http://in.archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5-minimal_2.5.2-2ubuntu4.1_i386.deb
Failed: http://in.archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5-minimal_2.5.2-2ubuntu4.1_i386.deb
Reason: [Errno socket error] (11001, 'getaddrinfo failed')

```
We have a proxy connection to internet at office..Is this the reason for error(I read some issues with proxy in the manual)..

---

### Post by EXCiD3 on 2009-03-04
Yeah that could be the problem. Does it require authentication? Sometimes you might need special formatting for the proxy. Try these methods:

http://<ip or domain>:<port>
and
<ip or domain>:<port>

Some have said that it does not save the proxy password either but you can edit the keryx.conf file and it will load the saved password just fine, just doesnt save it yet.

Hope this helps!

---

### Post by satish_j on 2009-03-04
Sorry..I did not get what you said..can you pls explain it more simply.
Does i need to enter proxy details in keryx.conf file??
And where do i need to enter <ip or domain>:<port>

---

### Post by EXCiD3 on 2009-03-04
In the Keryx options page (you can skip trying to download the files to get there) set the proxy information there and try it. Save the information and then try to download again and hopefully it will work. I would try it without the [http://.](http://.) Everything goes in the Proxy tab on the Edit->Options window for Keryx.

---

### Post by satish_j on 2009-03-04
Thanks..I tried with http:// and it is working...
Upgrades are getting downloaded..It may take an hour or so..

---

### Post by EXCiD3 on 2009-03-04
Glad you got it working. I don't have a proxy myself to test it with so I had to code it and let you users be the guinea pigs. :) Btw, does yours require authentication of a username and password?

---

### Post by satish_j on 2009-03-04
Finally,i have downloaded the updates through keryx.but,for some packages,i have received error in log as:
```

Downloading: http://in.archive.ubuntu.com/ubuntu/pool/main/h/hal/hal_0.5.11~rc2-1ubuntu8.2_i386.deb
Failed: http://in.archive.ubuntu.com/ubuntu/pool/main/h/hal/hal_0.5.11~rc2-1ubuntu8.2_i386.deb
Reason: ('http error', 407, 'Proxy Authentication Required', <httplib.HTTPMessage instance at 0x00A9A558>)

```
But that is for some of the packages.can i download these packages manually??
Or even if not,i can manage these remaining updates from my home PC..
Thanks **EXCiD3** a million for creating such a useful application..

And yes,it did required authentication of username and password.I first tried giving only proxy,but it didnt worked.

---

### Post by EXCiD3 on 2009-03-04
That is odd that only a couple of the packages didn't work. The code I am using for downloading the packages is known to be not so reliable and probably caused the issue. You can just copy and paste those links into your web browser and download them manually. Keryx is just there to help you get everything easier.

---

### Post by satish_j on 2009-03-04
INstalled the updates successfully at home..
Just before using this keryx(i.e yesterday),my system was showing some 341 updates available and now only 7..
I salute you for your work...it will really help peoples like me with slow internet connection..
HATS OFF ......:P:P

---

### Post by EXCiD3 on 2009-03-04
Thanks man! Spread the word! :D

---

