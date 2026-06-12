---
title: "firefox overloading cpu"
date: 2005-06-27
forum: Desktop Environments
---

### Post by nephish on 2005-06-27
Has anybody any clue why firefox spikes my cpu to 100% ?
it isn't on every page. i think its just pages with flash. sometimes while it loads
a page it spikes the cpu to 100% until i get off that page. 
i have a 900mhz athlon with 187 mb of RAM. i would think that its ok for a ubuntu system, and usually is. (uptime over a week usually) but..... any idea how i can fix this? 
thanks.

---

### Post by jobo on 2005-06-27
[QUOTE=nephish]Has anybody any clue why firefox spikes my cpu to 100% ?
it isn't on every page. i think its just pages with flash. sometimes while it loads
a page it spikes the cpu to 100% until i get off that page. 
i have a 900mhz athlon with 187 mb of RAM. i would think that its ok for a ubuntu system, and usually is. (uptime over a week usually) but..... any idea how i can fix this? 
thanks.[/QUOTE]
 Have you installed flash-plugin(s)?

---

### Post by nephish on 2005-06-27
yeah, from the macromedia as per the wiki here. 
flash works, but over works.
i did not install from an Ubuntu .deb package, i installed by download,
untar, run the setup script....

any ideas?

---

### Post by fishfork on 2005-06-28
Some flash pages can be very CPU intensive. One solution is to install [flashblock](https://addons.mozilla.org/extensions/moreinfo.php?id=433). This stops flash animations from loading until you click on them. Very handy unless you have a particular fondness for animated, noisy flash adverts  :)

---

### Post by rwabel on 2005-07-01
firefox is in my opinion very very memory hungry. I'm using session saver and in average I've about 10 over 15 pages open. I do have seldom cpu problems. They are really mostly related with flash. Same is for opera. 
Who the f**** needs flash!!!  :grin: 

In general I found out that I get in memory problem with all applications based on or using mozilla. It's a shame that they don't try to reduce the memory usage!!!

I can use opera with tones of webpages open during days. But with firefox after a while it crashes when I've too many pages open.

---

### Post by rdw200169 on 2007-12-25
I installed 'flashblock' and that did it!  The CPU usage by firefox plummeted from and average of 12-20% to 2-5% idle.  I generally keep 8-20 tabs open, and I guess one of them (or more) are constantly running flash animation and running my computer to death.  I imagined that firefox paused the animation, but I guess not!

---

### Post by John Hughes on 2007-12-25
Flash Tends to be intensive..... For some reason on Linux even more so then on windows.... I think the flash plugins in general seem less efficient on Linux then they should be. Firefox/Mozilla does have memory leaks as well but They try to work on that regularly.... There is Firefox 3 coming out soon so hopefully that fixes some of the memory holes....

Another thing to remember is that some webpages are poorly written and tend to throttle your internet connection slowing it down to a laggy mess and falling back on your cpu and making everything seem sluggish *cough* myspace *cough*  Alot of user pages on myspace and things like it tend to be laggy because people load them up with junk. Lotsa flash stuff etc.. 

An observation as well... While that computer is ok to run Ubuntu keep in mind it may not run it really well....  System Requirements

The minimum memory requirement for Ubuntu 7.10 is 384MB of memory for desktop CDs, and 256MB for other installation methods. (Note that some of your system's memory may be unavailable due to being used for the graphics card.)

With only the minimum amount of memory available, the installation process will take longer than normal, but will complete successfully, and the system will perform adequately once installed. Low-memory systems may be able to use the desktop CD to install by adding the only-ubiquity boot option to run just the installer rather than the whole desktop. 

Older versions may take less resources but stilll your memory is pretty low even for Ubuntu.... I'd reccomend at least 256 (512 if you can get it would be even better) of the highest ram your computer can handle... The processor is Ok but not grand. Again while the computer may run stuff it will in all likely-hood not run them as effectively as it could if it had more resources to pull...

---

### Post by bharadwaj on 2007-12-25
> **rwabel said:**
> firefox is in my opinion very very memory hungry. I'm using session saver and in average I've about 10 over 15 pages open. I do have seldom cpu problems. They are really mostly related with flash. Same is for opera. 
Who the f**** needs flash!!!  :grin: 

In general I found out that I get in memory problem with all applications based on or using mozilla. It's a shame that they don't try to reduce the memory usage!!!

I can use opera with tones of webpages open during days. But with firefox after a while it crashes when I've too many pages open.
yes i do agree with that i found the same problem while using songbird too.. mozilla must suerly come up with an answer to fight back its rivals :|

---

### Post by jeffus_il on 2007-12-25
Great to hear that you are running Ubuntu on an old slow machine,
it's good for the environment,
good for Ubuntu,
good for your pocket,
and bad for Uncle Bill

---

### Post by alecz20 on 2008-03-15
Please also not that System monitor in Ubutnu may also be buggy. Therefore I suggest using the gadget for monitoring the CPU load (and other things if you want)

I did this and I noticed that watching movies on youtube.com causes one of the two CPU's to go to 100%. While this is not a big problem for my case it is a problem nevertheless.

for example check this link: [http://youtube.com/watch?v=k6bRpsqr7D0](http://youtube.com/watch?v=k6bRpsqr7D0)
and notice that if you pause the movie, the CPU load will go to normal.

I haven't tested this on windows with Maxthon, but I doubt it occurs.

---

### Post by Aidin Sabetian on 2008-03-15
Check and see if you have installed firefox addons, extensions or plugins. Many of these addons are buggy and tend to eat up memory and cpu.

Try using gnash instead of flash. Uninstall flash then install gnash (gnu's open-source alternative to the macromedia flash player) instead. I watch youtube movies and browse flash sites with gnash.

---

### Post by Lantesh on 2008-03-16
> **fishfork said:**
> Some flash pages can be very CPU intensive. One solution is to install [flashblock](https://addons.mozilla.org/extensions/moreinfo.php?id=433). This stops flash animations from loading until you click on them. Very handy unless you have a particular fondness for animated, noisy flash adverts  :)

Hey thanks for the Flashblock tip.  I was having the same problem, and this did the trick.  I didn't even know that Flash was the problem until I read this thead, and realized I had the same identical symptoms.

---

### Post by najames on 2008-04-14
I have been using Mint Daryna (Gutsy) for some time and Firefox plssed me off so much that I quit using it.  CPU usage was linear with the number of tabs open, about 4-5 tabs would drive the CPU at 30%, temps would go from 30C up to 36C with 5 tabs every time.  As I closed tabs I could watch temps drop on my LCD temp display on my case.  Opera does not do this, I can have 10-15 tabs open and if I run the top command it is never in the top 3 listed, usually trackerd is the #1 CPU usage.  Opera has NO affect on CPU temps.

With Mint, Google is using some sort of high jacked "custom" Mint search page with ads.  I removed Google and other search engine crap I don't use, switched to a Yahoo search engine last night and now the Firefox CPU usage is running 6-9% in top, a LOT better than 30% plus Google was causing, temps are constant 32.5C now.  All this time I have been cursing Firefox, but it looks like our "friends" at Google were doing it.

Oops, opening tab 6 and FF was running at 20% for several minutes but is finally dropping back now, maybe it is not all Google's fault.  I give up.

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6535 homer    15   0  286m 103m  26m R   13  5.8   8:55.66 firefox-bin        
 6585 homer    15   0  139m  40m  26m S    2  2.3   2:16.87 amarokapp          
 5076 root        15   0  378m  80m  20m S    1  4.5   3:48.63 Xorg

---

