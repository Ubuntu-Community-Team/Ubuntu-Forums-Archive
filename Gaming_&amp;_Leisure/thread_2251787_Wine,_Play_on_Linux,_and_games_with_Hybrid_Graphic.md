---
title: "Wine, Play on Linux, and games with Hybrid Graphics"
date: 2014-11-06
forum: Gaming &amp; Leisure
---

### Post by lama2p0 on 2014-11-06
Hello all, I seem to be having trouble with some games through POL, some work, other do not. Even games like StarCraft II which is rated platinum in the wine appdb I am unable to install. I feel my issue might be due to hybrid graphics. Some help getting these things to work and understanding them would be much appreciated.. I have a thread open on playonlinux already: [http://www.playonlinux.com/en/topic-12565-Starcraft_II_Will_Not_Install.html](http://www.playonlinux.com/en/topic-12565-Starcraft_II_Will_Not_Install.html)


My PC: [http://www.msimobile.com/level3_productpage.aspx?id=454](http://www.msimobile.com/level3_productpage.aspx?id=454)
I'm running Ubuntu Gnome 14.04.1

error while installing StarCraft II: [http://tinypic.com/r/2dj9wt0/8](http://tinypic.com/r/2dj9wt0/8)

```
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
01:00.0 VGA compatible controller: NVIDIA Corporation GK104M [GeForce GTX 870M] (rev a1)

```

I have installed bumblebee, and tried "$ optirun playonlinux" and installing the games running POL like that, but that did not help.

Thanks for any help..

---

### Post by mastablasta on 2014-11-07
have you read info on this site: [https://appdb.winehq.org/objectManager.php?sClass=version&iId=20882](https://appdb.winehq.org/objectManager.php?sClass=version&iId=20882)

looks like a lot of trouble to get this game running. 

also what wine version do you have?

---

### Post by lama2p0 on 2014-11-07
Yes, I've been there, didn't see anything about the problem I'm having.
I installed through POL which installes SCII with 1.5.10, I've tried switching it to 1.6.2 and 1.7.22, and they both error, but the error isn't given from Wine, it's given from Blizzard, and shows no details..

---

### Post by jcllings on 2014-11-08
I've both a Ubuntu PC which I built myself and a laptop from System76 which is an awesome Ubuntu pre-install.  The Desktop was designed to be a game box and the laptop was not.  A mistake on my part.  SCII + POL works fine on the Desktop which has resources (a gig's gpu nVidia memory etc. etc. ) aplenty... the laptop on the other hand has Intel integrated graphics which means it steals it's GPU memory from main memory, etc. etc. So it works on the desktop and not on the laptop. <rasberry>thththbbtt!</rasberry> Same situation, BlizzTard craps out not POL or Wine. System76 says the hardware is up to the task of meeting SCII's requirements but I doubt it's up to the task of running Linux + Wine + Lions + Tigers + Bears + POL + SCII, etc. etc.  Now, again, don't get me wrong, the laptop is awesome and I love System76.com but I built it using the tool on their website and I wasn't thinking Wine + StarCraft II when I did that.  

So... conceptually this might be similar to your problem.  It still might work but likely what is needed is a fairly special config.

---

### Post by lama2p0 on 2014-11-08
I'm pretty sure it has to do with Hybrid Graphics, Intel is the first  graphics controller that get's used by default, the second one GTX 870M  is the descrete card, and not used by default, the optirun command is  supposed to make it use the descrete GPU. Some games install and work, I  have League of Legends installed and playable, SCII, TERA, and Last  Chaos are all others I've tried through POL and none have worked. Aion  I've tried and it worked as far as I could tell, it installed and  opened, but apparently my just newly created account was banned the  moment I tried logging in? lol.. So I couldn't fullly test Aion..

So far all native games I've tried have worked. Team Fortress 2, Star Conflict, Wakfu, and other native games.

Sadly  even though I'm pretty sure it's something to do with Hybrid Graphics,  searching Hybrid Graphics and Wine/POL gives me little to no information  what so ever... Would be real nice if there was someone who could help  and provide any info on it, even if just to provide better  understanding.

Thanks for input.

---

### Post by aquablue25 on 2014-11-09
Hello there,

I think the games should still be able to run, even if they're accessing the primary GPU, which is an Intel IGPU.

**Number 1.** Which drivers do you have installed for your GPU? Make sure you are using the right drivers for your setup. [See here]("https://wiki.ubuntu.com/X/Config/HybridGraphics") for more information. According to the Ubuntu-Wiki, Ubuntu supports hybrid-graphics to some extent. You should be able to switch between the IGPU and your dedicated Nvidia GPU via the proprietary Nvidia GPU driver & by installing the recommended driver. Afterwards its just a matter of "**sudo nvidia-settings**" via a terminal (without the ") or alternatively "nvidia-settings" via Gnome 3 search. Navigate to the graphics switcher tab and switch to the dedicated GPU.

**Number 2.** POL is good, but not as good as Crossover, which is a commercialized version and the official sponsor/supporter of vanilla Wine. Games that don't work via Wine or POL usually work fine in Crossover for me. In addition, games such as: World of Warcraft, Starcraft II, Diablo 3 and many more are officially supported and maintained by Codeweavers, the creators of Crossover. What does that mean? Well, basically it means that they will make sure that the officially supported titles run with the newest version of Crossover. Supported apps and titles are tested by professionals in order to achieve maximum compatibility and performance. Installation is a matter of clicks: Download Crossover, update it, search for the game you want to install via the app, click on install and let it do its magic. You can download the trial and give Crossover a try [via this link]("https://www.codeweavers.com/products/crossover-linux/download/").

More info on the subject (all three officially supported):

- [Starcraft 2]("https://www.codeweavers.com/compatibility/browse/name/?app_id=4619")
- [Diablo 3]("https://www.codeweavers.com/compatibility/browse/name/?app_id=6277")
- [World of Warcraft]("https://www.codeweavers.com/compatibility/browse/name/?app_id=7714")

Thanks to the "[performance enhanced graphics]("https://www.codeweavers.com/about/general/press/20131112/")" feature in Crossover, all three games run just as fast, and often even faster than on Windows via Crossover on my Ubuntu machine. 

This is one of the many reasons why Crossover is superior to POL. 

**Number 3. Only if step 1 doesn't work:** According to some tips on the internet, you would need to do something like this to get games installed via Crossover to run on your dedicated GPU:

[I]**"If you want to run Crossover with the Optirun command to use  your High Power GPU just use this command line (If WoW is installed on a  Windows HDD):**

optirun //opt/cxoffice/bin/wine --bottle  Winblows  "/media/3A7E7F427E7EF5CB/Games/World of Warcraft Cata/World of  Warcraft Launcher.exe"  

By Media "3A7E7F427E7EF5CB  "  is meant  your HDD. You will need to get that info from your system. Dont forget  to edit your Bottle name also.
[B]
If you have installed WoW with Crossover use this command:[/B]

optirun ~/cxoffice/bin/wine --bottle some-bottle-name --cx-app some-app-name.exe"[/I]

Cheers,
Aqua

---

### Post by lama2p0 on 2014-11-09
Well, as I've mentioned I have Bumblebee, which installed the 331 driver.

$ nvidia-settings gives minimal options, no switcher options. Bumblebee handles the switching, or optirun/primusrun. 

And if I'm to eliminate POL, I'd rather use WINE on it's own. In fact I'd like to eliminate POL and just use WINE.

---

### Post by aquablue25 on 2014-11-09
Hello there,

that's strange. Nvidia-settings should have the an option to switch between GPU's.

I think it might be because you are using Bumblebee **instead** of Nvidia Prime. I recommend you use Nvidia Prime to do the switching. According to a bunch of posts on Askubuntu.com, _you can't have both installed at the same time_, so you will have to uninstall/purge everything from Bumblebee, then install the Nvidia drivers freshly afterwards and finally configure them accordingly to your needs. [See here]("http://askubuntu.com/questions/459315/how-can-i-switch-back-to-nvidia-card-from-intel-with-nvidia-prime") for more information. Quote from the answer: *"Bumblebee is still supported so you can install it if you prefer. You'll have to remove nvidia-prime then as you can't use both."*

[IMG]http://www.phoronix.net/image.php?id=nvidia_prime_ubuntu1404&image=nvidia_optimus_prime1_show&w=1366[/IMG]

[Click here]("http://www.phoronix.com/scan.php?page=article&item=nvidia_prime_ubuntu1404&num=1") and you will find an article on Phoronix, which underlines what I wrote above. Also, the article mentions some informational tips and tricks + performance tests.

[See here]("http://xmodulo.com/install-configure-nvidia-optimus-driver-ubuntu.html") for even more information on the subject. Quote: *"The [Bumblebee]("http://bumblebee-project.org/")  project was until recently as good as it gets in terms of Linux support  for hybrid graphics. It was actually possible if configured correctly  to utilise the Nvidia card for a desired application via CLI (i.e. 'optirun vlc'), but getting things like HDMI to work was a different story."* ... *"Make sure you don't have any packages like Bumblebee or other loaded  Nvidia drivers, otherwise it'll probably just break your X11. In case  you aren't working with a clean install and did previously install  Bumblebee etc, run the following before installing nvidia-331 and nvidia-prime:..."*

Another user ditched Bumblebee in favor of Nvidia-Prime, but encountered some difficulties. Check out [this link]("http://askubuntu.com/questions/459315/how-can-i-switch-back-to-nvidia-card-from-intel-with-nvidia-prime") for more information.

[In this Q&A]("http://askubuntu.com/questions/450154/nvidia-331-nvidia-settings-prime-profile-switching-error"), another user explains how to delete Bumblebee and install Nvidia-Prime.

**A last ditch effort:**

For your convenience, [this]("http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html") also might be helpful. A Prime-Indicator to easily switch between supported GPU's. Please note: I am not sure if this uses Bumblebee or not. Better try everything mentioned above before using this app.

And if everything mentioned above fails, [try this]("http://askubuntu.com/questions/472529/ubuntu-14-04-cannot-open-nvidia-settings-switch-between-gpus-hybrid-graphics").

----------
----------

About POL, Wine and Crossover: Why go with a complicated vanilla Wine installation? Using vanilla Wine, you will have a degraded experience because:

a) You will have to use manually create (by terminal) a 32-bit Wine environment for most of your apps, because 64-bit Wine can and will be buggy with most games.
b) You will have to create, configure and access "bottles" for your apps manually via the terminal in a complicated way.
c) Performance will be slower than what you can experience in Crossover 14 with performance enhanced graphics and optimized app profiles for a bunch of games.
d) You will have forum and IRC support only, no professional support via ticket, mail or phone whatsoever.
e) You will have to "tweak" stuff and install dependencies manually via the terminal or via Winetricks if a title doesn't run out of the box or if a title causes you issues.

