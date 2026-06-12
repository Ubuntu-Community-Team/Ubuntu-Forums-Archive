---
title: "Tracker error in Jaunty"
date: 2009-04-15
forum: General Help
---

### Post by snorbens on 2009-04-15
Hi,
I seem to be having a problem with tracker.

When I boot up, I get the tracker error on the desktop stating that there was an error while performing indexing, and that the index is corrupt.
It gives me the option of re-indexing, cancel and OK.
Whatever I do, nothing appears to happen and the applet will just not disappear.

I uninstalled and reinstalled tracker, and the applet and error message still appear like a bad penny.
However,via the icon on the panel, I clicked on re-index, and although the cpu's have been working at between 95% and 100% for over an hour nothing appears to have been indexed, and the applet error is still there and will not close.

If I hover over the icon on the panel it states:

Tracker: Indexing (by System)

Done: 0 of 0
Estimated: Unknown Time
Elapsed: Less than one second

Any help for this newbie would be welcome.

---

### Post by dunbrokin on 2009-04-15
Don't use tracker....use Beagle...it is much better.

---

### Post by snorbens on 2009-04-15
> **dunbrokin said:**
> Don't use tracker....use Beagle...it is much better.

Thanks will take a look

---

### Post by frdrx on 2009-04-15
Skip Beagle and stick to tracker, which is by far the better choice of the two. I have encountered this error in Jaunty as well, but isn't it the purpose of running Beta software to hunt for bugs?

---

### Post by snorbens on 2009-04-15
> **frdrx said:**
> Skip Beagle and stick to tracker, which is by far the better choice of the two. I have encountered this error in Jaunty as well, but isn't it the purpose of running Beta software to hunt for bugs?

Of course you are 100% right about beta...just thought that someone may have found a fix.

Thanks for your input

---

### Post by frdrx on 2009-04-15
> **snorbens said:**
> Of course you are 100% right about beta...just thought that someone may have found a fix.

Thanks for your input

That's why I'm here as well. This problem has occurred on two of my machines after yesterday's upgrade. I'm browsing through launchpad at the moment to see if there's any relevant and hopefully useful information.

---

### Post by metalsand on 2009-04-15
Same here. I expected this to already be reported and fixed alas this is the only relevant thing google turns up.

Bug must not have that wide of infection among the Ubuntu populus...

---

### Post by snorbens on 2009-04-15
> **metalsand said:**
> Same here. I expected this to already be reported and fixed alas this is the only relevant thing google turns up.

Bug must not have that wide of infection among the Ubuntu populus...

Maybe it will be fixed for the main event in a few days time.

We can hope.

---

### Post by louleib on 2009-04-15
I am having the same problem with Tracker, corrupt index. Does anyone know if bug report has been submitted? Actually I will check for now. Any help  in this area will be appreciated.

Lou

---

### Post by frdrx on 2009-04-15
> **louleib said:**
> I am having the same problem with Tracker, corrupt index. Does anyone know if bug report has been submitted? Actually I will check for now. Any help  in this area will be appreciated.

Lou

It might have been filed [here]("https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361205"). So far I'm happy with the workaround posted one hour ago by Hector Louzao.

---

### Post by metalsand on 2009-04-15
> **snorbens said:**
> Maybe it will be fixed for the main event in a few days time.

We can hope.

I imagine so.

---

### Post by imbjr on 2009-04-15
I just noticed that Tracker wasn't even installed on my VirtualBox installation. Wonder why? I did choose ext4 for the partition, but I see no real link between the two.

---

### Post by Yeti can't ski on 2009-04-16
Same here. Also waiting for a solution...

---

### Post by psychok7 on 2009-04-16
i killed the tracker process and the messages dont show up anymore and my cpu is ok now

---

### Post by snorbens on 2009-04-17
> **psychok7 said:**
> i killed the tracker process and the messages dont show up anymore and my cpu is ok now

Yes that is what I had to do! I now use beagle instead.

---

