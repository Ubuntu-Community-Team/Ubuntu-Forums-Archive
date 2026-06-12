---
title: "Firefox can't access Writely.com"
date: 2005-10-10
forum: Desktop Environments
---

### Post by fheinsen on 2005-10-10
Firefox on Ubuntu Hoary can't access some websites, including writely.com -- the web browser just hangs.

*** SOLVED ***
The problem in this particular case was caused by a bug in the Firestarter firewall. See post #33 in this thread ([http://ubuntuforums.org/showpost.php?p=401223&postcount=33]("http://ubuntuforums.org/showpost.php?p=401223&postcount=33")) for the solution.

---

### Post by Efwis on 2005-10-10
I just tried it, works fine here. what version of ff are you using? that might have something to do with it.

---

### Post by fheinsen on 2005-10-10
I'm using version 1.0.7 -- the latest officially supported version.

---

### Post by Efwis on 2005-10-10
hmm, thats odd. same version I'm using.

i wonder if you might be running into the problem from that cogent-level3 thing going on right now. I know that is causing a lot of headaches for internet users.

other than that you might want to try and clear your FF cache and see if that helps or not.

---

### Post by fheinsen on 2005-10-10
Thank you.

The problem can't be caused the Level 3-Cogent snafu, because my Ubuntu box uses the same Internet connection as my Windows box, yet Firefox on the Windos box can access the site just fine.  

I had already trying clearing the cache before posting the problem here, and that didn't work either.

---

### Post by fheinsen on 2005-10-10
Any other suggestions, of course, would be appreciated...

---

### Post by Efwis on 2005-10-10
i'll do a little research and see what i can come up with. this is really weird. hopefully someone else can help too.

---

