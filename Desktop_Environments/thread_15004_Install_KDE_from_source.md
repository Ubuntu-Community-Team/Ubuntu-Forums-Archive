---
title: "Install KDE from source"
date: 2005-02-11
forum: Desktop Environments
---

### Post by mirtux on 2005-02-11
Hi,
 i would like to install KDE 3.3.2 from source file (i'm using Warty) and work with it under ubuntu. Do you if exists some sort of how-to to have it running *quite *easily? 
  I've seen that is available the package **Konstruct. **Is it affordable?
  Regards,
  MC

---

### Post by lao_V on 2005-02-11
[QUOTE=mirtux]Hi,
 i would like to install KDE 3.3.2 from source file (i'm using Warty) and work with it under ubuntu. Do you if exists some sort of how-to to have it running *quite *easily? 
  I've seen that is available the package **Konstruct. **Is it affordable?
  Regards,
  MC[/QUOTE]
 Konstruct is pretty good, but make sure you have installed all the dependencies as lister here

[http://www.kde.org/info/requirements/3.3.php](http://www.kde.org/info/requirements/3.3.php)

Then start by installing only kdebase.

---

### Post by mirtux on 2005-02-11
Hi,
  thanks for reply. Since i've installed from source a number of kde programs, do i have to recompile them another time, is this right?
 
 Regards,
 MC

---

### Post by lao_V on 2005-02-11
[QUOTE=mirtux]Hi,
  thanks for reply. Since i've installed from source a number of kde programs, do i have to recompile them another time, is this right?
 
 Regards,
 MC[/QUOTE]
 As far as I know, depending on which package you chose to install from Konstruct, it will compile everything that's included in that package. Good things is it makes a new directory in your /home so it doesn't overwrite existing KDE apps

---

### Post by apokryphos on 2005-02-11
And by the way, Konstruct is, of course, free.

---

### Post by mirtux on 2005-02-11
I'm currently building it..... i'll post about the results,
 
 Regards,
 MC

---

### Post by lao_V on 2005-02-11
[QUOTE=mirtux]I'm currently building it..... i'll post about the results,
 
 Regards,
 MC[/QUOTE]
 Let us know which package you're buillding and how long it takes!!
It took me over 4 hours for kde package on 2GHz with 300MB memory!!

---

### Post by mirtux on 2005-02-12
Hi, 
 i'm finally here after installing KDE. I'm pleasently surprised by the installation process and by KDE 3.3.2. I dropped GNOME in favour of this. 
 Konstruct worked very well ---> you have to stay connected to the internet during all installation that took me nearly  5 hours. I've made the "normal installation":
 
 meta/kde           | 172MB | All "KDE 3.3.2" packages & dependencies
 
 and after this i installed, always with Konstruct, kile, koffice and kdevelop.
 
 Happily convinced,
 MC

---

### Post by piedamaro on 2005-02-12
What's the point of compiling kde-3.3.2 on ubuntu while kde-3.3.2 is in the universe?

---

### Post by TheCondor on 2005-02-12
Hello people, I saw this thread as I was curious to see how I could install Kde in Ubuntu.

I tried through konstruct and all the time, after the whole compilation thing that took some time, I got errors. First there were some dependencies I resolved through synaptic. The last time it was an error with the kdescreensavers and all. I just didnt feel like dealing with it cos I didnt have the time and I had to shutdown the pc. 

I also looked at synaptic and found that the available KDE version was 3.2.3 and not 3.3.2 which is the latest, and that I happened to use it while on Suse 9.1 ( I upgraded to KDE 3.3.2 ) 

I wanted to ask how could I find the latest KDE through apt-get-synaptic?

I have enabled these extra repositories from this ubuntu guide, which is really helpful, but it seems I cant find the latest KDE.  :roll:  :roll: 

Could someone explain to me what I could be doing wrong as it seems there is no luck with konstruct. Id be really grateful and thanks in advance

---

### Post by piedamaro on 2005-02-12
To install Hoary, you may edit your /etc/apt/sources.list configuration file to replace all instances of 'warty' with 'hoary.'

---

### Post by mirtux on 2005-02-13
[QUOTE=piedamaro]What's the point of compiling kde-3.3.2 on ubuntu while kde-3.3.2 is in the universe?[/QUOTE]
 
 The point is that from the repositories you can only get version **3.2.3 **and not **3.3.2** (at least for warty)

---

### Post by TheCondor on 2005-02-13
I installed KDE 3.3.2 by replacing all instances of warty in the sources.list of the apt file into hoary. I put warty back again after the installation.

I must say that KDE installed pretty well, but it doesnt work on my account, hangs when loading the panel. This is because I had suse before with the same /home partition and after I put Ubuntu I didnt have kde and i think it messed up. With the root account it works normally. 

What I noticed is that after installing KDE, even Gnome runs A LOT faster than it did. I know it sounds weird, but heres an example : Whenever my system was getting a bit of abuse from some applications that needed cpu, if I tried to open my home folder, it would be a bit fast but the icons wouldnt show INSTANTLY, it would take like 1-2 seconds to show. I dont need to mention what was happening when I tried accessing my 120Gb drives with all the music on them...

Now, the home directory opens right away, its not sluggish anymore ( that was the reason for me to install kde cos I knew how it worked on suse - just as fast as gnome right now ) and I think ill stick with gnome even though I spent so much time for KDE. lol. 

I have two questions so far about gnome though. After the kde installation, the gnome-control-center refuses to start. Thats not a big deal because all of the options there are found elsewhere. The next thing that kinda bothers me a lot, and cant seem to find a solution for it, is that in the taskbar on the bottom, where the windows that are open are shown, they all are groupped instantly and they appear so small, thus giving me a hard time to understand what is what. Id like to have them group only when the space is limited, as I had before, but I cant find where to change this option. I tried nautilus, within the gnome control center options, and I didnt find anything to change it. Any help would be appreciated.

---

### Post by piedamaro on 2005-02-13
Right click on taskbar handle/properties.

---

### Post by TheCondor on 2005-02-13
[QUOTE=piedamaro]Right click on taskbar handle/properties.[/QUOTE]

I have tried this as well, because I was sure the option was there!! But its not  :-?  :-? 

How else could I configure this it really bothers me... ](*,)  ](*,)

---

### Post by mirtux on 2005-02-13
It seems that a great part of Ubuntu users has lot of, let me say, hate, againts KDE. Some time ago i made the same mistake, but now i realize that i'm preferring KDE over GNOME, for the cleaness and easy management. I think we must have both of them...  

Regards,
MC

---

### Post by TheCondor on 2005-02-13
[QUOTE=mirtux]It seems that a great part of Ubuntu users has lot of, let me say, hate, againts KDE. Some time ago i made the same mistake, but now i realize that i'm preferring KDE over GNOME, for the cleaness and easy management. I think we must have both of them...  

Regards,
MC[/QUOTE]

I was pretty much happy with kde when on suse. I still like it but since I installed and used Ubuntu ( its the ONLY OS I had that I didnt need to format or do other stuff to repair it for so long :) ) I started to like gnome more and more every day, although I think it misses some SERIOUS features. I wont be going back to KDE cos it gives me problems and I cant be bothered to fix them. 

