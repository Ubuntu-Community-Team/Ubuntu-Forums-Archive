---
title: "Wesnoth 1.4 stable has just been released!"
date: 2008-03-08
forum: Gaming &amp; Leisure
---

### Post by eragon100 on 2008-03-08
It's here! Get it now! :guitar:

---

### Post by eragon100 on 2008-03-08
And if you don't want (or, like me: can't) compile it, the windows binary is availabe for download. It runs so great under wine that I almost forgot I was running linux when I tried 1.3.17 in it because I didn't want to compile :lolflag:

---

### Post by timmy-mac on 2008-03-09
Who usually packages it?  

Can we expect it in the repos, or should I get compiling? 

Takes all week on this sh*tty machine! :P

---

### Post by Nevon on 2008-03-09
What's new?

---

### Post by Perfect Storm on 2008-03-09
release notes: [http://www.wesnoth.org/start/1.4/](http://www.wesnoth.org/start/1.4/)

Ubuntu 64-bit compiling guide: [http://gaming.gwos.org/doku.php/guides:64bit:battle_for_wesnoth](http://gaming.gwos.org/doku.php/guides:64bit:battle_for_wesnoth) (updated to fit v1.4)

---

### Post by safirst on 2008-03-10
**Compiled Wesnoth 1.4 for Ubuntu 7.10** (Gutsy) can by found [here]("http://195.234.110.72/wesnoth_1.4-safirst2_i386.deb"). :guitar:
[New version added!]("http://ubuntuforums.org/showpost.php?p=4530938&postcount=39")

Installation:
```
dpkg -i ./wesnoth_1.4-1_i386.deb
```

To run it just type "wesnoth" (without quotes) in terminal application.

I compiled The Batlle for Wesnoth from official sources and use checkinstall to build deb from it.

---

### Post by Perfect Storm on 2008-03-10
Note to those who want to try safirst .deb.

It's on your own risk. In general you don't install something from a random guy that throws in a package as you may not know what it contains without reading the codes.


Not accusing safirst have done it, but as in a general rule about computing safty.

---

### Post by timmy-mac on 2008-03-10
Whilst you're obviously quite right, AI, I'm going to flout your advice and offer my thanks to safirst!

- Many thanks!

---

### Post by anjilslaire on 2008-03-11
Debs are up at getdeb.net now
[http://www.getdeb.net/app/The+Battle+for+Wesnoth](http://www.getdeb.net/app/The+Battle+for+Wesnoth)

---

### Post by safirst on 2008-03-12
> **anjilslaire said:**
> Debs are up at getdeb.net now
[http://www.getdeb.net/app/The+Battle+for+Wesnoth](http://www.getdeb.net/app/The+Battle+for+Wesnoth)

Quote from getdeb.net:
> 
Hmm... I did not download the extra campaigns available above, and so when I, ingame, click on the Campaign button nothing happens. It seems that the standard campaigns are missing:

• wesnoth-aoi (An Orcish Incursion)
• wesnoth-did (Descent into Darkness)
• wesnoth-l (Liberty)
• wesnoth-nr (Northern Rebirth)
• wesnoth-sof (Sceptre of Fire)
• wesnoth-sotbe (Son of the Black Eye)
• wesnoth-thot (The Hammer of Thursagan)


Is it real?

---

### Post by Ozor Mox on 2008-03-12
Yeah I noticed this. There are 7 extra single player campaigns in Wesnoth 1.4, bringing the total to 13, but I noticed that the GetDeb packages don't include them, only the original 6. Presumably, there would be nothing appearing in the campaign menu because the 6 that GetDeb have are for Wesnoth 1.2, and are not compatible with 1.4 and therefore don't show up.

This is why instead I compiled it. It's very easy, all the dependencies are listed on the [Wesnoth site](http://www.wesnoth.org/wiki/CompilingWesnoth).

---

### Post by eragon100 on 2008-03-12
If you don't want to compile, you have two options:

1.Install the windows binary under wine, I hereby give it a platinum rating, single- and multplayer, and map editor as well. Literally everything works :)

2. Use safirst's unofficial .deb available on page 1 of this topic, which I recommencd :)

Oh and to start safirst's instlled package, open a terminal and type "wesnoth"

Have fun!

---

### Post by eragon100 on 2008-03-12
WARNING: after installing the .deb package on he previous page, the update manager will tell you have two updates available for wesnoth. Do NOT install them!
They''l downgrade to 1.2.8!!

If you have automatic installation of updates enabled, disable it!!

---

### Post by anjilslaire on 2008-03-12
Ack!
Sorry for posting the getdeb files guys. You're right, they're not complete. Guess we'll have to wait or compile ourselves. I'd rather not have a version that's naggign me from the repo's to update, or tweak my apt settings for 1 install.

---

### Post by wingnux on 2008-03-13
This game is soooo addictive! =)

---

### Post by eragon100 on 2008-03-13
You aren't going to believe this!

I tried to add a campaing as an add-on to 1.4. With the unofficial (but complete and working fine) .deb on the first page, it didn't work. It said it installed the add-on, but ti wasn't in the menu, even after restarting the game. In the windows version under wine, it worked perfectly! It was the same campaign! :confused::confused::confused:

---

### Post by happyhamster on 2008-03-13
Wesnoth is evil. Really. You just think: 'Wesnoth, hmmph, whatever,  never heard of it.  It's probably crap, but let's check it out', and next thing you know (and 1 million mouse-clicks later), the police breaks down your front door because the neighbours didn't see you leave your home for a few weeks. And you notice your cat died of starvation. And it becomes painfully obvious that whatever little was left of your social life after previous incarnations of Wesnoth (or Frozen Bubble; that one is evil too!) has been obliterated completely.

Could a mod move this thread to the jail please? For all our sakes? Please?

Evil I say!

---

### Post by Ozor Mox on 2008-03-13
> **eragon100 said:**
> You aren't going to believe this!

I tried to add a campaing as an add-on to 1.4. With the unofficial (but complete and working fine) .deb on the first page, it didn't work. It said it installed the add-on, but ti wasn't in the menu, even after restarting the game. In the windows version under wine, it worked perfectly! It was the same campaign! :confused::confused::confused:

Perhaps there is a problem with the unofficial deb? Try compiling it. I haven't yet installed any add-ons yet but I'll try it later and see that they appear in the campaign menu.

---

### Post by solitaire on 2008-03-13
Think i'll wait awee while before i'll install it 

I just tried compiling the source but I keep getting an error saying sdl_mixer must have OGG support ( as far as i can tell it does)

When i run ./Configure  I geet to the following point:

```
checking for OGG support in SDL_mixer... no
configure: error: *** SDL_mixer has no OGG support! You need SDL_mixer with OGG support

```

I've installed the SDL_mixer from the SDL site (as per the Compiling Guide).


any Ideas guys?

---

### Post by eragon100 on 2008-03-13
I can't compile it *** well, it keeps saying i don't have libsdl-image while i have installed both the normal and the -dev one form synaptic, and even compiled boh of them from source


Wine compile without any problems, but wesnoth won't :(

plus, I don't want to have to compile every minor realease and i do want to stay up to date woth bugfixes.  And i have a lot of aved games in the windows version already. I think i will' keep using the windows version, it's a lot easier and it runs, well, better, obviously :lolflag:

---

### Post by solitaire on 2008-03-13
Runing Windows version for now too :D :lol:

---

### Post by anjilslaire on 2008-03-14
Isn't it kind of sad that sometimes we have to run the Windows version of an app in wine, because the native Linux version isn't available in an *easy to use* form?

Not knocking those using the Windows bits, but anyone know what I mean?
I don't suppose there's a chance that someone associated with th Wesnoth team could host a repository? After all, Debian-based distros are pretty popular...

---

### Post by eragon100 on 2008-03-14
I don't understand why they don't make a autopackage or other distro-independent package. They package the game for opensolaris, which is less popular then linux. Hack, they even package it for amiga OS 4, something obscure called "e-com workstation" :(

---

### Post by Ozor Mox on 2008-03-14
> Isn't it kind of sad that sometimes we have to run the Windows version of an app in wine, because the native Linux version isn't available in an *easy to use* form?

When I first started using Ubuntu I always used to find it odd that new versions of free software were released straight away for Windows as an exe, but for Ubuntu I had to either wait for the next release when the repositories are updated, or compile the software myself and look for dependencies etc. Now I've compiled quite a bit of software, I've become more familiar with the process so I'm not so bothered anymore, but it would be great if these software projects could release at least a deb and rpm as well maybe...

---

### Post by icechen1 on 2008-03-14
> **anjilslaire said:**
> Isn't it kind of sad that sometimes we have to run the Windows version of an app in wine, because the native Linux version isn't available in an *easy to use* form?

Not knocking those using the Windows bits, but anyone know what I mean?
I don't suppose there's a chance that someone associated with th Wesnoth team could host a repository? After all, Debian-based distros are pretty popular...

I never got problem compiling(just install all the dependencies and the ones with a -dev at the end then use checkinstall to install it),it even makes an icon for it.
EDIT:Unofficial repos here: [http://vleu.net/apt/](http://vleu.net/apt/)
EDIT:My version of wesnoth got upgraded itself!The version is 1:1.4~ppa1,maybe because i got the backports repos on?

---

### Post by anjilslaire on 2008-03-15
Interesting. Please post your relevant sources.list
Although, if you have your own repo, wouldn't that be the source of your upgrade?

---

### Post by MaX on 2008-03-16
I tried installing Wesnoth 1.4 on Hardy now.
Everything but sound works...

---

### Post by Lord Illidan on 2008-03-16
Honestly, compiling wesnoth isn't so difficult.

---

### Post by dynamethod on 2008-03-16
> **Lord Illidan said:**
> Honestly, compiling wesnoth isn't so difficult.

Well maybe you would like to shed some light on this?

I get as far as this:

configure: error: *** SDL_mixer has no OGG support! You need SDL_mixer with OGG support

however i installed SDL_mixer like this:

./configure --enable-music-ogg-tremor


and i still have that same error :confused:

---

### Post by Perfect Storm on 2008-03-16
Well SDL_mixer(-dev) works well on my installation. Other than you have to prefix the lib if you compiled it from scratch.

---

### Post by dynamethod on 2008-03-16
bah, i just cheated and grabbed the debs from getdeb, though the game runs reaaally slow :S

---

### Post by safirst on 2008-03-16
**New version of my unofficial deb.**

Changes:
** Fix bug with downgrade to 1.2.8*

**Note:** Addons working fine in this version. To play in addons company use "Local game" from "Network game" menu. Select addon in maps and play!

You can download new version [here]("http://195.234.110.72/wesnoth_1.4-safirst2_i386.deb").

---

### Post by eragon100 on 2008-03-16
Thanx, great :)

---

### Post by eragon100 on 2008-03-16
Yep! Everything works great, including the addons. If it would just install a menu entrie it would be perfect :lolflag:

---

### Post by anjilslaire on 2008-03-16
I just grabbed the new debs from Getdeb.net. They no longer try to downgrade to 1.2.8, but the new campaigns still are not included :(

EDIT:
Compiling now. We'll see how it goes. Will it place a Kmenu entry for Kubuntu Gutsy when it's done?

---

### Post by Perfect Storm on 2008-03-17
If not, you can easely make one by yourself. The command is
```
wesnoth
```

---

### Post by anjilslaire on 2008-03-17
Alright, finally got things sorted :)

Compiling went fine, everything installed (with Kmenu even!) and the new campaigns were there. Of course, apt was complaining that there was a new version of wesnoth (1.2.8 ) to install, and it also was recommending wesnoth-data

What I did to resolve everything was:
1. made a backup of the campaign dir from /usr/share/games/wesnoth/data/campaigns/
2. Did a complete removal of everything wesnoth: config files, etc
3. Installed the 1.4.1 getdeb2 debs (that have the apt-version bug fixed)
At this point, Wesnoth 1.4 is installed & apt isn't complaining, so I moved to step:
4. Copied over the new campaigns from the backup of my compiled version into the install from the debs.

The result being Wesnoth 1.4 with all campaigns and apt is happy (and so am I) and I learned a bit more about compiling in the process.

@ Artificial Intelligence:
Yup, I know I could've made one myself, I was just wondering aloud. Thanks for the tip, anyway :)

---

### Post by eragon100 on 2008-03-17
Like I said above, safirst's deb also makes apt happy and has all of the new campagins. Just do the folowing if you don't want to run in any problems (you don't want 1.2.x campaigns to trie to start in 1.4, resulting in a crash)

1. remove /home/yourusername/.wesnoth

2. just double-click on the deb and install it normally.

---

### Post by safirst on 2008-03-17
I made some changes in my The Battle for Wesnoth deb.

**Changes:**
[LIST]
[*]Added menu entries
[/LIST]

Now it have all campaigns, working addons and menu items! :KS
New version can be found [here]("http://195.234.110.72/wesnoth_1.4-safirst2_i386.deb").

---

### Post by eragon100 on 2008-03-17
Thanks! :KS

---

### Post by anjilslaire on 2008-03-17
Yup, that'll help alot of people that dont generally do things the hard way, which I tend to do, so I can learn more ;) In my case, I had the compiled extra campaigns, just not in deb form, so I just dropped them in manually.

Good job safirst!

---

### Post by Mr. Svinlesha on 2008-03-20
I followed the instructions on [this page]("http://gaming.gwos.org/doku.php/guides:64bit:battle_for_wesnoth"):


I did'nt realize I had to uninstall my earlier version of Wesnoth first.

The game runs really well, but my "updater" tells me I have "unsupported dependencies".  When I try to update, the manager tells me I need to type "sudo apt-get install -f" in the terminal.  If I do that, the terminal tells me it wants to uninstall Wesnoth.

Synaptic tells me that I have a broken package, namely an older version of Wesnoth.

Should I go ahead and remove it?  If so, will I need to redo the installation process with Wesnoth 1.4?

Thanks in advance for the help/advice.

---

### Post by Perfect Storm on 2008-03-20
uninstall it. if you look in the source you downloaded the checkinstall have created a .deb - so no you don't need to recompile.

If synaptic want to make fuss either by downgrading etc. you can set the version number a little higher in checkinstall.

---

### Post by Mr. Svinlesha on 2008-03-20
Great.

Thanx.

---

