---
title: "Load images in Evolution doesn't work"
date: 2008-09-06
forum: Desktop Environments
---

### Post by dkorz on 2008-09-06
Images are not downloaded and displayed in Evolution. The image area is displayed (usually with the correct dimensions) but only a small black rectangle is in the upper left corner. Ctl-I or Load Images seems to reload the message (the window flashes) but no change occurs. I changed the  preference to "Always load images the Internet" but that didn't work. 

I tried to display the Debug Log but nothing ever shows up in it. I don't know where else to look for error messages.

I'm running 8.04 32 bit. Any help will be appreciated, thanks...

---

### Post by focrstrych9 on 2008-10-05
I am having the same issue under 8.04. Oddly, some images load while others do not. On the emails that won't load the images, I see that the status bar shows the email loading the images, but they all never come off of 0%. The emails that **do** load images show the usual percentage progression 0-100%. Could some sites be blocking Evolution? That seems to be the behavior. Any help is appreciated.

---

### Post by liviococcia on 2008-10-13
Hello dkorz, did you find out what the cause was, regarding the problem of  email images not displaying in the Evolution Client?

I'm having the same problem, and tried the same things too, with no luck.

I did also have a load of updates today, so Ubuntu is fully up to date, and after doing so had a crash error notification after a restart 'compiz.real' was the app, but i sent a bug report.

And after reading the bug threads, change my 'Appearance' settings to 'contrast' fonts, and 'Human Interface clear', and effects to 'none'.

Ubuntu's running even better, bear in mind, i am using the 8.10 beta version.

This didn't sort Evolution out though

regards

---

### Post by &lt;iostream&gt; on 2009-05-30
I am having the same problem on 9.04. Need a solution! *bump*

---

### Post by kweejibo on 2009-05-30
Me, too. 9.04 32-bit. Images don't load at all in any emails. I've tried all of the HTML options in an effort to make it work. Tried restarting Evolution after each change. 

Please advise what I might be able to do to log this problem and help debug.

Josh

---

### Post by kweejibo on 2009-05-30
All hail Google!

I found this link:

[http://www.mail-archive.com/evolution@lists.ximian.com/msg02045.html](http://www.mail-archive.com/evolution@lists.ximian.com/msg02045.html)

The solution is to change the Proxy connection in the Network Settings section. Instead of using "system defaults," I changed mine to "Direct Connection to the Internet" and restarted Evolution-- voila!

Works great.

Josh

---

### Post by days_of_ruin on 2009-05-30
Edit>Preferences>Mail Preferences>HTML Messages> Always load images from the internet. Have you all tried that?

---

### Post by roman.lange on 2009-06-14
> **kweejibo said:**
> All hail Google!

I found this link:

[http://www.mail-archive.com/evolution@lists.ximian.com/msg02045.html](http://www.mail-archive.com/evolution@lists.ximian.com/msg02045.html)

The solution is to change the Proxy connection in the Network Settings section. Instead of using "system defaults," I changed mine to "Direct Connection to the Internet" and restarted Evolution-- voila!

Works great.

Josh

Thanks a lot! I had exactly the same problem on Jaunty and Evolution 2.26.1 and this solved it.

---

### Post by PatricioLearner on 2009-08-01
Same problem but "Direct Connection to the Internet" did not solve it...  
Jaunty

---

### Post by smartmeister on 2009-12-05
just to let you that this workaround doesn't work either on ubuntu 9.10

Images are loaded one by one, one each 10 secondes, a simple html email becomes a hell to load

---

### Post by kelvin.illa on 2010-02-07
> **roman.lange said:**
> Thanks a lot! I had exactly the same problem on Jaunty and Evolution 2.26.1 and this solved it.

Thanks! This worked.

But I don't get why I can't have my proxy on auto-proxy with evolution. I need my auto-proxy when I'm using the internets from school. Firefox runs normally and uses the proxy only when I'm in school. Pidgin won't run when I'm in school, but runs well at home. Why won't evolution show images with the auto-proxy on even when I'm just at home?

---

### Post by Jordan G on 2010-05-06
> **kweejibo said:**
> All hail Google!

I found this link:

[http://www.mail-archive.com/evolution@lists.ximian.com/msg02045.html](http://www.mail-archive.com/evolution@lists.ximian.com/msg02045.html)

The solution is to change the Proxy connection in the Network Settings section. Instead of using "system defaults," I changed mine to "Direct Connection to the Internet" and restarted Evolution-- voila!

Works great.

Josh

This worked perfectly for me too with Ubuntu 9.10 and Evolution 2.28.1. 
I don't want to try the other proposed solution of loading all images in all messages, because image-laden messages can be time consuming to download and bloat the evolution folders if many  are saved. I only automatically download images from senders who are in my address book and manually choose which other messages' images to download.
Jordan

---

### Post by apochry on 2011-03-27
> **kweejibo said:**
> All hail Google!

I found this link:

[http://www.mail-archive.com/evolution@lists.ximian.com/msg02045.html](http://www.mail-archive.com/evolution@lists.ximian.com/msg02045.html)

The solution is to change the Proxy connection in the Network Settings section. Instead of using "system defaults," I changed mine to "Direct Connection to the Internet" and restarted Evolution-- voila!

Works great.

Josh

Thanks a bunch Josh!

This made my day! It fixed the problem with the images and also my other issue in Evolution - it couldn't connect to the Google Address Book. After changing the setting to "Direct Connection to the Internet" it begun to work. :-)

I was struggling for 3 days with Evolution because of those two issues.
Thanks! Thanks! Thanks!

Izzo

---

### Post by scaremi on 2011-03-28
> **kweejibo said:**
> All hail Google!

I found this link:

[http://www.mail-archive.com/evolution@lists.ximian.com/msg02045.html](http://www.mail-archive.com/evolution@lists.ximian.com/msg02045.html)

The solution is to change the Proxy connection in the Network Settings section. Instead of using "system defaults," I changed mine to "Direct Connection to the Internet" and restarted Evolution-- voila!

Works great.

Josh

This worked for me. Thanks a lot!
Sergio

---

### Post by srara on 2011-05-29
> **days_of_ruin said:**
> Edit>Preferences>Mail Preferences>HTML Messages> Always load images from the internet. Have you all tried that?

Works great thanx a lot. :p

---

