---
title: "Typing in Wordpress extremely slow in Firefox"
date: 2009-05-04
forum: General Help
---

### Post by bhagwad on 2009-05-04
I'm having a problem where any typing in certain types of text editors is extremely slow. Example is Wordpress where if I press the "Backspace" key, it takes several seconds for the text to be deleted - one by one, long after I have released the key. There is also a delay between pressing the key and the character appearing on the screen.

The same problem to a little lesser degree occurs on the Twitter web site.

It renders the wordpress text editor completely unusable for me, and the *only* thing that works is to go the the HTML view - where I don't face any problems either typing, or deleting.

Here are my system Specs:

Ubuntu 9.04 32 bit
Sony VAIO VGN-NR498E
3 GB RAM, Dual Core 2.0 Ghz
Firefox 3.0.10
Intel 965 Graphics chip

I have also started Firefox in Safe Mode with all plugins disabled, and the problem is the same.

When I use a different browser like Opera, the problem vanishes and I can edit and delete very fast. But I need the plug ins in Firefox :( as I'm a writer and have several add ons that are critical to my work...

Once again, when I go to the HTML mode in Wordpress, I face no problems. I feel this should be a big hint in solving it, but don't know what the issue is...

I really hope someone here can help me out.

Bhagwad

---

### Post by BslBryan on 2009-05-04
It could be a cache problem.

Try Tools --> Clear Private Data 

Good luck. :)

---

### Post by bhagwad on 2009-05-04
> **BslBryan said:**
> It could be a cache problem.

Try Tools --> Clear Private Data 

Good luck. :)