Gnome gives you also a more linux feeling, rather than the windows feeling that you get with KDE. Its all about taste anyway you cant blame anynone for their choice of their GUI ( not implying you are ). 

Its linux so whatever the case, Gnome, KDE, IceWM, its just perfect.  :-)

---

### Post by jdong on 2005-02-13
Umm, it's quite impossible to compile KDE 3.3.x from source on Warty without destroying your system.

I tried to make a KDE backport, but it quickly fell apart because of the masses of libs that I needed that weren't in Warty. If you add them, you risk breaking binary compatibility with existing programs, which would require a complete rebuild of all reverse dependencies (revdep-rebuild... you mean that tool in Gentoo that took hours to run after every update? yeah)

---

### Post by TheCondor on 2005-02-13
lol every time i log to KDE to check some things Im getting obsessed  :-P 

My root account can log in just fine, everything is functional, which isnt the case with my normal user account. I think the files in my home directory since I used Suse ( and broke KDE ) are still there, and KDE appears to load but i cant do anything, nothing is shown on the panels, nothing on the 'start' menu etc. 

I managed to make KDE load ( it didnt even load at first ) by copying the .kde folder of my root's home into my user's account home directory. But it seems its not the only thing required to make KDE load normally.

Could someone guide me through what Id need to do to recover my KDE on my user account please? Ill be trying on the meantime but Im afraid I might break something on Gnome too and then ill go some serious headbanging  ](*,)  ](*,)  ](*,)

---

### Post by piedamaro on 2005-02-13
Perhaps you have borked your system because you used root privileges to do normal work...
Sorry I could give hints on restoring gnome config since I've done it a bunch of time, but I 've never really used kde, I've always preferred gnome (4 years as of now). 
I know there are .qt and .kde directories.
Probably it's just a matter of saved session (especially if you are using your suse home directory, I wouldn't make this). Try to log into kde and launch your components manually (kicker, konqueror, etc.).

---

### Post by mirtux on 2005-02-14
[QUOTE=jdong]Umm, it's quite impossible to compile KDE 3.3.x from source on Warty without destroying your system.
  
 I tried to make a KDE backport, but it quickly fell apart because of the masses of libs that I needed that weren't in Warty. If you add them, you risk breaking binary compatibility with existing programs, which would require a complete rebuild of all reverse dependencies (revdep-rebuild... you mean that tool in Gentoo that took hours to run after every update? yeah)[/QUOTE]
  Hi,
 sorry what do you mean by "destroying your system"? If you want to say that i cannot upgrade any longer my system with apt regarding KDE packaging i agree with you, but however KDE install itself automatically in a user directory without asking any time the root password.
  
  Regards,
  MC

---

### Post by mirtux on 2005-02-14
I think i have to correct the last post: IT IS possible to continue using KDE components given by the repositories since if you build KDE from sources using Konstruct it uses by **default** the flag $HOME/kde3.3.2, so it doesn't touch any system files in /usr (of course you can change it and let it override the /usr KDE installation). So it's an indipendent installation that goes parallel and doesn't encounter the precompiled one. 
 
 Regards,
 MC

---

### Post by piedamaro on 2005-02-14
Then you'll have to use a separate account for that, cause probably mixing configuration files in your home dir will lead to problems.

---

### Post by mirtux on 2005-02-14
[QUOTE=piedamaro]Then you'll have to use a separate account for that, cause probably mixing configuration files in your home dir will lead to problems.[/QUOTE]
  
  You'll not have a messed up installation, and don't have to use a separate account because the *.kde* directory in your home is not touched..... konstruct is able to create a new directory (for me, as an example is *.kde3.3.2*) where th fresh KDE can install user's options.
  
  Regards,
  MC

---

### Post by piedamaro on 2005-02-14
Didn't imagine that :) konstruct is smart.
Eheh dai che siamo sempre di più! :)

---

### Post by mirtux on 2005-02-15
I agree with you....
  (sono d'accordo!!) ;)
  
  MC

---

