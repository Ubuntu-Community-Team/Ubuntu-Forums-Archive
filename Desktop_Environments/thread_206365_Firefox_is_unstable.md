---
title: "Firefox is unstable"
date: 2006-06-30
forum: Desktop Environments
---

### Post by Peepsalot on 2006-06-30
Well, I started [this](http://www.ubuntuforums.org/showthread.php?t=200246) thread not too long ago, about me not being able to view one particularly large HTML file in firefox, without it crashing.  Since then I gave in and just printed the pieces I needed from the smaller broken up pages.  I don't really care anymore about that problem, the only remarkable thing about that crashing was that it was consistent.

But actually, firefox has been crashing on many other occassions.  Many times it has crashed immediately after I have pressed Ctrl-S.  Other times it will just crash seemingly randomly during use.  It has crashed a lot in the past few weeks.

This is especially bothersome since almost everything I do on this computer is through the browser.  I frequently have multiple windows and multiple tabs open: for developing my own website, programming references & documentation, google searches, my webmail page, etc.  So when firefox crashes, I lose track of where I was...times 20.

Anyways, my system doesn't seem like it is very stable in general though, could it possibly be something that is not even firefox's fault?

Is there anything I can do to track down the source of my problems?  I'm getting tired of this.  I almost want to go back to windows. :confused:

---

### Post by Peepsalot on 2006-06-30
Last crash I had, the talkback extension popped up.  Being the curious fellow that I am, I clicked the "Details" button.  Well, guess what: that crashed too.  Talkback just disappeared.  This is infuriating.

---

### Post by YourDoom123 on 2006-06-30
hmm... that's very odd. can you post the output of 

```

dmesg | tail

```

after a crash? just copy and paste that line into a terminal.

---

### Post by ahaslam on 2006-06-30
[QUOTE=Peepsalot]Well, I started [this](http://www.ubuntuforums.org/showthread.php?t=200246) thread not too long ago, about me not being able to view one particularly large HTML file in firefox, without it crashing.  Since then I gave in and just printed the pieces I needed from the smaller broken up pages.  I don't really care anymore about that problem, the only remarkable thing about that crashing was that it was consistent.

But actually, firefox has been crashing on many other occassions.  Many times it has crashed immediately after I have pressed Ctrl-S.  Other times it will just crash seemingly randomly during use.  It has crashed a lot in the past few weeks.

This is especially bothersome since almost everything I do on this computer is through the browser.  I frequently have multiple windows and multiple tabs open: for developing my own website, programming references & documentation, google searches, my webmail page, etc.  So when firefox crashes, I lose track of where I was...times 20.

Anyways, my system doesn't seem like it is very stable in general though, could it possibly be something that is not even firefox's fault?

Is there anything I can do to track down the source of my problems?  I'm getting tired of this.  I almost want to go back to windows. :confused:[/QUOTE]

Nothing would EVER make me go back to windows. But I've just had my first FireFox crash and i'm quite concerned, as the main reasons that I moved to Linux were stability, security & freedom. See this screen:
[ATTACH]11995[/ATTACH]
As you can see, I was hardly stretching my system resources.

btw, the only time my system has crashed before was while playing 3D games. My particular chipset (via k8m800) is not fully supported, so that was to be expected.

Tony.

---

### Post by atoponce on 2006-06-30
[quote=Peepsalot]Last crash I had, the talkback extension popped up.  Being the curious fellow that I am, I clicked the "Details" button.  Well, guess what: that crashed too.  Talkback just disappeared.  This is infuriating.[/quote] 
Can you answer these questions:[LIST]
[*]What version of Firefox are you running?
[*]What extensions are currently installed?
[*]How long has Firefox been running before it crahses?
[*]How many tabs have you opened and closed prior to the crash?
[*]What are your system resources (RAM, CPU, etc.)?[/LIST]This can give us a good picture of exactly what is happening here.  I use Firefox religiously on Ubuntu Dapper, and have only had a few minor crashes, so something is definitely getting in the way.

---

### Post by kpkeerthi on 2006-06-30
Most of the crashes are attributed to the 3d graphics cards. What graphics  hardware are you running?

Also do you have flash plugin? Did you observe if the pages you visit have embedded flash when firefox crashes? That used to happen to me and I had to install flash from adobe.com and the problem went away. Its been stable ever since.

---

### Post by peterthewolf on 2006-06-30
Not just firefox but opera too so perhaps its not either but dapper itself. Since installing dapper I can never use the internet for long and if i try to download a file of more then 1 or 2 mb it will certainly freeze. I can use a non-wireless adsl modem router, a wireless adsl modem router, or a usb adsl modem  and all give the same results.

---

### Post by Peepsalot on 2006-06-30
[QUOTE=kpkeerthi]Most of the crashes are attributed to the 3d graphics cards. What graphics  hardware are you running?

Also do you have flash plugin? Did you observe if the pages you visit have embedded flash when firefox crashes? That used to happen to me and I had to install flash from adobe.com and the problem went away. Its been stable ever since.[/QUOTE]
My computer is an [Asus Pundit P2-AE2](http://www.newegg.com/Product/Product.asp?Item=N82E16856110040&CMP=OTC-pr1c3watch&ATT=56-110-040)
It is a mini-itx combo that came with a motherboard with built in video.  The specs say it the graphics card is: "VIA UniChrome Pro 3D Graphic"

I wouldn't be surprised if the video card had something to do with it, it's a piece of crap as far as I can tell.  I had to completely disable screensavers, they were causing my computer to lock up constantly, requiring a power down each time.  I'm not even completely sure that my drivers are setup correctly(X settings are just set to "VIA", is there any options more specific than that?).  I switched to XFCE because I read that the GUI was supposedly more responsive, but it's still pretty bad on my system.

atoponce: I will try to answer those questions tonight when I get home.  I am at work right now, so I can't check all that.

For the flash plugin, I used whatever Automatix installed for me.

Thanks for the help so far everyone.

---

### Post by Jasper Houtman on 2006-06-30
Did you try the [Unichrome project drivers]("http://sourceforge.net/projects/unichrome")? 
Had no more crashes after I installed those.

---

### Post by ahaslam on 2006-06-30
[QUOTE=Jasper Houtman]Did you try the [Unichrome project drivers]("http://sourceforge.net/projects/unichrome")? 
Had no more crashes after I installed those.[/QUOTE]
These drivers aren't the best, the x.org & openchrome drivers are what I recommend. It's only really the 3D acceleration that's still buggy, I doubt that'll cause FireFox to crash.

Tony.

---

### Post by Peepsalot on 2006-06-30
[QUOTE=Anthony Haslam]These drivers aren't the best, the x.org & openchrome drivers are what I recommend. It's only really the 3D acceleration that's still buggy, I doubt that'll cause FireFox to crash.

Tony.[/QUOTE]
Funny, I just reread your first post in this thread and realized you have the same chipset(k8m800) as me.

I'd like to try the openchrome drivers, but I'm afraid I don't completely understand what I'll need to do to install them.

Found this page:
[http://www.openchrome.org/snapshots/ubuntu/](http://www.openchrome.org/snapshots/ubuntu/)
Do I need all three of those files?  Will it be a problem that I am on Dapper, and those are for Breezy?
I don't want to screw anything up.  Can I just run dpkg on the two .deb files?  

And then what about this tgz with the kernel modules?  My system has a AMD Sempron(not 64bit) 3000+.  I installed the linux k7 kernel package not too long ago.  That page says the kernel modules are for 686 kernel, should I be using that one instead?  Do I even need those modules?
The instructions on that page are not clear to me, I'm a bit of a noob.

Why do you not recommend the Unichrome project? 


Answers to atoponce questions:
> 
What version of Firefox are you running?
1.5.0.4

What extensions are currently installed?
    Dom Inspector 1.8.0.4
    New Tab Homepage 0.3
    Web Developer 1.0.2
    del.icio.us 1.1
    FireBug 0.4
    Javscript Debugger 0.9.87
    Talkback 1.5.0.4

How long has Firefox been running before it crahses?
    I don't really have an answer to this.  I can make it crash at any time, with the link from my first post.  Other crashes are more random.  Usually i've probaby had it open for multiple hours before it crashes.

How many tabs have you opened and closed prior to the crash?
   It's not consistent, it might crash with just a couple, or with 20.

What are your system resources (RAM, CPU, etc.)?
   1GB single dimm RAM
   AMD Sempron(not 64bit) 3000
   Asus Pundit P2-AE2
        North Bridge 	VIA K8M800
        South Bridge 	VT8237R
        VIA UniChrome Pro 3D Graphic


---

### Post by ahaslam on 2006-07-01
[QUOTE=Peepsalot]I'd like to try the openchrome drivers, but I'm afraid I don't completely understand what I'll need to do to install them.
....
Why do you not recommend the Unichrome project? [/QUOTE]
For more info about the different Via drivers, [look here]("http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=The+Different+Unichrome+family+display+drivers").
For help installing onenchrome drivers, see these:
[[installation] General 6.06 - VIA Unichrome S3 display driver]("http://ubuntuforums.org/showthread.php?t=184512")
[[multimedia] Ubuntu 6.06 - Anyone find working instructions for installing UNICHROME drivers?]("http://ubuntuforums.org/showthread.php?t=203312")
Be aware that 3D accel is buggy with our chipsets, [see here]("http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=3DStatus").

Tony.

---

### Post by Peepsalot on 2006-07-01
It just crashed again.  I tried to right click and choose "Save Image As...", and all firefox windows disappeared.  Talkback came up, I tried to view the details again, and talkback disappeared also. 

result of "dmesg | tail" (immediately after firefox crash):
```

[17757548.736000] VFS: busy inodes on changed media.
[17757548.760000] VFS: busy inodes on changed media.
[17757550.788000] VFS: busy inodes on changed media.
[17757550.808000] VFS: busy inodes on changed media.
[17757550.836000] VFS: busy inodes on changed media.
[17757550.856000] VFS: busy inodes on changed media.
[17757552.884000] VFS: busy inodes on changed media.
[17757552.904000] VFS: busy inodes on changed media.
[17757552.928000] VFS: busy inodes on changed media.
[17757552.952000] VFS: busy inodes on changed media.

```

result of "dmesg | tail"(after talkback crash):
```

[17757580.148000] VFS: busy inodes on changed media.
[17757580.172000] VFS: busy inodes on changed media.
[17757582.200000] VFS: busy inodes on changed media.
[17757582.220000] VFS: busy inodes on changed media.
[17757582.240000] VFS: busy inodes on changed media.
[17757582.264000] VFS: busy inodes on changed media.
[17757584.288000] VFS: busy inodes on changed media.
[17757584.312000] VFS: busy inodes on changed media.
[17757584.332000] VFS: busy inodes on changed media.
[17757584.356000] VFS: busy inodes on changed media.

```
I have no clue what that's about.  Is that information even relevant?  I think my kernel just generates these lines all day long.  Every time I dmesg, the list of numbers are different.
The full dmesg output(without tail) is just full of those same lines, and nothing else.

I reopened firefox and tried to save the file again, and it worked fine.

Update:
I realized where the log file is (i guess), so I decided to check the whole thing.  There is a 6mb kernel.log in /var/log, and a 14mb kernel.log.0
I tried to see filter out the lines with this inode error(since a 3-5 are generated every second).
I found out grep -v inverts the output, displaying lines that don't contain the search string, so:
```

peeps@ninja:/var/log$ cat kern.log | grep -v inodes
peeps@ninja:/var/log$ cat kern.log.0 | grep -v inodes
Jun 30 09:03:01 ninja kernel: [17652216.668000] usb 1-2: USB disconnect, address 5
peeps@ninja:/var/log$

```
Nothing really but inodes messages.

---

### Post by Peepsalot on 2006-07-01
And I feel dumb for asking this, but how the heck do I get glxgears to tell me the framerate?  I'd like to get a before and after for these drivers(assuming I'm even capable of installing them).

It's supposed to go to cout automatically?  I run it from gnome terminal 2.14.2, and it outputs nothing.  I've had this running for the past 30 miinutes.  

```

peeps@ninja:~$ glxgears
__driCreateNewScreen_20050727 - succeeded
*blinking cursor goes here*

```

I'm having trouble controlling my rage.](*,)   Nothing ever works!

---

### Post by ahaslam on 2006-07-01
[QUOTE=Peepsalot]And I feel dumb for asking this, but how the heck do I get glxgears to tell me the framerate?  I'd like to get a before and after for these drivers(assuming I'm even capable of installing them).

It's supposed to go to cout automatically?  I run it from gnome terminal 2.14.2, and it outputs nothing.  I've had this running for the past 30 miinutes.  

```

peeps@ninja:~$ glxgears
__driCreateNewScreen_20050727 - succeeded
*blinking cursor goes here*

```

I'm having trouble controlling my rage.](*,)   Nothing ever works![/QUOTE]

"glxgears -printfps"

I feel we're drifting off topic (though it is your thread), it may not be helpful to others. It's very unlikly that Via drivers have any adverse effect upon FireFox, as it's the 3D accel that's buggy. The exception is if you're using a composite manager (for drop shadows & transparencies), then it would affect stability in general.

Tony.

---

### Post by Peepsalot on 2006-07-01
Yeah sorry, not trying to go offtopic, but I really thought the video could possibly be a source of problems.  And for now, it's the only solution available for me to try.

Unless someone has some insight on how to find the source of these crashes.  It seems my kernel logs do not have any information relevant to the firefox crashes(those messages in the log are generated constantly, even without any firefox process running).  Is there maybe some other log file that firefox generates that i can look at directly?

---

### Post by Peepsalot on 2006-07-01
Well, i found this extension called "Crash Recovery" that sounds nice.
[https://addons.mozilla.org/firefox/1955/](https://addons.mozilla.org/firefox/1955/)

It's not really the solution I was looking for but I think it will keep me from tearing my hair out on every crash.

I'm not giving up trying to find the source of the problem though, so if anyone has more suggestions, please speak up.

---

### Post by Peepsalot on 2006-07-01
Could it be bad RAM? I ran a couple passes of the livecd memory test when I first got this computer, and it passed as I recall.  But i'm not sure anymore, could the test have missed it somehow?

---

### Post by ahaslam on 2006-07-02
[QUOTE=Peepsalot]Last crash I had, the talkback extension popped up.  Being the curious fellow that I am, I clicked the "Details" button.  Well, guess what: that crashed too.  Talkback just disappeared.  This is infuriating.[/QUOTE]
I read on another thread that some extensions are incompatible with others and cause FireFox to crash. If you're not using fancy eye candy and it's only FireFox with this problem, it's probably the case. 

**Try removing all extensions and then adding only essential extensions, one at a time - see what works with what.**

**If that fails completely remove FireFox from Synaptic and delete the directory, '/home/username/.mozilla/firefox' (hidden folder). Reboot and then reinstall from Synaptic. **

Tony.

BTW, I looked at the link on your first thread, it directs me to a mirror site for 'php_manual_en.html.gz'. If I click the download I get the prompt to 'open with' or 'save as'. I chose open with 'Archive Manager', which opened and then I clicked on the html file. It opened up in a new FireFox window quickly & flawlessly. **A reinstall of FireFox may be the solution.**

Tony.

---

### Post by Peepsalot on 2006-07-02
Well, i basically did try those things, in my first thread, which was about me opening a specific document that consistently crashes my browser.
[http://www.ubuntuforums.org/showthread.php?t=200246](http://www.ubuntuforums.org/showthread.php?t=200246)
I'm not sure if that problem is related to the more random crashes though.

I also tried fasterfox(or is it called swiftfox) briefly, which exhibited the same problems.  I switched back to normal firefox since fasterfox didn't seem to have talkback.

---

### Post by alb1954 on 2006-07-02
I had this trouble too but only with Dapper. I switched back to Breezy.

---

### Post by Peepsalot on 2006-07-02
Ok, so I tried installing openchrome with instructions from this thread that Anthony linked me to:
[http://www.ubuntuforums.org/showthread.php?t=203312](http://www.ubuntuforums.org/showthread.php?t=203312)
I got through that small list of commands, but I couldn't tell if that was all i needed to do.  I thought I would have to edit xorg.conf or something?  My glxgears are consistenly right around 560fps, same as before I tried to install the drivers.
Anyways, after I rebooted, I tried to load the file that consistently crashes firefox for me.  Well, it loaded the whole thing, so things are looking good.  Hopefully the other random crashes will not happen so often either now.

I'm just wondering if the drivers were what fixed the problem, or something else I did.  How can I verify that the drivers are installed properly?  My video still seems slow to me, i was hoping it would speed up a bit.

Another thing to note, my kernel log is not filling up with "inodes" messages anymore.  When I searched on this topic, this is the same thing others said: no one knows what they are about, but rebooting made it stop.  Still don't know if that is related or not.

---

### Post by DJiNN on 2006-07-02
I've been having more & more problems with Firefox crashing as time has gone on. It hardly ever used to crash, and now never a day goes by "Without" it crashing, and the only saving grace (if you can call it that) is the Crash Recovery extensions that let you go back to where you were before it crashed.... which is great, but sometimes can be a pain because if a particular page is causing a crash (fro whatever reason) then it'll just reload that page (if it even gets that far) & then Crash again!! :)

My answer, after much frustration, was just to use Opera, which hasn't bombed at all opn me yet, but i do miss some of the FF extensions... Sigh! :)

Good luck anyway. & if i find some miracle cure i'll be sure to post it..... but don't hold your breath! :)

DJiNN

---

### Post by Peepsalot on 2006-07-03
Well, so much for my optimism, firefox just crashed again.  I think it really sucks that the only option is to not use firefox in Dapper.

I'd really like to try to help stamp out this bug, but I just don't know what I can do.

---

### Post by ahaslam on 2006-07-03
BTW, I've had no more crashes, so that should ease your mind regarding our graphics cards.


Tony.

---

### Post by Tamihania on 2006-07-03
Hi,
I just would like to confirm that I also "fight" with the issue since I came back from my holidays (5 days ago!) and upgraded Xubuntu (linux, Firefox) - Firefox is crashing constantly as often as I try to get to [www.nordea.pl]("http://www.nordea.pl") as well as to any site with hidden advertisments... maybe it's a feature? ;)

Anyway - I consider it a bug. The dmesg | tail output after crashing is as follows:

> tami@ubuntu:~$ dmesg | tail
[17179601.204000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179601.204000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
[17179601.204000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode
[17179601.336000] NET: Registered protocol family 10
[17179601.336000] lo: Disabled Privacy Extensions
[17179601.336000] IPv6 over IPv4 tunneling driver
[17179602.660000] ppdev: user-space parallel port driver
[17179602.928000] apm: BIOS not found.
[17179603.472000] ra0 (WE) : Driver using old /proc/net/wireless support, please  fix driver !
[17179611.360000] ra0: no IPv6 routers present 
I found some similiar not resolved bugs on launchpad but nothing exactly the same. I am afraid to fix my ralink driver because it works and can connect me to the Internet without a problem which is a kind of Xubuntu miracle... :)

Anyway - as I am a bit busy now - I will try to fill up the bug report when I come back home. 

After my "n00b's" meaning and all the reading on the net the bug has something in common with new kernel version or Xorg...

I will let you all know when I fill the bug report and ask you for confirmation - but feel free to make it earlier ;)

Many kind regards,

tami

PS. The temporary solution to the problem - using Epiphany (it's not crashing on any webites) + Firefox (on sites like Ubuntu Forum)
PS2. Disabling IPv6 did not solve the problem either...
PS3. I would be of course grateful for any suggestion how to fix the problem and any help from people more experienced than me with (X)Ubuntu:oops:

---

