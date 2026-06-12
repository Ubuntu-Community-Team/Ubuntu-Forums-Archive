---
title: "Can't run Pogo games with Ubuntu 13.10"
date: 2014-01-10
forum: Gaming &amp; Leisure
---

### Post by jgwphd on 2014-01-10
I have recently installed Ubuntu 13.10 (Processor: Intel® Core&#8482; i3-3120M CPU @ 2.50GHz × 4 and Graphics: Intel® Ivybridge Mobile  64-bit). My wife likes to play games at [www.pogo.com]("http://www.pogo.com") Unfortuniately, when she tries to load a game from Pogo in the firefox browser, she gets "Your Adobe Flash Player is out of date". When I checked the plugins, I have Shockwave Flash version 11,2,202,332 (shockwave Flash 11.2 r202). I checked the system files at usr/lib/mozilla/plugins and they show a libflashplayer.so 19.2 MB type=Unknown Dec 1 2013. This is the latest version according to ([http://get.adobe.com/flashplayer/?no_ab=1](http://get.adobe.com/flashplayer/?no_ab=1)). I get the SAME error message using the Chromium browser too ([http://game3.pogo.com/error/flava-upgrade-flash.jsp](http://game3.pogo.com/error/flava-upgrade-flash.jsp)). Again the Flash version shows as:shockwave Flash 11.2 r202. My belief is I have some kind of system problem since both browsers have the same problem. 

Also, I don't know if these are related but I also have been getting errors using Java from the same Pogo web site. To test Java I go to a Java test site ([http://javatester.org/version.html](http://javatester.org/version.html)) I get an error message: Application Blocked. Click for details - Java Plug-in 11.0.2.121 Using JRE version 1.8.0-ea-b121 Java HotSpot(TM) 64-Bit Server VM. Again both Firefox and Chromium show the same error. I don't know if these two problems are related. But I sure would like to allow my wife to play games at the Pogo web site. Any assistance on how to proceed or where to post these questions are greatly appreciated. Thanks!

---

### Post by ajgreeny on 2014-01-10
If you are using the open source openjdk for java I am afraid it will not work with that site.  You will need to install Oracle java by following the info from webupd8 at [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

Lots of java info as well as links to the above at [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by jgwphd on 2014-01-10
From the Java Control Panel - About Java. I already have the Java Standard Edition. Version 8 (build 1.8.0-ea-b121) Copyright (c) 2012, Oracle and its affiliates, installed.  So it seems I already have the correct Java version? Is that true?  The plug in shows "Java Plug-in 11.0.2.121 Using JRE version 1.8.0-ea-b121 Java HotSpot(TM) 64-Bit Server VM" The About Java message on the Plug in says "Java (TM) Plug-in 11.0.2 Version 11.0.2 Next Generation Java Plug-in 11.0.2 for Mozilla browsers. Is this Oracle? Does the "plug in" have to be "Oracle"?  Does it matter? 

I reduced security and now the Java tester web site works ([http://javatester.org/version.html](http://javatester.org/version.html)) and reports "Java Version: 1.8.0-ea from Oracle Corporation" So I must have the correct Java version. Is it ok to reduce security?  Now I am back to the original problem in my first post (details are there) the Pogo web site consistently shows the message "Your Adobe Flash Player is out of date" Can you provide any help with the flash problem? Thank-you

---

### Post by jgwphd on 2014-01-15
Can anyone PLEASE help me to, at least, better define the problem or   suggest where I should post for assistance if this is not the correct   place. My wife is getting anoyed at me because she can't play her Pogo games...  remember happy wife, happy life  :-)  Many Thanks!

---

### Post by arsenic23 on 2014-01-15
What OS was on the system before 13.10 ?  Pogo worked with that setup, right?  I know they have been changing things over there preparing for the incoming Java security updates.  I've had customers with Windows who needed tweaking just to get that blasted site to work. 
Have you tried using Chrome?  

Pogo is a mess.

---

### Post by jgwphd on 2014-01-15
I was using Ubuntu 12.04 before. My wife tells me it didn't work that well before either but, at least she could get on the site and "run some games". When I use the Chromium browser I get the same error message that I get with Firefox that says "Your Adobe Flash Player is out of date". Is there something I can do to better define exactly "the problem" (such as install a test tool, or some program that is known to give correct error/status messages or go to web site to verify things etc)? I'd like to drill down with some kind of diagnostic approach to find out exactly what is wrong. Many thanks again for your assistance. 

BTW, do you have any suggestions for a better games web site than Pogo?

---

### Post by arsenic23 on 2014-01-15
If you feel competent hex editing the flash module you could always do this:
[http://www.youtube.com/watch?v=7hEYuSbBsmU](http://www.youtube.com/watch?v=7hEYuSbBsmU)

--------------------------------------------------------------------------------------
Oh, and as for the java errors; in Windows there is a Java config panel were you can edit your java security settings.  I've never had the problem in linux, so I'm not sure how to go about that, but it's the direction you should probably be looking in.

---

### Post by jgwphd on 2014-01-15
I have done hex editng in the past. I have watched the video and I will give it a try in a few days (I am leaving on business for a day or two). This seems straight forward (I do have a slightly different version of the flash module than the one shown in the video but the module editing technique should work) and I do appreciate your response. Also the "libflashplayer.so" module was in the /usr/lib/ directory in the video, but in my machine (13.10) it is in the /usr/lib/flashplugin-installer directory. I assume this module moved in 13.10 to this directory. Is that the correct module location to modify? I'll also try out using the Eterm editor as shown in the video too  :-)

It seems to me, the Pogo people don't want any Linux customers? I think I need to encourage my my wife to take her business somewhere else.

As for Java, I do have the Oracle 8 Java control Panel installed. I'll try that if I get any Java errors after I get flash working.

---

### Post by jlguru on 2014-01-17
Had same problems ... Adobe's Flash for Linux is an older version and POGO pukes without the latest/greatest.

solved by installing Chrome browser. Chrome and POGO play well together.

Live long, and prosper

---

### Post by jgwphd on 2014-01-18
Hi Arsenic23! I did the hex editing as described in the video with some modifications since the my flash module wasn't the exact same (but close enough) and it is located in a different directory (Path: /usr/lib/mozilla/plugins/libflashplayer.so). Now I have Pogo running in Mozilla Firefox. I just want to say THANKS! for the pointer to the video. My wife is happy she can at least run Pogo in Firefox  :-) 

As you know from my first post, Pogo wasn't working in the Chromium browser either. I got the same "Your Adobe Flash Player is out of date" message. But since I edited the "libflashplayer.so" module (as described by the video) the symptom for Pogo in the Chromium browser changed. Now when I start Pogo in Chromium I get the message "Shockwave Flash has crashed" and the Pogo game loading stalls (and it generated a bug report the first time I tried it). In the Chromium about:plugins it does show: [COLOR=#000000][FONT=Ubuntu]**Adobe Flash Player**[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu](2 files)[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu]- Version: 11.8 r800[/FONT][/COLOR] Shockwave Flash 11.8 r800 (see below for details) . So it appears Chromium is using the same hex edited module as Firefox. Is there something different I need to do with Chromium? ...perhaps a different Flash version numbers? Any further assistance would be appreciated.  Many thanks for the assistance so far!

From chrome://Plugins display:

[COLOR=#000000][FONT=Ubuntu]**Adobe Flash Player** - Version: 11.8 r800Shockwave Flash 11.8 r800

[TABLE]
[TR]
[TD="class: plugin-details-label"]Name:[/TD]
[TD]Shockwave Flash[/TD]
[/TR]
[/TABLE]


[TABLE]
[TR]
[TD="class: plugin-details-label"]Version:[/TD]
[TD]11.8 r800[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD="class: plugin-details-label"]Location:[/TD]
[TD]/usr/lib/mozilla/plugins/libflashplayer.so[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD="class: plugin-details-label"]Type:[/TD]
[TD]NPAPI[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD="class: plugin-details-label"][/TD]
[TD]Disable[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD="class: plugin-details-label"]MIME types:[/TD]
[TD][TABLE="class: mime-types"]
[TR="class: header"]
[TD]MIME type[/TD]
[TD]Description[/TD]
[TD]File extensions[/TD]
[/TR]
[TR]
[TD]application/x-shockwave-flash[/TD]
[TD]Shockwave Flash[/TD]
[TD][TABLE="class: hlisting"]
[TR]
[TD].swf[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[TR]
[TD]application/futuresplash[/TD]
[TD]FutureSplash Player[/TD]
[TD][TABLE="class: hlisting"]
[TR]
[TD].spl[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]



[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Disable    _  Always allowed    (BTW this box is shown checked in the browser even though it doesn't show here in the ubuntu forum posts)
[/FONT][/COLOR]

---