### Post by kaivalagi on 2009-04-17
There is a bug logged here: [https://bugs.launchpad.net/ubuntu/+s...er/+bug/361205](https://bugs.launchpad.net/ubuntu/+s...er/+bug/361205)

I think I fixed the CPU usage issues by killing trackerd and tracker-applet, deleting the ~/.cache/tracker folder and restarting the apps and re-indexing again

---

### Post by snorbens on 2009-04-17
> **kaivalagi said:**
> There is a bug logged here: [https://bugs.launchpad.net/ubuntu/+s...er/+bug/361205](https://bugs.launchpad.net/ubuntu/+s...er/+bug/361205)

I think I fixed the CPU usage issues by killing trackerd and tracker-applet, deleting the ~/.cache/tracker folder and restarting the apps and re-indexing again

Thanks will try that later.

---

### Post by MindSz on 2009-04-19
I might just wait a few days and have a fresh installation of the release version of Jaunty.

Aside from the tracker error, Jaunty looks pretty good.

---

### Post by snorbens on 2009-04-19
> **MindSz said:**
> I might just wait a few days and have a fresh installation of the release version of Jaunty.

Aside from the tracker error, Jaunty looks pretty good.

I had to do a complete re-install today and the tracker error has not returned.:D

---

### Post by Yeti can't ski on 2009-04-20
A complete re-install is really not an option for me at this moment (too much caotic and unrecorded tweaking, no separate partition for the Home folder, and so on...). 

I removed Tracker and will wait for the final release of Jaunty (and a few weeks thereafter) to see what happens. 

If the problem persists, Beagle may be an option. It seems to licensed under GPL, but is not a part of Ubuntu due to past bugs and current patent-risk related to its programming language. Is it really so?

If that is the only problem, I understand the decision of keeping it out of standard-Ubuntu but it would still be free software as far as I am concerned.

---

### Post by imbjr on 2009-04-20
Well, I installed the RC and tracker is again not installed.

This is under VirtualBox, mind, though I would have though that made no difference.

And I do not know why I complain - since one of the first things I do when installing recent releases is to un-install it.

---

### Post by baytuni on 2009-04-20
exactly the same problem

---

### Post by Yeti can't ski on 2009-04-22
It will probably sound too obvious but think I should share with you an update, because there may be other absolute rookies like me out there having a similar problem. 

After I uninstalled "Tracker" using (in GUI) Applications> Add/Remove Applications I solved most "gray screen" problems I was having but still faced a serious performance decrease in relation to the period of Hardy Heron. This, even though I had already used the new "System Janitor" application to try to clean things a little bit. 

Then, I finally thought of running "top" on terminal and I saw that "tracker" was still there with two bloody and heavy processes! Back from the dead!

I ran a "kill" of both processes, then also "sudo apt-get remove tracker", as well as "sudo apt-get autoremove". Finally, I went to System>Administration>Start-up and eliminated references to activation of Tracker during boot. Then I did reboot. 

It seems a whole new computer now!!! Fantastic! Zero "gray screens" or slowdowns! Much more speed! The CPU is even cooler. 

I must say I am a little disappointed with "Add/Remove Applications". I thought it was able to do clean and full uninstalls...

---

### Post by jml75 on 2009-04-23
Hi Guys,

As a previous post noted, you simply have to delete Tracker's current DB and reindex everything.

So delete " ~/.cache/tracker/* " and reindex everything and the problem is gone.

Must be that the newer version of Tracker as a problem with the db format of the older version.

Gxis!

---

### Post by faintscrawl on 2009-04-23
I have same error. It started seconds after booting up Jaunty for 1st time.

---

### Post by brallan on 2009-04-24
could this problem be that jaunty is not expecting that we have tracker-utils by default and that it is not installed? installing this package solved it for me.

---

### Post by kaivalagi on 2009-04-24
> **brallan said:**
> could this problem be that jaunty is not expecting that we have tracker-utils by default and that it is not installed? installing this package solved it for me.

I had the tracker-utils installed with intrepid but I still had the issue on upgrade, the only thing that fixed it for me was deleting the ~/.cache/tracker folder,restarting the apps and re-indexing again...

---

### Post by Yeti can't ski on 2009-04-24
[COLOR="Gray"]Ok, so I want to give a fresh start to Tracker, after removing it. I installed/reinstalled the relevant packages with Synaptic and once again I have a Tracker icon on Applications > Accessories. 

Now, the questions are:

i) how to start indexing?

ii) how to have once again the tracker applet?

iii) how to have it as a part of startup? 

Sorry for bothering and thanks in advance.[/COLOR]


EDIT - Ok, Problem solved. Sorry for the dumb questions. I had to re-add tracker and tracker-applet to the Startup (System -> Preferences -> Startup Applications (which was previously named "Sessions")). I logged in as a different user to get the necessary references:

Name: Tracker
Command: /usr/lib/tracker/trackerd
Comment: Tracker search and indexing service


Name: Tracker
Command: tracker-applet
Comment: Control and monitor the Tracker search and indexing services

Then reboot. After that I erased [username]\.cache\Tracker and now indexing seems to be working fine.

---

### Post by ayllu on 2009-04-25
I deleted the files inside those folders: /.cache/tracker/ and /.local/sahre/tracker/data/ then I Logout and login and the tracker reindex all well, and I solve the problem

---

### Post by rdelfin on 2009-04-25
> **ayllu said:**
> I deleted the files inside those folders: /.cache/tracker/ and /.local/sahre/tracker/data/ then I Logout and login and the tracker reindex all well, and I solve the problem

Thank you so much for your response.  It worked like a charm! :KS

---

### Post by gluxoid on 2009-04-26
Deleting ~/.cache alone did not help for me. Leaving my PC for 5-6 h alone, my 4 GB machine was heavy on the swap file. Typing "apt-get remove tracker" solved the problem with some loss of functionality (back to locate, find, grep, etc.)

---

### Post by Yeti can't ski on 2009-04-27
> **gluxoid said:**
> Deleting ~/.cache alone did not help for me. Leaving my PC for 5-6 h alone, my 4 GB machine was heavy on the swap file. Typing "apt-get remove tracker" solved the problem with some loss of functionality (back to locate, find, grep, etc.)

May be that's not the origin of your problem, but please note deleting only ./cache/tracker is not enough. You must also delete /.local/share/tracker/data/ 

Many thanks for the other guys that pointed that out.

---

### Post by lornaleeming on 2009-04-27
It seems that everyone has found this problem. We'll has to be patient until a fix is found :)

---

### Post by artheon on 2009-04-27
> **kaivalagi said:**
> I had the tracker-utils installed with intrepid but I still had the issue on upgrade, the only thing that fixed it for me was deleting the ~/.cache/tracker folder,restarting the apps and re-indexing again...
I have the same problem. Installing tracker-utils didn't solve it in my case. I'm now going to try the other options.

---

