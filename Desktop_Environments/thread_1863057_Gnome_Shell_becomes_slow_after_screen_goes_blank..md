---
title: "Gnome Shell becomes slow after screen goes blank."
date: 2011-10-17
forum: Desktop Environments
---

### Post by hotstovejer on 2011-10-17
I have noticed that when I leave my machine for a while then come back, that GS is very slow. I put in my password because the screen is locked, and it becomes so slow that I have to restart the lightdm service to make it snappy again.

Anyone else noticing this?

Also, side note. Is it just me, or does Alt + F2 not work anymore?

---

### Post by Sir Rodness on 2011-10-18
I'm using Gnome Shell as well. I'm not sure it's tied into the screen going blank, but I do agree that there is some over all latency with programs opening. For instance ubuntu tweak when I launch it takes quite a while longer to open up than it did in the past. Granted ubuntu tweak was probably never intended for Gnome Shell it still a little surprising the speed of that program and other programs used when running gnome shell. Even noticed that saving simple text files in gedit while in gnome shell takes noticably longer than it should. Gnome Shell is pretty and I personally prefer it over Unity in 11.10(though I wouldn't mind turning off the notification popup bar at the bottom) can anyone tell me what they done on a clean install that maintained performance? I may go back to 11.04 where I can use the reliable gnome panel which is much easier to customize to personal perference than gnome shell is.

---

### Post by 23dornot23d on 2011-10-18
Check memory usage and cpu usage in system monitor .....

I tend to run a conky ..... and the cpu can go mad in firfox .... container-plugin

but it also grows after that ....... 1100 Meg + if its left 

This may be the problem also check Htop see what is running ....

just a thought ..... might help identify the problem ....

Not sure why it does it when leaving into the lock screen ...

---

### Post by Jim_in_Omaha on 2011-10-19
> **23dornot23d said:**
> Check memory usage and cpu usage in system monitor .....

I tend to run a conky ..... and the cpu can go mad in firfox .... container-plugin

but it also grows after that ....... 1100 Meg + if its left 

This may be the problem also check Htop see what is running ....

just a thought ..... might help identify the problem ....

Not sure why it does it when leaving into the lock screen ...

I am having this happen too. Left the system on last night doing some encoding. This morning I had one core at 100%. Also, during general use, I noticed that dragging windows around it sometimes starts hesitating while dragging ever so slightly. 

So far to fix it, I reload the Gshell with the ALT-F2, then 'r' in the command. If you don't have that then set up the 'keyboard' -> shortcuts -> System -> 'Show the run command prompt' and set it to ALT-F2 to bring up the 'Please enter a command:' prompt.

This does reset it. I noticed the resources returned back to normal.

---

### Post by Sir Rodness on 2011-10-21
> **Sir Rodness said:**
> I'm using Gnome Shell as well. I'm not sure it's tied into the screen going blank, but I do agree that there is some over all latency with programs opening. For instance ubuntu tweak when I launch it takes quite a while longer to open up than it did in the past. Granted ubuntu tweak was probably never intended for Gnome Shell it still a little surprising the speed of that program and other programs used when running gnome shell. Even noticed that saving simple text files in gedit while in gnome shell takes noticably longer than it should. Gnome Shell is pretty and I personally prefer it over Unity in 11.10(though I wouldn't mind turning off the notification popup bar at the bottom) can anyone tell me what they done on a clean install that maintained performance? I may go back to 11.04 where I can use the reliable gnome panel which is much easier to customize to personal perference than gnome shell is.

