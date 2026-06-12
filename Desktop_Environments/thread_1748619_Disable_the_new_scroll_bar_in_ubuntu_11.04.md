---
title: "Disable the new scroll bar in ubuntu 11.04"
date: 2011-05-03
forum: Desktop Environments
---

### Post by mjsilverstri on 2011-05-03
Hi,

In the ubuntu 11.04, the scrollbar work different. The left/right arrow controls appear after I click on the orange scroll part of the scroll bar. Is there a way to disable to go back to the traditional scroll bar, where  it has left/right arrow at each end and I can click on anywhere of the scroll bar to scroll there.


Thank you.

---

### Post by Purplerob on 2011-05-03
I found this command 
```
sudo apt-get remove overlay-scrollbar liboverlay-scrollbar-0.1-0
```
 Here 
[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

---

### Post by 3rdalbum on 2011-05-03
The left-ride grab handle should appear after you mouseover/mousenear the orange part of the scroll bar.

---

### Post by mihai.ile on 2011-05-04
oh thank you, the new scrollbar is so slow to work with on a PC.
You always have to wait for the widget to appear before you can scroll...

---

### Post by compmodder26 on 2011-05-04
If you simply want to disable them without uninstalling the package, you can do the steps here:

[http://www.webupd8.org/2011/04/how-to-disable-overlay-scrollbars-in.html](http://www.webupd8.org/2011/04/how-to-disable-overlay-scrollbars-in.html)

---

### Post by Highlander14781 on 2011-05-07
That work:)... Now I am at the original scroll bar.

Frank

---

### Post by Lucas32 on 2011-05-08
is there a way to make those new scroll widgets be visible all the time?

---

### Post by mr_niceguy on 2011-05-17
> **Purplerob said:**
> I found this command 
```
sudo apt-get remove overlay-scrollbar liboverlay-scrollbar-0.1-0
```
 Here 
[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

Sweet thanks!

I'll think about reinstalling them if my desktop monitor ever turns into a tiny phone.

---

### Post by lx3r on 2011-05-22
I'm using a **touch-screen** monitor, and this overlay scrollbar can hardly be used now. 
(there is no 'hover' for touchscreens ).

This thing needs improvement imho.

---

### Post by alpha-buntu on 2011-08-09
thank you. just another stupid example what mark is thinking about improvement of ubuntu, when he had a night too much counter-strike playing .... or looking too much at his iphone.

---

### Post by Donnie Love on 2011-08-12
> **Purplerob said:**
> I found this command 
```
sudo apt-get remove overlay-scrollbar liboverlay-scrollbar-0.1-0
``` Here 
[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

I put the above magic jibberish into the DOS window and it gave me this:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

Anyone know what it means (I don't speak jibberish), and how to fix it?

---

### Post by Donnie Love on 2011-08-12
> **compmodder26 said:**
> If you simply want to disable them without uninstalling the package, you can do the steps here:

[http://www.webupd8.org/2011/04/how-to-disable-overlay-scrollbars-in.html](http://www.webupd8.org/2011/04/how-to-disable-overlay-scrollbars-in.html)

This solution worked better for me. Thanks. :0>

---

### Post by LinuxQuint on 2011-08-25
I do not like the new scroll bars at all.  Usually it's the people at Microsoft doing this stuff.  I *DO* thank you for Ubuntu as a whole, though, which is generally pretty great.

---

### Post by HerzeleidMeister on 2012-03-11
Thank you the new scroll bar really sucks. I could not scroll anything to save my life after upgrading from 10.10.

---

### Post by tribbletribble on 2013-01-31
My gods, thank you.  I feel like I have just scratched an ubearable itch.

Logging out of KDE and restarting X was sufficient to get X to update, and quite quick.

Sigh, I'm confused - was this abomination (yet another) piece of KDE idiocy or was it an Ubuntu idiocy?

In any case it needs to stay gone.  Features are not good interface design.  Preach. Choir. Done.

---

### Post by zombifier25 on 2013-01-31
> **tribbletribble said:**
> My gods, thank you.  I feel like I have just scratched an ubearable itch.

Logging out of KDE and restarting X was sufficient to get X to update, and quite quick.

Sigh, I'm confused - was this abomination (yet another) piece of KDE idiocy or was it an Ubuntu idiocy?

In any case it needs to stay gone.  Features are not good interface design.  Preach. Choir. Done.

It was Ubuntu. If you install Ubuntu (not variants), it will come with the Ayatana overlay scrollbar.

---

### Post by rI9^)wx! on 2013-05-31
> **Donnie Love said:**
> I put the above magic jibberish into the DOS window and it gave me this:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

Anyone know what it means (I don't speak jibberish), and how to fix it?

Do what it says, and type 'sudo dpkg --configure -a' into your terminal window, then press enter.  It should run for a while, after it is done try the command again.

---

### Post by oldos2er on 2013-06-01
Old thread closed.

---

