---
title: "Flash video and Firefox"
date: 2009-02-05
forum: General Help
---

### Post by Openrulers on 2009-02-05
I installed Ubuntu 8.10 with Wubi on Windows XP machine and Windows Vista machine. Both having similar problems with flash video playing in Firefox 3.0.

In youtube First few videos plays well. then a next one starts with blank with sound only. I need to refresh with Ctrl + F5 to sort this out. Same happen if Firefox is running for a longer period. Then I need to restart Firefox. 

I seen various types of problems reported with flash here.

I am not sure this is a issue with Ubuntu or Firefox.
 
I installed flashplugin-nonfree package in both cases.

your thoughts and suggestion please.

---

### Post by mb_webguy on 2009-02-05
Did you install the 32-bit or 64-bit version of Ubuntu?  I don't have any experience with Wubi installations, but...

Most issues with Flash seem to have been resolved in 8.10, at least in the 32-bit version.  I've been seeing considerably fewer posts concerning Flash on Intrepid than I did with Flash on Hardy.  However, I am occasionally having the problem you're experiencing (i.e. a gray box in place of the Flash video, occasionally with sound).  I didn't have this problem with the 32-bit version of Intrepid.  The 64-bit version of the Flash plugin for Linux is still in alpha, though, so some issues are to be expected.

If you're using the 32-bit version of Intrepid, though, then it may have something to do with Wubi, and I don't have any advice.

---

### Post by adoyle626 on 2009-02-05
Some people have issues with Firefox 3.
If you are using Firefox 3, try out opera [http://www.opera.com/]("http://www.opera.com/")
If that doesn't fix it, then I do not know.

---

### Post by Openrulers on 2009-02-10
I am using a 32 bit edition of Ubuntu 8.10
This is my Kernel: 2.6.27-11-generic
Thank you
I will look at opera as well.
Let me see

---

### Post by Openrulers on 2009-02-13
But running firefox with this command " gksudo firefox " is not having any problem with Flash.
I am not sure that is the safe mode. 
I believed this is the safe mode command " firefox -safe-mode ". 
But plugins are also disabled in first one. 
Opera seems to work. But after restart I am gettting this error messege 

Opera encountered a problem during plug-in set-up.

Plug-ins will not work properly.

Check your installation.



Could not locate plug-in executable 'operapluginwrapper'

This executable is included in the install package.



Searched directory

Your suggestions please.

---

### Post by Openrulers on 2009-04-23
I do have all strange problem with flash in Firefox. 
Flashvideo of youtube is jittery. BBC iplayer plays without any problem. But if you click videos link of a bbc page, then after playing few videos visuals go blank, then i need to refresh browser each time to play video or I need to restart browser to play it correctly. 
This is even true in Safe Mode of Firefox 3.0.9. Shockwave flash 10.0.r22 plug-in is installed. I am using Ubuntu 8.10.

[COLOR="Red"][SIZE="2"]This was the log I got on terminal when I was running firefox in safe mode. Please find the attachment.[/SIZE][/COLOR]

Your suggestions please

---

### Post by krnekhelesh on 2009-04-23
I dont about firefox but opera has the same problem you mentioned...ie blank video with only sound. And also what I noticed at those time is that the browser stops responding and you need to force quit it.

So I wouldnt recommend opera. But I dont know why firefox is acting like that for you.

---

### Post by Vaphell on 2009-04-23
i had similar problem with previous versions, i gave flash10  from adobe site a try (64bit in my case, 10r22) and it fixed it

---

### Post by paul@cyberengel.com on 2009-04-24
I upgraded to Jaunty (32-bit) last weekend and nothing I've found has fixed the Firefox/Flash problem.  (No flash objects work at all.)  I've tried uninstalling, purging, reinstalling flashplugin-nonfree, adobe-flash and flashintaller.  I've even tried downloading the plugin from Adobe, but no joy.

I installed Opera, and it works fine... video and sound.

---

