---
title: "Web Filtering How-to???"
date: 2006-06-30
forum: Desktop Environments
---

### Post by shane2peru on 2006-06-30
Ok, I have searched these posts for recent material, and have turned up nothing recent.  I was wondering if anyone knows how to setup dans guardian, or squid guard, or any other internet filtering type program.  I have tried both, and found it very dificult, with many problems.  I'm not asking for the moral debate that is so often debated with this topic, just for a how to in getting these to work with Ubuntu.  It seems that dansguardian's web page: [www.dansguardian.org](www.dansguardian.org)  or .com doesn't work.  Hence this thread.  Any help would be greatly appreciated by many.

Shane

---

### Post by majstor on 2006-06-30
What do you need to filter out? For ads I only use Firefox and one extension. On windows I used Proxomitron and it was good, really powerful and freeware application.

---

### Post by shane2peru on 2006-06-30
I'm looking for a filter that would filter porn, sexual type things, violence, crude language ect.  For Windows we have Trend Micro, has a filter with their internet security package.  I would like something for Linux, and something to recommend to others as well.  -- However it needs to be simpler than what I have seen so far. 

Shane

---

### Post by Dr. Nick on 2006-06-30
Privoxy is a good filtering program, Its fairly easy to setup and you dont really notice it running.

The problem is that it does not block all the violence/language by default.

It has a file that you can add urls to block, but doesnt provide a list or you..

If you know of a site that has a text file of all the crap you want to block you could use it though.

---

### Post by shane2peru on 2006-06-30
Dr. Nick,

    Thanks!  I installed it via apt, and don't know how to configure it now.  Or, do I not need to do anything?  Sorry, I have been trained by windows for more than 10 years now.  Any help  on this is appreciated!  

Shane

---

### Post by Dr. Nick on 2006-06-30
[quote=shane2peru]Dr. Nick,

    Thanks!  I installed it via apt, and don't know how to configure it now.  Or, do I not need to do anything?  Sorry, I have been trained by windows for more than 10 years now.  Any help  on this is appreciated!  

Shane[/quote] 
This may take a bit of interrupting since I am on windows now and privoxy may be a tad different.

If its installed then open your browser and set it to conncect through a proxy

the proxy address is 

127.0.0.1 and port is 8118

after setting that it should be working. It will help filter out ads and cookies by default, If you want to block urls then look at the user.action file. I am not sure where it is since I am currently on windows :(

In that file is a some docmentation for how to block images out, the same thery works for blocking out webpages. If you add [www.yahoo.com]("http://www.yahoo.com") to the { +block } section then you will not be able to get thier anymore. Only problem is that on the page it loads instead their is a option to bypass the block and go anyway. I would imagine that you could disable that option, but im not sure how to.

If you have a subscription to a site that keeps a updated blocklist or know of a free blocklist then you could just copy/paste all desired urls into the user.action file. 

As far as I know thier really isnt a filter that does a good job without you telling it which sites to block, none that can "tell" automatically if a site is bad befor loading it.


EDIT
[http://www.privoxy.org/user-manual/actions-file.html](http://www.privoxy.org/user-manual/actions-file.html)

may help some. I see you are using kde? If you are using konqueror as your browser I am not sure if you set the proxy in konqueror or in a kde contolr panel

The only 2 flaws i see ( pretty big flaws) in this approach is the option to bypass the block, which you may be able to stop. And the fact that if you reconfigure the browser not to use the proxy everything will work, nut if the browser is set to use privoxy and privoxy isnt running then no websites will load.

---

### Post by ryanclem on 2006-06-30
We have DansGuardian set up and it uses sets of rules (such as if it sees certain phrases or words) to determine if a page is vulgar or not.  So far it's worked pretty well.  It's also very customizable if you need to adjust what/how much it blocks.  It was a little confusing to set up but I think it was worth it in the end.  The problem is that Dan's Gaurdian needs to access the internet through a proxy server.  Basically what you have to do is set up squid, tell Dan's Gaurdian to use the squid proxy server to connect to the internet (this is accomplished through editing the Dans Guardian config files), and then tell Firefox (or whatever web browser you're using) to use Dans Gaurdian as its proxy server (which is accomplished by going to Options [or maybe it's Preferences] dialog and instructing it to use localhost port 8080).  Once I had figured out that's what you had to do it wasn't too hard to set up, but I'm a more experienced user and you may still have some difficulty.  Let me know if this helps!

---

### Post by Dr. Nick on 2006-06-30
Ive heard of dansguardian, looks to be exactly what he wants to do, but it appears the site for it is down. That is why i recommended privoxy+custom blocklist.

It would be cool to see a link to dansguardian, or is it no longer around?

---

### Post by shane2peru on 2006-06-30
[QUOTE=ryanclem]We have DansGuardian set up and it uses sets of rules (such as if it sees certain phrases or words) to determine if a page is vulgar or not.  So far it's worked pretty well.  It's also very customizable if you need to adjust what/how much it blocks.  It was a little confusing to set up but I think it was worth it in the end.  The problem is that Dan's Gaurdian needs to access the internet through a proxy server.  Basically what you have to do is set up squid, tell Dan's Gaurdian to use the squid proxy server to connect to the internet (this is accomplished through editing the Dans Guardian config files), and then tell Firefox (or whatever web browser you're using) to use Dans Gaurdian as its proxy server (which is accomplished by going to Options [or maybe it's Preferences] dialog and instructing it to use localhost port 8080).  Once I had figured out that's what you had to do it wasn't too hard to set up, but I'm a more experienced user and you may still have some difficulty.  Let me know if this helps![/QUOTE]
Ryanclem,

