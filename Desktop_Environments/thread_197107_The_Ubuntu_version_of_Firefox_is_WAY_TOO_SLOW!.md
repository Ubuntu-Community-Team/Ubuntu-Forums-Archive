---
title: "The Ubuntu version of Firefox is WAY TOO SLOW!"
date: 2006-06-15
forum: Desktop Environments
---

### Post by Farenji on 2006-06-15
Why is it that the Ubuntu version of firefox is so very slow compared to the standard mozilla firefox version? I haven't timed it but it looks like the ubuntu version takes 2-3 times as long to render a big page and that is *very* noticeable on slower systems. On big pages with a lot of javascript, the ubuntu version is unresponsive for a very long time while loading. The default version does not have this problem, or in a much lesser extent.

What exactly is the difference between the ubuntu and standard version? Why even bother to make a different custom version?? The default version works perfect and fast with no tweaking needed, and it works and looks the same.... Firefox is (one of) the most important and most used apps on the desktop. I personally think the devvers should do everything to make it work as fast & smooth as possible...

---

### Post by codypumper on 2006-06-15
The custom version is designed to work on ANY computer, and its not really that hard to tweak it once a year, is it?

---

### Post by FredB on 2006-06-15
> **Farenji]Why is it that the Ubuntu version of firefox is so very slow compared to the standard mozilla firefox version? I haven't timed it but it looks like the ubuntu version takes 2-3 times as long to render a big page and that is *very* noticeable on slower systems. On big pages with a lot of javascript, the ubuntu version is unresponsive for a very long time while loading. The default version does not have this problem, or in a much lesser extent.[/quote]

I did not see such slowing down between the two versions. And optimization line is nearly the same. So, did you have any statistics to make your words clearer ?  said:**
> What exactly is the difference between the ubuntu and standard version? Why even bother to make a different custom version?? The default version works perfect and fast with no tweaking needed, and it works and looks the same.... Firefox is (one of) the most important and most used apps on the desktop. I personally think the devvers should do everything to make it work as fast & smooth as possible...

What's your computer hardware ? Maybe there is the explanation though ;)

---

### Post by Hairy_Palms on 2006-06-15
i found this too, 6-7 seconds to load google is unacceptable, i installed swiftfox and it made everything better still quite slow but 2 seconds is acceptable

---

### Post by FredB on 2006-06-15
6 to 7 seconds ? This is not very low. It depends on your bandwith too. With my 8 Mbits/s line, with a -Os -march=pentium4 minefield (pre-pre-3.0alpha), I got google in about 4 seconds or so.

---

### Post by Eversmann on 2006-06-15
Maybe your problem isn't firefox, could be a network issue with dapper.

Check this out: [http://ubuntuforums.org/showthread.php?t=87798&highlight=disable+ipv6](http://ubuntuforums.org/showthread.php?t=87798&highlight=disable+ipv6)

Also, type this address at firefox: about:config

and on filter use: ipv6. At network.dns.disableIPv6 make a double click and set it to "True". Reopen firefox and try it out.

(I think with just tweaking firefox you'll see an speed improvement).

Reply if its useful so other people can solve their problems about this too ;-)

regards.

---

### Post by gamma on 2006-06-16
Yea disable ipv6, that's probably your bottleneck. For some reason it trys to resolve to ipv6 first instead of ipv4 I've heard. I tried the official binary and there isn't any speed difference here...

---

### Post by chrsjav on 2006-06-16
Try the latest alpha of Firefox 2 (Bon Echo alpha 3 I think).  It's mostly stable and noticeably faster.  You can use Nightly tester tools to force your extensions to work, if you like.

---

### Post by FredB on 2006-06-16
Using an alpha is not really a good idea for a standard user.

As a **completely mad tester** I am using Minefield (aka pre-pre-alpha version of Firefox 3.0) and sometimes it is exploding ;)

---

### Post by mystdragon on 2006-07-22
Is it Firefox or X, or some interaction of the two?  I've found that scrolling a window up and down in recent firefox builds causes X to use up to 100% of the CPU.  I've seen this on both Debian and Ubuntu.  It would cause audio playback to become choppy, make the computer slow, etc.  However, using older builds of Firefox or Mozilla fixed the problem.

Try running top and see what happens.

---

### Post by hellmet on 2006-07-22
i dislike firefox sometimes for the reason that it hogs too much 
memory..and recently it shut down completely without a hint
two three times..thank god i was not on important work!!
i think i'd have to switch to some stabler browser..
any idea ppl??

---

### Post by DoktorSeven on 2006-07-22
The default Ubuntu Firefox I have found to be pretty slow, even with ipv6 completely disabled and using a lightweight desktop (Flux).  Fortunately, compiling my own Firefox gave me a faster browser.

---

### Post by JoWilly on 2006-07-22
The ubuntu firefox is slower than the official firefox from mozilla due to the pango support that is compiled in.

There is nothing that can be done about this short of rebuilding it without pango support ... or installing the official version.

---

### Post by styven on 2006-07-22
Hi all,

I use firefox in dapper, 1mb connection, 1ghz amd, 256mb ram, google home page loads in under a second. From google to this forum, just under 3 seconds.

I a not convinced that page loading speed is all down to firefox.

Just my two penneth.

Steve

---

### Post by Dubbayoo on 2006-07-22
Google loaded for me in well under 2 seconds. I have never even thought about the speed but then I have the Fasterfox plugin installed. I can open a new instance of Firefox, which I have set to load 4 sites on startup, in less than 7 seconds.

