---
title: "compiz wont work"
date: 2009-10-15
forum: Desktop Environments
---

### Post by yanvolking on 2009-10-15
Hello Community

I have recently installed compiz on my laptop (DELL LATITUDE D610).  I have set the "cube" and "rotate" settings and it works beautifully.  

When I did the same on my desktop computer, the compiz function is there as I can access SYSTEM->PREFERENCES->COMPIZ CONFIG SETTINGS MANAGER.  but after clicking DESKTOP CUBE and then ROTATE CUBE, there is no cube nor rotating effect.  The change from desktop to desktop is just the same as before I installed COMPIZ.  The computer is a month old so I am sure it is not a hardware problem there.  BUT the screen is an old cathode ray model dating to 1993.  It is small and requires scroll bars (horizontal and vertical) to view your average web page for example.

Could this antiquated screen be the cause of this? if not what?

Thanks

---

### Post by baffledsimian on 2009-10-15
The CRT screen has nothing to do with this problem. It only generates the image that the video card sends it in the first place.
This could perhaps be a problem with the video drivers. Have you checked whether other elements of compiz work such as wobbly windows?

If you're sure that compiz has been correctly configured you might try checking that Ubuntu has installed the latest drivers for your video card.

---

### Post by yanvolking on 2009-10-15
Hi Baffledsimian.  Thanks for your reply.

I have tried loads of other elements and there is absolutely no change.  It really is as if compiz had not been installed with the only exception of the preferences menu being available.

If Ubuntu has not installed the latest drivers for my video card, how come there is not that problem with my laptop which is at least six years old and has had exactly the same installation sequences as my desktop?

If however it is that, How can I make UBUNTU install the latest drivers for my video card?

Thanks

---

### Post by HNS-I on 2009-10-15
I'm not entirely sure if this information is up-to-date but there are two projects going on. Compiz and Beryl. A stable version of compiz is included in the ubuntu distro. Compiz and Beryl joined forces into a project called compiz-fusion, now the've changed their name to compiz. I presume because of this confusion.
So a while ago you needed to add an additional repo to your sources.list in the apt dir, and you had to download compiz-fusion; in order to get the desktop cube effect.
But again I'm not sure if this is up-to-date info. Maybe someone else can shed his/her light on this.
EDIT: here is a link
[http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml)

---

### Post by baffledsimian on 2009-10-15
You might want to check out this page for the driver installation info:
[http://www.freesoftwaremagazine.com/articles/installing_compiz_fusion](http://www.freesoftwaremagazine.com/articles/installing_compiz_fusion)

Do you have an nVidia or an ATI card in your desktop?

Further, you might want to check that you have exactly the same number of compiz packages installed as on your laptop. Go to synaptics manager, search for compiz and check that you have exactly the same packages installed on both computers.

---

### Post by baffledsimian on 2009-10-16
you might also want to check out this page on the forum:

[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

---

### Post by yanvolking on 2009-10-16
Hi Baffled Simian

I looked at the packages installed on my desktop and they are exactly the same as those on my laptop.  I suppose it could well be a video card problem.  
How can I check which video card I have?
How can I check if the drivers of this card are correct or up to date?
I looked at  "http://www.freesoftwaremagazine.com/articles/installing_compiz_fusion" but it all seems so complicated with lots of command line instructions.  Is there not a GUI environment solution to the video card / driver situation?

Thanks in advance

Yan

---