And much more. [See here]("https://www.codeweavers.com/products/faq/differences/") for more information ("choosing the right Wine-based solution").

Verdict: I highly recommend using Crossover from Codeweavers, which is also recommended for endusers by WineHQ and POL.

-> [See here]("https://www.winehq.org/download/") at the top, WineHQ recommends and promotes the use of Crossover.
-> Quote from the [POL download site]("https://www.playonlinux.com/en/download.html"): *"PlayOnLinux mainly relies on [WineHQ]("http://www.winehq.org") project. If you want help them and to get a professional support of wine, please consider buying [codeweavers]("http://www.codeweavers.com/") products."*
-> Codeweavers is also responsible for a huge amount of work on the Wine project and they give all their technical advancements back to the project. By supporting Codeweavers, you are automatically supporting Wine. [See here]("https://www.codeweavers.com/about/support_wine/") for more information on the subject.

I hope this helps! I can't feel my fingers anymore.

Cheers,
Aqua

---

### Post by mastablasta on 2014-11-10
> **lama2p0 said:**
> Yes, I've been there, didn't see anything about the problem I'm having.
I installed through POL which installes SCII with 1.5.10, I've tried switching it to 1.6.2 and 1.7.22, and they both error, but the error isn't given from Wine, it's given from Blizzard, and shows no details..

not specifically. I ment if there is something in the setup you might have missed. the issue is either with the driver or with some missing libraries - it's what the error on the pic says.  the error is from blizzard but It is telling what the issue is in that screenshot you gave. 

using such a compatibility layer the error could actually mean something else. since we do not know exactly what is wrong or not recognised. is there any error thrown out in terminal when running wine or just this blizzard error?

---

### Post by lama2p0 on 2014-11-11
Well my problem with Starcraft II is resolved on the POL thread. [http://www.playonlinux.com/en/topic-12565.html](http://www.playonlinux.com/en/topic-12565.html)

---

