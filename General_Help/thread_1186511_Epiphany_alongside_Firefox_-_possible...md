---
title: "Epiphany alongside Firefox - possible..?"
date: 2009-06-13
forum: General Help
---

### Post by Thanh-BKK on 2009-06-13
Hi.

Just a quick question - is it somehow possible to install Epiphany WITHOUT having to remove Firefox (and a good dozen other things including "Ubuntu Desktop" that Synaptic wants to get rid of when installing Epiphany)..?? 

Firefox's sluggishness is going on my nerves now and someone suggested i use Epiphany as it would be better integrated in Gnome. I already tried Swiftfox and it made no difference.

Ubuntu 8.04.2 Hardy here, 

Kind regards......

Thanh

---

### Post by t0p on 2009-06-13
I'm running Jaunty NetBook Remix and I installed epiphany on it without any problems.  Firefox still works fine and nothing has gone wrong with the system.  As NBR's difference with a usual Ubuntu set up is mostly cosmetic, I'd say you won't have any problems either.

---

### Post by ajgreeny on 2009-06-13
If firefox is so sluggish, I suspect it is something to do with your configuration of the application.  Perhaps it is worth looking into that a bit more before you start fiddling too much.

However, I am amazed to hear you say that installing epiphany means you have to remove many other applications.  That is definitely not normal, and therefore leads me to believe that there is something very wrong with your system in general which needs further investigation.

---

### Post by tragicglee on 2009-06-13
Open up a terminal, run the following to simulate an install of the browser, and paste the output here. (I'm just curious about what Synaptic wants to remove, and why). Did you install firefox from somewhere other than the repos? 
  
```
sudo apt-get install -s epiphany-browser
```

FWYIW, ubuntu-desktop is merely a meta-package. Removing it doesn't remove your actual desktop, and letting it go temporarily it is fine. You definitely want to re-install once it's taken out though b/c it insures proper upgrades! OTOH, I'd hold off on removing it in this situation, not knowing what the other files are.

---

### Post by Thanh-BKK on 2009-06-13
Hi.

In the beginning my Firefox ran excellent. However at some stage it got some update and ever since it got slower and slower with each subsequent update. Now it takes  aboyt 10 seconds to start and just as long to close, often briefly displaying a message that it stopped responding and if i want to force-quit? It does eventually quit by itself, just takes it's time.

I installed Swiftfox and after initial installation it was lightning-fast, however after the first regboot it behaves exactly like Firefox, no difference at all.

Either one, if used together with Thunderbird, brings Thunderbird down - i.e. when i start Thunderbird and Firefox/Swiftfox at the same time they both grey out for about 30 sends, after which Thunderbird (!) comes up with "A script on this page is busy or stopped responding..", clicking "stop script" gets both Thunderbird and Firefox/Swiftfox working again.

I have posted several times about this issue and was never given a solution, however googling the issue yields the fact that a LOT of users have the exact same problem, i.e. extreme sluggish Firefox - not only in Ubuntu but in Linux generally, and only with Firefox 3.x. 

@t0p
Err i'm on Hardy and wish to stay there..... plus, on a second computer running Jaunty, Firefox is just as sluggish (and there no add-ons whatsoever are installed!)

@ajgreeny
It is the "epiphany-gecko" package that wants to remove all that stuff, and the others won't install before that one is in. Please see attached screenshot, looks like it wants to delete half my system. Apart from the sluggish Firefox my system runs rock stable and ultra-reliable, however Firefox is one of the apps i use the most, so the more annoying it becomes. Once open it (Firefox) works fine, too, i have no issues at all for example with flash/YouTube.  However the extreme slow startup/shutdown and it taking T-Bird down is enough for me. 

@tragiclee
Your command yields this:

thanh@thanh-desktop:~$ sudo apt-get install -s epiphany-browser
[sudo] password for thanh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  epiphany-browser: Depends: epiphany-gecko but it is not going to be installed or
                             epiphany-webkit but it is not installable
E: Broken packages

Please see my screenshot to see what happens when i want to install the mentioned "epiphany-gecko" package. 

Firefox is what came from Hardy's live CD and has been updated again and again through normal updates which are coming from the repos. Swiftfox is a non-repo one however my problem existed long before installing that. When Firefox 3 was still beta it worked absolutely fine..... ever since one of it's updates it virtually broke on me (reproducable by installing Hardy on another computer and updating nothing but Firefox - it'll show the same behaviour).

Add-ons installed: Black Steel Theme, AdBlock Plus, Forecastfox, DownloadHelper, DownThemAll, PDF Download, FlashGot. Disabling or uninstalling them shows no difference, as mentioned on another machine a Firefox without any of them does the same. 

Kind regards.....

Thanh

---