Just tried clearing the cache - no luck :( .

---

### Post by BslBryan on 2009-05-04
Hmmm...   Well, try clearing all private data.  If that doesn't work, go into CSS and change the CSS value ```
position: relative
``` to ```
position: absolute
```.

If that doesn't work, change all CSS values that say ```
width:(number)%
``` to a fixed value i.e. ```
width:(number)px
```.

---

### Post by bhagwad on 2009-05-04
> **BslBryan said:**
> Hmmm...   Well, try clearing all private data.  If that doesn't work, go into CSS and change the CSS value ```
position: relative
``` to ```
position: absolute
```.

If that doesn't work, change all CSS values that say ```
width:(number)%
``` to a fixed value i.e. ```
width:(number)px
```.

I assume you mean style.css in the wordpress settings? I tried that and couldn't fine "position:relative" anywhere.

Also, the width values are all in px, and not percents, so that couldn't be it.

Off the top of my head, could this have anything to do with the Intel 965 graphics drivers which are still blacklisted?

---

### Post by BslBryan on 2009-05-04
I don't know about that...  I mean, it works fine in other browsers, right?

---

### Post by bhagwad on 2009-05-04
> **BslBryan said:**
> I don't know about that...  I mean, it works fine in other browsers, right?

Yes, it works like a charm in Opera. I thought that maybe the Javascript was slowing it down somehow, since even the Twitter texbox is somewhat slow and when I disable Javascript it works great (Twitter updates the no. characters remaining using Javascript I guess).

I tried installing the latest Firefox beta since it's claimed that Javascript is blazingly fast, but it doesn't seem to help. Maybe I should give it another try.

Is no one else facing the issue? Just me?

---

### Post by bhagwad on 2009-05-05
Update: I installed Firefox on wine and this issue doesn't occur! Typing and deleting in Wordpress is as smooth as silk.

I won't be using the wine installation of Firefox since it looks horrible and has some other issues, but this means that the problem is definitely one with the Ubuntu version of Firefox.

Is this a known fact? Windows Firefox = ok, but Ubuntu Firefox = Not so good?

---

### Post by bhagwad on 2009-05-06
@BslBryan

After monkeying around with the CSS in the wp-admin folder for a while, I found that your suggestion indeed works! Changing the "position" tags in "global.css" as you suggested improved the situation vastly.

However, as I'm a writer, I blog on several wordpress blogs and I can't do the same to each of them since I don't always have access.

What could be the reason do you think that Firefox on Linux does such a poor job with performance on CSS pages?

As a workaround, I've found that if I toggle the Wordpress editor to Full Screen mode, it becomes usable again - possibly because there's no "Toggle HTML" tab - just a gut feel.

I really would greatly appreciate insights from anyone as to why this happens. Will it make a difference if I compile my own Firefox?

---

### Post by 50words on 2009-05-06
Just FYI, I am having similar problems in Firefox using a brand-new computer with Windows Vista Ultimate. So I don't think it is an Ubuntu problem.

---

### Post by bhagwad on 2009-05-06
> **50words said:**
> Just FYI, I am having similar problems in Firefox using a brand-new computer with Windows Vista Ultimate. So I don't think it is an Ubuntu problem.

That's strange. Maybe the two aren't related, because I don't have this issue when booting into Vista - I even ran the Windows Firefox in Ubuntu using Wine and it worked great.

I have this suspicion that it may be the video drivers somehow - even though it works fine in Opera. Also, scrolling is a bit jerky in Opera too lending further weight to my suspicions...

---

### Post by bhagwad on 2009-05-08
I just tried using Konquerer, and it works fine - no typing or backspace lag in wordpress.

So I'm guessing it's the fault of the Gecko engine in Ubuntu or Linux since the problem doesn't show in Opera either.

On the other hand, it shows up in Epiphany using Gecko.

Anyone have an idea why Gecko is slow in Linux?

---

### Post by dave31175 on 2009-05-08
I've got the same problem typing in Facebook fields. It's so bad I usually type my comment into gedit, then copy/paste into Facebook.

---

### Post by Endolith on 2009-05-25
Same problem with a fresh Jaunty install.  HTML view is fine, Visual view is slow typing and super slow backspacing.

---

### Post by bhagwad on 2009-05-26
> **Endolith said:**
> Same problem with a fresh Jaunty install.  HTML view is fine, Visual view is slow typing and super slow backspacing.

Ok - so I know I'm not the only person with this problem. Now to diagnose...

What is your configuration? Graphics chip?

---

### Post by Endolith on 2009-05-26
> **bhagwad said:**
> Ok - so I know I'm not the only person with this problem. Now to diagnose...

What is your configuration? Graphics chip?

Dell Inspiron 8600
  nVIDIA GeForce FX Go5200 64M
  15.4" WSXGA+ (1680x1050 widescreen)

Using the nvidia-glx-173  Nvidia drivers.

In WinXP, Wordpress edits fine.  In Jaunty, it's super slow.

---

### Post by bhagwad on 2009-05-26
Ok. So not a hardware issue like I thought it may be.

If you edit wordpress in full screen mode (Alt+Shift+G) does the problem become much better? Also, were you using Hardy before Jaunty (Or any other Ubuntu)? Was the problem there in that too?

---

### Post by Endolith on 2009-05-26
> **bhagwad said:**
> If you edit wordpress in full screen mode (Alt+Shift+G) does the problem become much better?

I'll check later.  I have Compiz disabled, by the way.

> Also, were you using Hardy before Jaunty (Or any other Ubuntu)? Was the problem there in that too?

I was using Intrepid, and I don't remember this being a problem.  I still have that install on the disk (just upgraded), so I can try that later too. :)

---

### Post by bhagwad on 2009-05-26
Great. This will help us know if the issue is with Ubuntu, or with Firefox in Ubuntu.

When you test intrepid, will you use the same Firefox version that you're using now?

---

### Post by Endolith on 2009-05-26
Firefox 3.0.10 in both:

In Jaunty, typing is relatively normal now, but backspace is super slow.  The CPU maxes out while I'm trying to backspace.  Full screen doesn't change anything.

In Intrepid, it's working ok.  The letters are appearing as I type them, and the backspace works quickly.  There are lock-ups every few seconds, but that affects everything, and is one of the reasons why I did a fresh install of Jaunty.  :)

---

### Post by bhagwad on 2009-05-26
> **Endolith said:**
> Firefox 3.0.10 in both:

In Jaunty, typing is relatively normal now, but backspace is super slow.  The CPU maxes out while I'm trying to backspace.  Full screen doesn't change anything.


Just to check, you're using Fullscreen in the Wordpress editor tab and not Firefox itself right? (Screenshot attached).

Will need to revise my theory that it's the CSS engine in Firefox that's the culprit if what you're saying is correct....

---

### Post by Endolith on 2009-05-26
> **bhagwad said:**
> Just to check, you're using Fullscreen in the Wordpress editor tab and not Firefox itself right? (Screenshot attached).

Will need to revise my theory that it's the CSS engine in Firefox that's the culprit if what you're saying is correct....

No I was running Firefox in full-screen mode.  You're right, Wordpress works a lot better when it's in full screen.  Thanks for the workaround :)

---

### Post by bhagwad on 2009-05-26
Ok great.

I think the problem is with CSS rendering. When in full screen mode, the sidebars are not being rendered and so the problem doesn't exist.

Since you say that this wasn't a problem in Intrepid, it *must* be in Ubuntu Jaunty itself. But Opera seems to work fine....

It's very confusing. I wish there were clear answers to this. Scrolling is also very slow on complex pages.

Basic question: Firefox issue or Jaunty issue. If it's a Firefox problem, then Firefox on Intrepid should also work poorly.

If a Jaunty issue, then why is Opera working fine?

---

### Post by Endolith on 2009-05-26
Just tried with a clean profile and it happens there, too.  It seems like there are always problems like this with every Ubuntu release.  Scrolling suddenly gets very slow, typing gets very slow.  It's always something.

---

### Post by 0Sully on 2009-06-12
I am having a similar issue.  Slow, jerky scrolling, very slow backspacing.  I was also having issues with video and flash rendering but after using a fix most of that has gone away.  This remains an issue tho.

That fix is here:  [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

I am running a Dell Inspiron 500m with the intel 855G graphics card and a 1.3GHz processor with 1 GB ram.

---

### Post by bhagwad on 2009-06-12
> **0Sully said:**
> I am having a similar issue.  Slow, jerky scrolling, very slow backspacing.  I was also having issues with video and flash rendering but after using a fix most of that has gone away.  This remains an issue tho.

That fix is here:  [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

I am running a Dell Inspiron 500m with the intel 855G graphics card and a 1.3GHz processor with 1 GB ram.

I had tried this patch some time ago, but it *didn't* fix the typing and backspace problems.

When you say " This remains an issue tho", are you saying that the typing/backspacing problem persists?

---

### Post by regebro on 2009-06-13
Just here to say I also have this issue, and that Firefox also is very slow in Gmail, not only typing, but scrolling, especially if I have the Todo-list on.

Very annoying. I'm currently running gmail in Chrome to go around that issue.

---

### Post by bhagwad on 2009-06-14
> **regebro said:**
> Just here to say I also have this issue, and that Firefox also is very slow in Gmail, not only typing, but scrolling, especially if I have the Todo-list on.

Very annoying. I'm currently running gmail in Chrome to go around that issue.

Are you using Windows with Chrome? The problem I've mentioned is only with Ubuntu. But maybe there are some linkages...

---

### Post by josaphat on 2009-06-27
I've seen this problem in forums all over the place. People complaining that facebook is terribly slow with typing/scrolling.
First let me say that I'm glad *this* community (at least) isn't automatically recommending new machines or keyboards. :)

Now, since most of the folks I've seen in various forums who say they have this problem aren't using Ubuntu, I very seriously doubt that the problem is in the Operating System.
What has thus far worked for me has been disabling some of those applications that I never use on Facebook (i.e. those stupid quizzes). I read a suggestion to clear the Firefox Cache, so you can try doing that also. Don't know if it will work with Wordpress.
I think it would be safe to pass on the blame to the Facebook developers because I seriously doubt that its a Firefox issue.

---

### Post by bhagwad on 2009-06-27
> **josaphat said:**
> I've seen this problem in forums all over the place. People complaining that facebook is terribly slow with typing/scrolling.
First let me say that I'm glad *this* community (at least) isn't automatically recommending new machines or keyboards. :)

Now, since most of the folks I've seen in various forums who say they have this problem aren't using Ubuntu, I very seriously doubt that the problem is in the Operating System.
What has thus far worked for me has been disabling some of those applications that I never use on Facebook (i.e. those stupid quizzes). I read a suggestion to clear the Firefox Cache, so you can try doing that also. Don't know if it will work with Wordpress.
I think it would be safe to pass on the blame to the Facebook developers because I seriously doubt that its a Firefox issue.

Well, I'm sure the problem is *either* Ubuntu or Firefox on Ubuntu or a bit of both. This is because:

1. On the *same* hardware, the typing is perfectly fine in Windows Vista but not in Ubuntu
2. Typing in *Opera* is perfectly fine on Ubuntu on the same sites where Firefox is unacceptably slow.

When typing is slow in Windows, it *might* be a different problem. So see how bad it is in  Firefox on Ubuntu, you can see an uploaded video of the delay on this Bug report comment: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/368242/comments/5](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/368242/comments/5)

---

### Post by secondstage on 2009-06-27
I'm just going to put my two cents of experience/knowledge into this conversation.

On Facebook, using almost any text input, or textarea is putting quite a load on the CPU. It has gotten to the point where typing will cease for 3-5 seconds, and then all the text appears in a burst, as if Firefox is getting the input, but Facebook's scripting or whatever is just holding up the processing. 

I do web development, and have noticed that with any other text input, or textarea, the speed is perfectly fine, and the CPU load is nearly nothing. I have not read all of these posts, but I'm saying that it has something to do with the JavaScripting, and possibly Firefox waiting for Facebook (or any site) to be done with whatever it does before Firefox does what it does.

My system specifications are as follows:
Intel Core 2 Duo E6550 2.3GHz
2 GB of PC6400 RAM 800Mhz
Nvidia 9400GT video processor.
Compiz is enabled, with cube, and 6 desktops.
Ubuntu Studio 9.04 (up to date with packages)
Firefox 3.0.11

---

### Post by Endolith on 2009-06-27
> **josaphat said:**
> Now, since most of the folks I've seen in various forums who say they have this problem aren't using Ubuntu, I very seriously doubt that the problem is in the Operating System.

Then why would it be a problem in Ubuntu but not Windows XP on the same machine?  It's obviously a problem with the operating system.

> What has thus far worked for me has been disabling some of those applications that I never use on Facebook (i.e. those stupid quizzes).That's not a solution.  That's just avoiding things that are affected by the bug.

> I think it would be safe to pass on the blame to the Facebook developers because I seriously doubt that its a Firefox issue.Facebook wrote Wordpress?

---

### Post by Xarijus on 2009-07-05
Good day.

I just want to confirm, that problem exists on  Linux Mint 7 (which is based on Ubuntu).
Writing in wordpress is extremely slow using firefox 3.0.11.
Writing with wordpress text editor in full screen mode DOES help a bit, but the speed of typing is not as same as in OpenOffice for example.

My PC CAN handle wordpress:
Intel Core 2 Duo 2.0 Ghz;
2 Gigs of RAM;
Intel GM965/GL960.

---

### Post by kufeiko on 2009-07-11
Hi,

I can confirm the issue: Firefox (3.0.11) is slow in typing in some JS/AJAX textareas. I don't have the possibility to test it under Wordpress. 

I'm with Xubuntu 9.04 on MSI Wind U100 (Intel Atom @ 1,6GHz). Didn't noticed that typing problem when I was on 8.04 and 8.10.

But here's another test: I started VirtualBox machine on top of Jaunty with WinXP installed and there was no problem with typing in Firefox. So I guess it is FF+Jaunty issue.

---

### Post by JohnLau on 2009-07-11
I think this problem might be related to to the kernel.
Have you tried [installing the newer 2.6.30 kernel]("http://compustorm.no-ip.org/2009/07/boost-ubuntu-performance-by-installing-2-6-30-kernel/") and see if it works? 
John

---

### Post by bhagwad on 2009-07-14
> **JohnLau said:**
> I think this problem might be related to to the kernel.
Have you tried [installing the newer 2.6.30 kernel]("http://compustorm.no-ip.org/2009/07/boost-ubuntu-performance-by-installing-2-6-30-kernel/") and see if it works? 
John

I upgraded the Kernel a while back and found the same problem :(

---

### Post by jimmykicker on 2009-08-06
Issues with Firefox and slow text input has brought me here as well.  This is what I found.  Epiphany and Firefox both have the same issue.  As another user pointed out is that he used the windows version under wine.  That works fine for me as well.  Also Konquerer works without a hitch.:D

This laptop is a P3 with 1.3 Ghz single processor, and dual boots XP and Ubuntu.  None of the issue with Firefox are present while running Windows (miracle I know).

So what gives?:(

---

### Post by zooklaw on 2009-09-17
It seems people are having trouble tracking down the root of the slow typing/backspace/scrolling problem while using Firefox in Ubuntu.  

This issue was driving me crazy.  Note, I wrote "was"!

It seemed that my computer would slow down to a crawl in any website that had message boxes.  I would make typos due to the slow response of the keyboard.  The delete key was a nightmare; it would lock up the browser.

I saw the links to various fixes that came with multiple warnings.  I did not try any of the fixes because they looked complicated and few people seemed to have clear success with the fixes.

I instead downloaded google's Chrome 64 browser for Linux.  It is the "unstable" development version and it works like a charm.  It is fast, fast, fast. Scrolling is smooth without a glitch.

Now I can type!  I can even use the backspace key to delete as fast as I desire.

Some features are not available in the release of Chrome at this time but at least it works for typing.

Good luck!

---

### Post by Endolith on 2009-09-17
Telling people to switch to Chrome as a "solution" is like telling them to switch to Windows.

...then again, if you run Firefox in Wine I bet it doesn't have this problem.  It's probably [faster, too]("http://www.tuxradar.com/content/browser-benchmarks-2-even-wine-beats-linux-firefox").

---

### Post by bhagwad on 2009-09-17
> **zooklaw said:**
> 

I instead downloaded google's Chrome 64 browser for Linux.  It is the "unstable" development version and it works like a charm.  It is fast, fast, fast. Scrolling is smooth without a glitch.

I agree that Chromium doesn't have this problem and I'm sure it'll be a very viable option for power users soon. But till that time, we still need to figure out why this problem is plaguing Firefox in Ubuntu.

Hopefully Karmic Koala will not have this issue...

---

### Post by carlos123 on 2009-09-18
I don't know if the problem is just with Firefox or not (it seems to be) but if it is...Firefox better fix what is wrong and quick or it will lose market share big time to the up and coming Google Chrome.  I am starting to use Chromium myself on Linux for this or that and as it improves I will probably use it even more to get around these irratating quirks that I experience in Firefox.  

Not that I expect Firefox to fix anything.  I mean goodness gracious.  It's a free browser!  

Just saying that it will start losing market share if it doesn't fix these sorts of things and quickly.  Assuming it is a Firefox problem.  

Carlos

---

### Post by RedRat on 2009-09-18
I will add my two cents worth here. I blog on the Washington Post under the "Comments" section. I too found that typing there was infernally slow! So I just gave up on typing my stuff into their comment box and instead write it all up in gedit and then cut and paste it into the box, then hit send. It is annoying. I have not tried Opera on the box yet, I will give it a try perhaps next week.

---

### Post by relay_man on 2009-09-18
This problem has become common lately.

I believe this will help.
Look here:

[http://kb.mozillazine.org/Reducing_memory_usage_(Firefox](http://kb.mozillazine.org/Reducing_memory_usage_(Firefox))


and here:

[http://kb.mozillazine.org/Standard_diagnostic_(Firefox](http://kb.mozillazine.org/Standard_diagnostic_(Firefox))

---

### Post by bhagwad on 2009-09-18
> **relay_man said:**
> This problem has become common lately.

I believe this will help.
Look here:

[http://kb.mozillazine.org/Reducing_memory_usage_(Firefox]("http://kb.mozillazine.org/Reducing_memory_usage_%28Firefox"))


and here:

[http://kb.mozillazine.org/Standard_diagnostic_(Firefox]("http://kb.mozillazine.org/Standard_diagnostic_%28Firefox"))

I'm fairly sure this particular problem isn't related to the usual Firefox problems (plugins, themes, install etc.) I've tried all the usual options and nothing helps.

Also, as someone has earlier noted on this thread, the problem occurs with another browser as well (konquerer I think) - my personal suspicion is that it's got something to do with the Gecko rendering engine.

---

### Post by bhagwad on 2009-10-19
I'm eagerly awaiting the release of Karmic Koala which has improved support for Intel Graphic chipsets. Let's see if that solves the problem. I certainly hope so!

I'm sanguine because the typing problem didn't seem to manifest itself with Ubuntu versions such as Hardy Heron.

Fingers crossed...

---

### Post by Endolith on 2009-10-19
> **bhagwad said:**
> I'm eagerly awaiting the release of Karmic Koala which has improved support for Intel Graphic chipsets. Let's see if that solves the problem. I certainly hope so!

I'm sanguine because the typing problem didn't seem to manifest itself with Ubuntu versions such as Hardy Heron.

Fingers crossed...

I have the problem but I do not have Intel Graphics.

Karmic may fix the problem, but it will invariably introduce new problems, too, just like Jaunty introduced this one.

---

### Post by bhagwad on 2009-10-28
I've just been testing the release candidate for Karmic and the problem seems to have improved. The backspacing is nowhere near as slow as it was in Jaunty.

But there is <em>still</em> a delay without a doubt. If I keep the backspace pressed continuously for a say 2 seconds, I find that I can let go and still have the characters disappearing. But people won't need to do that frequently.

So problem still not solved but much better nonetheless.

---

### Post by bhagwad on 2010-03-28
I can finally confirm that this is SOLVED in Lucid Lynx 10.04! I'm using the beta and the typing and backspacing in Wordpress in Firefox is as smooth as it gets.

Good job canonical. At least now we know that the issue was the OS and not Firefox.

---