---

### Post by jISh on 2006-07-22
Why don't you guys just grab Swiftfox?
[http://www.getswiftfox.com](http://www.getswiftfox.com)
You can choose an optimized build for your processor.

---

### Post by Dubbayoo on 2006-07-22
> **jISh said:**
> Why don't you guys just grab Swiftfox?
[http://www.getswiftfox.com](http://www.getswiftfox.com)
You can choose an optimized build for your processor.


Can you run Swiftfox side by side with the default version?

---

### Post by KFASheldon on 2006-07-22
Yep you can run Swiftfox and indeed other Firefox 'clones' along side Firefox

My fav is definatly FLOCK - fast, freindly and super extras, nice bookmarks and RSS intergration as well as fLICKR, Blogs and more.

---

### Post by Matchless on 2006-07-22
Hi,
   I have had the same problem, finding that Firefox would hang for a good while and then suddenly log in to a website. This was caused by the way my nic card was set up. I found that I had my DNS IP's in the order first my gateway, then my two ISP addresses. By swopping them around and putting the gateway last my logging into websites is the same as on Windows. I have proved this on both my dual boot Kubuntu PC's
Remember to reboot after doing this change if required!
Strange, but it works.

---

### Post by hellmet on 2006-07-23
I tried Faster Fox..an extension for FireFox..and it works gr8..

---

### Post by Jhongy on 2006-07-23
Since it prefetches content, are there any issues with FasterFox and administrative or active webpages?

I remember when Google came out with their pre-fetching "accelerator" recently, there were instances of it pre-emptively clicking on things in, for example, e-commerce or hosting control panels.

---

### Post by ericesque on 2006-07-24
One of the first things I do when I install firefox on any computer is get the fasterfox extension.  It makes a world of difference and I've never run into any issues with admin or active webpages.  Just fast as all get out load times. :)

---

### Post by sulobanks on 2006-07-24
If there is any slowness related to the cross-platform bloat of something like firefox, why not try epiphany?  It's GNOME-native and is a gecko browser.

---

### Post by JoWilly on 2006-07-24
> **sulobanks said:**
> If there is any slowness related to the cross-platform bloat of something like firefox, why not try epiphany?  It's GNOME-native and is a gecko browser.

Because it is not compatible with firefox extensions, and the firefox search tool is better.

---

### Post by vamped on 2006-08-19
Linux newb here.

Im running an AMD Duron 1.8 GHz, 1 Gig ram, and my DSL typically provides 100 MB/s.

Firefox is SO slow under Ubuntu Linux, it's as bad as when I had dialup! It's completely unuseable. I'm under windows now just to post this.

I tried a couple of download speed web sites (ie [http://www.neisg.org/Bandwidth/](http://www.neisg.org/Bandwidth/) ) and the download speeds were nearly identical between Windows-Firefox vs Linux-Firefox. Also I downloaded my Ubuntu updates at ~108 KB/s. Yet Linux-Firefox loads pages really slowly (20-30 seconds) vs Windows-Firefox 2-3 seconds.

Whether or not I continue to give Linux a serious try or not depends completely on whether I can fix this issue. Since not everyone is seeing this slowdown, it must be a system dependent bug. I'm going to try installing the regular version of Firefox (as soon as I figure out how to.)

---

### Post by tribaal on 2006-08-19
Did you try the about:config hack? it really changed my linux life...

In firefox's adress bar type "about:config" (without "").
in "filter" type "ipv6"
It leaves only one line, double click it (this sets network.dns.disableIPv6 to "true")
Restart firefox
Enjoy ;)

Most of the PCs I installed linux (and firefox) on had this exact problem, and it was fixed by the above hack.

- trib'

---

### Post by Dubbayoo on 2006-08-19
I don't find Swiftfox to be significantly faster, plus if I use Firefox in between Swiftfox will ask about being the default browser everytime even if i answer no.

---

### Post by gamma on 2006-08-20
If you can live without Firefox's extensions I'd recommened trying Epiphany. It uses the gecko backend so it renders like Firefox 1.5, the only thing is it's better intergrated with Gnome.

---

### Post by holomorph on 2006-08-20
> **hellmet said:**
> i dislike firefox sometimes for the reason that it hogs too much 
memory..and recently it shut down completely without a hint
two three times..thank god i was not on important work!!
i think i'd have to switch to some stabler browser..
any idea ppl??

As for losing stuff in the case of a crash, thank goodness for the Session Manager extension.  If I encounter a page which makes firefox hang or crash, it's no big deal to kill it and then open it again and have all my windows and tabs restored.

---

### Post by vamped on 2006-08-20
> **tribaal said:**
> Did you try the about:config hack? it really changed my linux life...

In firefox's adress bar type "about:config" (without "").
in "filter" type "ipv6"
It leaves only one line, double click it (this sets network.dns.disableIPv6 to "true")
Restart firefox
Enjoy
...
- trib'


Wow! That really sped things up.

Now I don't understand at all what ipv4 or ipv6 is, but does Linux-Firefox not handle ipv6 well? I can't figure out why it makes such a speed difference.

---

### Post by vamped on 2006-08-20
> **gamma said:**
> If you can live without Firefox's extensions I'd recommened trying Epiphany. It uses the gecko backend so it renders like Firefox 1.5, the only thing is it's better intergrated with Gnome.

I can't live without them!

---