### Post by Hairy_Palms on 2005-10-10
i have the exact same problem with [http://www.mapleglobal.com/](http://www.mapleglobal.com/) i dont know why it is, unless the website is demanding windows if so i beleive theres an extension that lets u tell the website that you are running windowsxp even if you arent

---

### Post by fheinsen on 2005-10-10
Lo and behold, I *can't* access  [http://www.mapleglobal.com/]("http://www.mapleglobal.com/") either from Firefox on my Ubuntu Hoary box -- it hangs in just the same way as writely.com.  However, I can access both sites just fine with Firefox running on my Windows box.  Clearly there's a pattern here.

Suggestions anyone?

---

### Post by Efwis on 2005-10-10
ok I was just looking at the source code for both those sites. the only thing I am seeing that is the same is the JS. do you both have java installed on your systems??

---

### Post by Lord Illidan on 2005-10-10
I believe it may be the java...
I have it installed on my system and both sites work perfectly on my box...

---

### Post by Benchrest on 2005-10-10
I'm using Firefox 1.0.7 on both windows and Hoary. both have Java installed. Windos works fine, will try Hoary shortly.

---

### Post by blastus on 2005-10-10
I must say that [www.writely.com](www.writely.com) is poorly created. Who the hell creates a site these days that uses ActiveX and requires popup blocking to be turned OFF? The "You must disable it (popup blocker) for this site to work properly" message doesn't even register with Firefox. And of course their site cannot be validated with [W3C Markup Validation Service](http://validator.w3.org/). 

But it's probably not directly their fault; that can be blamed on Visual Studio .NET. Still, there's no excuse (except perhaps ignorance) for not designing a website that doesn't follow web standards XHTML, CSS, JavaScript etc... This is one reason why I am against using Microsoft products to create websites or web applications. They are infamous for creating standards-broken, non-interoperable websites that only work with or work best with Internet Explorer.

---

### Post by madjo on 2005-10-10
> ok I was just looking at the source code for both those sites. the only thing I am seeing that is the same is the JS. do you both have java installed on your systems??
JS (javascript) is **not** Java.. both are entirely different, even in make up of the language.

have you both tried to access the sites in different browsers? (epiphany or konqueror or opera?)

---

### Post by Efwis on 2005-10-10
[QUOTE=madjo]JS (javascript) is **not** Java.. both are entirely different, even in make up of the language.

have you both tried to access the sites in different browsers? (epiphany or konqueror or opera?)[/QUOTE]
I know that, but I have found that sometimes Js will not work if you dont' have Java installed. It depends on the person writing the JS. you can incorporate Java into a JS code even though its a seperate language.

---

### Post by fheinsen on 2005-10-10
[QUOTE=Efwis]ok I was just looking at the source code for both those sites. the only thing I am seeing that is the same is the JS. do you both have java installed on your systems??[/QUOTE]
I do have Java installed, but I'll try re-installing it... perhaps I don't have the latest version...?  Let me try.

---

### Post by aysiu on 2005-10-10
[QUOTE=Hairy_Palms]i beleive theres an extension that lets u tell the website that you are running windowsxp even if you arent[/QUOTE] There is. It's called User Agent Switcher, it's right [here](https://addons.mozilla.org/extensions/moreinfo.php?id=59), and it's always worked for me.

---

### Post by fheinsen on 2005-10-10
[quote=madjo]JS (javascript) is **not** Java.. both are entirely different, even in make up of the language.

have you both tried to access the sites in different browsers? (epiphany or konqueror or opera?)[/quote]

Reinstalling Java didn't work.  I had already tried opening the site from a different browser, and that didn't work either.  I will try the "Agent Switcher" extension for Firefox.

---

### Post by fheinsen on 2005-10-10
[QUOTE=aysiu]There is. It's called User Agent Switcher, it's right [here](https://addons.mozilla.org/extensions/moreinfo.php?id=59), and it's always worked for me.[/QUOTE]

The "Agent Switcher" extension for Firefox didn't work either.  

A friend also using Ubuntu just pointed out another (unintentionally humorous) website that doesn't work for him either on Firefox+Hoary: [www.condoflip.com](www.condoflip.com).

Any other suggestions?

---

### Post by weblars on 2005-10-10
Writely.com should work with Firefox. IE and Firefox are the only supported browsers. 
I've tested the site on Hoary/Firefox 1.0.6 a few weeks ago and it worked. Now I'm using Breezy and it still works fine with Firefox 1.0.7 and 1.5 beta 2. 

Can you be more specific about what is happening when you try to access writely (or any of the other sites)?
Do you use the Firefox version from the repositories or directly from mozilla.org?

---

### Post by websavages on 2005-10-10
I had troubles surfing to particular sites which used flash when i had the flash-plugin installed from the universe repository, could this be causing the problem?

Cheers ws

---

### Post by Efwis on 2005-10-10
[QUOTE=websavages]I had troubles surfing to particular sites which used flash when i had the flash-plugin installed from the universe repository, could this be causing the problem?

Cheers ws[/QUOTE]
no.
First off those websites mentioned in this thread don't utilize flash.
Second if flash isn't working properly that is more then likely from a coding status by the web designer. If they set up the flash system to utilize only IE or Windows, which they can do, it will prevent proper use of any flash player on another browser.

---

### Post by websavages on 2005-10-10
Ok, perhaps i was a little premature with my response. If it helps, i have no problems with the mentioned website. I'm running firefox 1.0.7 with the flash (and swf) plugin from macromedia, citrix plugin and pdf plugin from adobe.
Hmm, just noted that I don't have the java plugin.... Let me check my notes

Cheers ws

**** UPDATE ****
I have just installed the java plugin and am still able to view the mentioned sites.

---

### Post by Benchrest on 2005-10-10
I'm running 5.04 and Firefox 1.0.7 and can access all three sites fine. I don't have anything special installed. Do you have any extensions installed?

---

### Post by jpmontalbo on 2005-10-10
Hello everyone. I just verified that it is flash that's causing firefox 1.07 to crash or hang. Everytime I tried to access some sites, it would crash and give me this message ===>
```
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadShmSeg (invalid shared segment parameter)'.
  (Details: serial 61 error_code 163 request_code 147 minor_code 2)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

I experimented and uninstalled libflash-mozplugin through synaptic and then installed flashplayer-mozilla from synaptic as well. Now I try to access sites and works just fine. Hopefully that helps some of you guys :p . By the way I'm current running breezy 5.10 rc version, Firefox 1.07.

Here's my sources.list just in case.
```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release Candidate i386 (20051005)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu breezy universe
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

##Backports
deb http://ubuntu-backports.mirrormax.net/ breezy-backports-staging main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-extras-staging main restricted universe multiverse

```

---

### Post by joshuapurcell on 2005-10-11
I'm glad I found this thread. I thought I was the only one who was having problems with Firefox working on certain websites. One website that I get alot of grief from my wife about because it doesn't work is [www.studentdoctor.com](www.studentdoctor.com), and this has happened on both 32-bit and 64-bit Hoary running Firefox. She can go to the site and surf around for a while, but randomly the browser will hang and the entire computer will not respond to anything except for a hard reboot. This only happens on the above website and a couple of others, and only while in the process of scrolling.

Since I've installed Opera I haven't had any of those problems (only other problems related to lack of plug-ins).

---

### Post by aysiu on 2005-10-11
I know this doesn't help, but [I'm able to access Writely.com just fine](http://i22.photobucket.com/albums/b337/psychocats/4254c021.png). I'm using Firefox 1.0.7 on Kubuntu Breezy.

---

### Post by barus243 on 2005-10-11
Well guys you arent the only ones having problems.  Mine wont access Google of all things, and that my friends sucks.  I tried some of those sites you had posted as well, and well they don't work either.  I have tried Lynx, Mozilla, and Firefox, and well none of them work.  What's up with this?  If any of you guys figure this one out, that would be great.  I'm working on it to, so If I figure it out, I'll post.  Good luck

---

### Post by Wide on 2005-10-11
I had the same problem on Sourceforge.net

I reboot cleared it right up

Drove me crazy trying to figure it out, never did find the cause :confused:

---

### Post by barus243 on 2005-10-11
Ok guys, I have narrowed this problem down I think.  I am almost one hundred percent confident it IS Javascript related, but I can't figure out what the hangup is.  I went to [www.ubuntuguide.org](www.ubuntuguide.org), which would not load the whole page.  It loaded the page until the point it hade to load the Google search box, which is programmed in, you guessed it, Javascript.  I dont know what the crap is up with the JS but I'm workin on it.

---

### Post by barus243 on 2005-10-11
Ok, now I am 100% confident is the freakin java script.  I saved a page, edited the source, removing Javascipt, resaved the page and it works fine.  I hate Javascript. Also I just tested another theory, I decided to try the live CD of Ubuntu and [www.google.com](www.google.com) worked and [www.writely.com](www.writely.com) both worked...So now the question is what has been changed since the last install.  I was cleaning house on my system yesterday and I decided to do a fresh install of 5.04 and the only things that I have put on there are the updates.  I'm trying to figure out if this could possibly be somewhere in the updates. Good luck to everybody on this one.

---

### Post by fheinsen on 2005-10-11
[quote=weblars]Writely.com should work with Firefox. IE and Firefox are the only supported browsers.[/quote] 

I agree, it *should* work, but... it doesn't :-(

[quote=weblars]Can you be more specific about what is happening when you try to access writely (or any of the other sites)?[/quote]

The status bar indicates "Looking up writely.com..." and stays like that for a long while.  Note that I can access writely.com from Windows PCs on the same LAN, and I can open the terminal and ping writely.com just fine from my Ubuntu Hoary box, so this is a Firefox problem.

[quote=weblars] Do you use the Firefox version from the repositories or directly from mozilla.org?[/quote]

From the repositories.  Here's a copy of my /etc/apt/sources.list file:
```

deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

```

Any suggestions?

---

### Post by fheinsen on 2005-10-11
*** SOLVED *** 

Here's the quick fix:
1. Open a terminal and type "sudo gedit /etc/firestarter/non-routables"
2. Remove the line "72.0.0.0/8" and save the file.
3. Restart Firestarter (i.e., File -> Quit, then start again from the Applications menu).

Here's the how I got there:
After trying a bunch of different things, I discovered that temporarily disabling the firewall solved the problem. Digging a bit deeper, I found that whenever I tried to access writely.com I got the following message: "Oct 11 09:30:23 Source: writely.com Destination: 192.168.1.5 In IF: eth0 Out IF: Port: 32800 Length: 44 ToS: 0x00 Protocol: TCP Service: Sun-RPC portmap." Digging further, I found that this was due to **a bug in the version of Firestarter which is currently stored in the Ubuntu 5.04 repositories**.  Here is where I found the solution: [http://article.gmane.org/gmane.comp.security.firewalls.firestarter.user/326](http://article.gmane.org/gmane.comp.security.firewalls.firestarter.user/326)

Thanks to everyone who lent a hand.

---

### Post by barus243 on 2005-10-11
Thanks...working on Firestarter proved to fix the problem. I thought for sure it was in the Java Script, I never thought about looking there for the problem.

---

### Post by fheinsen on 2005-10-12
[quote=barus243]Thanks...working on Firestarter proved to fix the problem. I thought for sure it was in the Java Script, I never thought about looking there for the problem.[/quote]

My pleasure.  Thank *you* for lending a hand. :-)

---

### Post by Hairy_Palms on 2005-10-12
wow that worked like a dream! thanx a lot :D

---

### Post by fheinsen on 2005-10-12
[quote=Hairy_Palms]wow that worked like a dream! thanx a lot :D[/quote]
Happy to hear that.  Thank ***you*** too -- we all solved it together.  Reading other people's suggestions and ideas ultimately led me to the right solution.

The Ubuntu community is just awesome, isn't it?  I find these forums to be as good or better at providing technical support than the paid support I've gotten in the past from many commercial software vendors.  I mean, it's not just that the people here are friendlier; it's also that in the aggregate they are  vastly more knowledgeable than any low-wage customer service rep on a toll-free line could ever be.

---