Made some discoveries that have me working a little more quickly and with a little more stability. I imagine like most other ubuntu situations doing what I did may not work for everyone, but it's got me feeling a more stable and a little happier. Thanks for 23dornot23d for their tip. That's what got me thinking that I may have to search for update apps and start thinking about possible conflicts and which platforms apps may have been originally designed for.
1. Ubuntu tweak had a newer version for 11.10. Loads faster than ever. So if you happen to have an older version of tweak archived on your computer be sure to go to their website and download the latest version from the ubuntu tweak website. That also got me to remove all archived debs that I have. I only install from the Software Centre or PPAs for gnome shell at the moment. Speed sticks around when sticking to that route...for now.
2. I uninstalled Unity desktop and all directly associated with it. Only have gnome shell now. Works for me.
3. Installed all gnome shell extensions to help with configuration. Found them all at [http://www.webupd8.org/](http://www.webupd8.org/) in the gnome shell section. Nice site by the way. Though I went back to docky instead of using the dock extension. Found the dock extension wasn't playing nice when I wanted to use dual screens.
4. Ubuntu is for tweaking and discovery, I love it!

---

### Post by Jim_in_Omaha on 2011-10-21
It appears to also happen on my Thinkpad T500. What I discovered is that Gnome3 does not have a screen saver. But it blanks the screen and initiates power-save on the monitor.

When it wakes up I found the CPU usage goes way up. Then I restart Gnome3 and it goes back to normal.

I see that XScreensaver is loaded but the daemon is not running. So when I started it and set it to blank the screen, so far it does not chew up the CPU after coming back on. To soon to tell.

Yes Gnome3 is getting slick especially with all the extensions and stuff over at WebUpd8 is coming up with.

I have not unloaded Unity yet. I have found it seems fairly stable so it will be my fallback for the time being if Gnome3 goes nuts.

So far, it's this screen blanking then CPU usage that is bothering me. Most everything else seems good.

This typing thing to find applications grew on me fast. Now in XP (work) I am wanting to type the name of the program to start, instead I'm poking through the start menu-programs to find it amongst the hundred or so applications.

---

### Post by Jim_in_Omaha on 2011-10-22
Left it running overnight with Xscreensaver. It did not shut off the monitor, so I obviously did not have it set right.

But the memory usage for Gnome-shell grew to 2.9G. Reset it, and it went back to normal.

Any ideas, using Gnome Shell 3.2?

---

### Post by joonpy on 2011-10-25
I'm using openSUSE, but this happens to me as well. It becomes very slow, and when I kill it it becomes snappy again.

---

### Post by Jim_in_Omaha on 2011-10-25
I ran Unity (not Unity2d) all night. This morning it is fine. No CPU or memory usage. But I do not know if it does some kind of reset on its own like Gnome Shell can do when there are enough errors.

---

### Post by joonpy on 2011-10-25
Apparently there is a bug report: [https://bugzilla.gnome.org/show_bug.cgi?id=642652](https://bugzilla.gnome.org/show_bug.cgi?id=642652)

It's a little bit disappointing that it has not been fixed for more than 8 months though.

---

### Post by Jim_in_Omaha on 2011-10-25
> **joonpy said:**
> Apparently there is a bug report: [https://bugzilla.gnome.org/show_bug.cgi?id=642652](https://bugzilla.gnome.org/show_bug.cgi?id=642652)

It's a little bit disappointing that it has not been fixed for more than 8 months though.

I wonder.. This problem for me is happening on my desktop which is an upgrade from 11.04 which was a fresh install at the time with a down graded compiz.

My T500 is a fresh install and seems very well.. And the T500 comes out of suspend in about two seconds, connects on the network in about 2 seconds after that..

Perhaps I will back up home, and wipe it out then rebuild it...thoughts??

---

### Post by Jim_in_Omaha on 2011-10-25
Update: I am sticking my neck out here on the stability side of things.

I am trying this
[http://www.ubuntuupdates.org/ppa/gnome_shell?dist=oneiric](http://www.ubuntuupdates.org/ppa/gnome_shell?dist=oneiric)

They put out some new updates today 10/25. I did the update with this PPA, and so far the ram usage is holding at around 108meg and no CPU usage at 0%. Before it would continue upward.

sudo add-apt-repository ppa:ricotz/testing 
sudo apt-get update

I will leave it on all night and see what the morning brings.

Side note: The extensions for the app menu does not work. It gets turned off in the tweaks.

---

### Post by Jim_in_Omaha on 2011-10-26
After running all night UPDATE:

The PPA with the update for 3.2.1 has done this much
There is no longer a CPU usage on gnome-shell process, but the memory still grows. Although, it only grew to 323meg instead of 2.9gig like the night before.

Doing the reset Alt-F2 'r', resets it back to under 80meg.

So, for the moment, it has increased the usability for GnomeShell for sure. On the laptop, the memory was not such a huge issue but the CPU usage would spike up. The CPU usage is not happening, the memory did grow to 240meg, I closed FF 7.0 that I left on, it dropped to 220meg on the gnome-shell process. Did not see that behavior before. It would just stay the same after closing other applications.

For what its worth...

---

### Post by jstapels on 2011-11-23
I'm glad to hear that Ricotz PPA makes things more stable, but I'm a little nervous to enable this (and the necessary oneiric proposed ppa). Does anyone know if the stuff Ricotz is building will eventually make it into the gnome3-team ppa?

---