How did you get Dans Guardian setup? I have been tinkering with it for several hours and was not able to get it to work.  I followed the Edubuntu setup guide for squid as well, and was not able to get either one to work.  I did get the one above to work.  Privoxy.  That was really simple, but I don't know about the quality of it.  Every time with Dans Guardian I kept getting errors, same with squid.  I would prefer to use these, as they seem to be better.

Shane

---

### Post by shane2peru on 2006-06-30
Is there a way to get this privoxy to work with Squid?  Assuming I can get squid to work, that seems like an option, or is it Dans Guardian that actually does the filter work.  Well, anyway, thanks to the both of you.  I will keep my eyes open for more posts, and help.  

Shane

---

### Post by Dr. Nick on 2006-06-30
I believe dans guardian does the filtering, I researched it awhile ago but never used it.

Privoxy could do the filtering for you, it would just be time-consuming to setup and very easy to bypass if someone was determined enough. Hope you figure out a solution. I know their are several windows programs that say they filter it all out, but I doubt that half of them do a good job lol. I tried one once and the amount of false positives was very annoying

---

### Post by ryanclem on 2006-06-30
Dansguardian is the program that does the actual filtering, it just needs a proxy to run through.  I installed squid using the synaptic package manager.  Then I installed dansguardian the same way.  Do you know why it won't let you install squid?  I seem to recall when trying to install the latest version of DansGaurdian it needed ClamAV to be installed and that didn't want to install for some reason.  I think it was that it couldn't find some folder and all I had to do was create the folder myself.  A little weird, but it worked after that.

---

### Post by shane2peru on 2006-06-30
ryanclem,

     I did get both installed it was the configuration that I had problems with.  Here is the error I get:
```

Error creating/opening pid file:/var/run/dansguardian.pid

```

Here is another error:
```

~$ sudo dpkg-reconfigure dansguardian
Stopping DansGuardian: dansguardian.
Starting DansGuardian: Error connecting to parent proxy
invoke-rc.d: initscript dansguardian, action "start" failed.

```

I had squid installed, but didn't get it configured.  I'm trying these instructions now:  [http://www.pilpi.net/journal/item-985.php](http://www.pilpi.net/journal/item-985.php)  - however they are a little vague and still leave out steps for us newbies.

Shane

---

### Post by shane2peru on 2006-06-30
Ok, I got it to work.  It took some time.  If you have never tried to install dansguardian, it is easier, once you have messed with the configuration files, it stays on the computer even if dansguardian is deleted, therefore you will need to delete those conf files for dansguardian and squid, or anything else that has been installed and edited.  (If you edited them, you should know where to find them.)  If you follow these instructions it seems to work the best.  -  [http://www.pilpi.net/journal/item-985.php](http://www.pilpi.net/journal/item-985.php)  - I found them on another thread here somewhere.  Thanks for the help.

Shane

---

### Post by Dr. Nick on 2006-06-30
Glad you got it, if you want to remove the config files later then you can use synaptic to do a "complete removal" which should purge the configuration files aswell.

---

