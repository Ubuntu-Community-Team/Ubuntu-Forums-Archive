---
title: "I tried Fedora..."
date: 2007-03-11
forum: Fedora/RedHat and derivatives
---

### Post by CocoAUS on 2007-03-11
Seeking a new distro, I played around with Fedora Core 6 and Fedora 7 (alpha).  These are my experiences:

[LIST=1]

[*]Live CD

The Live CD for Fedora was much better than Ubuntu's.  Ubuntu has always given me problems with KDE not loading, Gnome giving me errors, or simply freezing at the loading splash.  Fedora booted without a single problem, and did so a little bit faster (not much, but enough that I noticed).

[*]Defaults

Fedora's default look is much better than Ubuntu's.  This is just opinion, but I'm sure it's in the majority.  Fedora also included the Beagle extension in Firefox by default, which was a pleasant surprise.  Fedora, however, had an absolutely horrid default Gnome setup.  Really, I couldn't stand it.  And no Gconf tool is included to fix it.

Ubuntu to this day remains the ONLY distribution that doesn't properly configure my monitor.  I run at 1280x1024, Ubuntu, NOT 1024x780!  What's more, Ubuntu's xorg.conf display section is full of mostly useless values.  Fedora not only got my monitor working without any tinkering on my part, but it did it without all the extra junk in my xorg.conf.  C'mon, Ubuntu.  I'm sure the meta-packages for codecs and whatnot are great, but can you fix the basics please?

Ubuntu maps my ATi Remote Wonder's buttons quite well.  Volume, mute, mouse....  Fedora, on the other hand, did a horrible job with this, making the remote almost completely unusable.

Fedora uses su - to run terminal commands as root.  Ubuntu's sudo is much nicer.  sudo runs commands as the user, not root.  You can keep track of which user (on a multi-user system) is running commands this way, whereas su - shows all the commands as being done by root.  sudo also keeps you from having to hand out the root password to anyway.  For some reason, when I tried setting up a user as a sudoer in Fedora, it wouldn't let him sudo.  Not sure what the deal was there, but I assume it was an isolated occurrence.

[*]Aesthetics

Fedora has a better color scheme, login (gdm), and wallpaper, while Ubuntu has a better Gtk theme and icon set.  Again, opinion, but probably more common than not.  Brown is just not an attractive color.

[*]Other

Fedora provided me with a very sexy bootup.  GRUB was skinned, I was presented with a verbatim boot display.  The entire boot process was sexified, and I was able to view or hide the load process with a mouse click.

[*]Programs

Fedora included much more up-to-date programs, with the exception of Firefox 1.5 (2 was installable using a single command).  Fedora included Linux kernel 2.6.19, while Ubuntu Edgy still uses 2.6.17.  The Gaim package in Ubuntu is outdated as well.

As for options, Fedora did not include a Gconf tool.  This is extremely valuable for configuring Gnome, especially when Fedora comes with such a horrid Gnome desktop.  If Fedora is where people get their Gnome experience from, no WONDER they like KDE better!  Fedora also included AbiWord instead of OpenOffice, which is included in Ubuntu.  Opinions may vary here, but I believe (as do the majority of people I've talked to) that OpenOffice Writer is leaps and bounds ahead of AbiWord.

In general, the packages were much more solid.  Ubuntu has had problems with Ekiga not allowing people through the entire initial setup, but this was no problem in Fedora.  Ubuntu's tvtime package, ever since Dapper, has been defaulted to root ownership, making it impossible for the user to save channels, pictures settings, etc.  This is completely unacceptable and has been reported as a bug.  Fedora doesn't have this problem.  Ubuntu has also had problems with ndiswrapper and Azureus, yet both of these are wonderful in Fedora.  From my experience, Fedora's packages are current, stable, and properly configured.  The same can generally be said of Ubuntu, minus a few hiccups.

[*]Package managers

Yum is incredibly slow.  Just a check-update takes a long time.  I did full system updates on both Ubuntu and Fedora.  In Ubuntu, my system was fully updated in 45 minutes.  In Fedora, a yum update took 10 minutes.  ...TO FIGURE OUT WHAT PACKAGES TO INSTALL.  It took 10 minutes, and hadn't even downloaded anything yet!  It took a full 10 minutes to merely report back to me what it was THINKING about doing!  After telling it to actually please DO the update, I had to wait another hour and 10 minutes for the update to finish.  This is simply unacceptable.  Installing anything using yum takes an incredibly long time.  In fact, yum gave me a number of errors installing things like the nVidia driver.  I shouldn't have to worry about conflicts and dependencies when I'm using a package manager, and I never do when I use apt.

Yum is also a mess with its configuration file and various repo files.  Ubuntu's apt uses a single sources.list file, and this consists of essentially nothing more than just URIs for the repositories.

Perhaps yum isn't that bad.  Maybe Ubuntu just has me spoiled with apt.  I don't care.  Fedora needs to get its act together.

[*]Install

Fedora 7 installed from the Live CD in literally less then 7 minutes.  This is much faster than Ubuntu (which took ~35 minutes).  In all fairness to Ubuntu, Fedora 7 basically did nothing more than copy the CD image to the harddrive, while Ubuntu unpacked a large amount of data.  Still, Fedora 6 (not live) took a bit less time to install than did Ubuntu.  Fedora's install option is hidden in a menu on the Live CD, while Ubuntu includes an icon right on the desktop.  In general, once you get going, both installers are relatively similar.

I've got to mention this:  Both Fedora Core 6 and Fedora 7 included a license agreement on first boot.  This, to me, is absurd.  I had to read the thing just to make sure I was using something open source!  A license agreement is NOT the best greeting to give people.  Especially with how NOT newbie-friendly Fedora is, I would expect that the vast, vast, vast majority of Fedora users (and installers) know about Fedora being open source and without warranty.  The license agreement has nothing to offer other than aggravation.

[*]Community

Ubuntu is generally praised for its amazing community.  I don't want to bash anyone, but I've found that this is nothing more than hype.  Ubuntu's community is helpful in offering "how-to" help.  But for those of us who have moved beyond "How do I play DVDs?" and "How do I install Beryl?" type questions, the community doesn't offer much in the way of real troubleshooting support.  I understand why this is, but the point remains that the community offers very limited support.

The Ubuntu community is also exploding right now.  This makes it very difficult to find real answers or to help people.  Just take a stroll onto the #ubuntu IRC channel and you'll see how many people are around just looking for help!  What's more, most of the requests for help could be avoided if the user in question would simply Google it.  The Ubuntu community is also very immature at this point.  This is in no small way thanks to Digg.

The Ubuntu community is extremely disorganized.  Ubuntuforums.org has so many threads with questions and answers and troubleshooting spread all over, you can be sure the answer is in there somewhere at least in part, but you'll probably never find it.  Some of the more popular threads have hundreds of pages for anyone to sort through to find an answer that may or may not be there.

The Ubuntu community is also full of poor answers.  Screen resolution is a common issue, but the top Ubuntuforums Google results on the matter are WAY too confusing and bloated.  Following one of the guides for screen resolution might take 10 or 15 minutes if you know what you're doing.  However, using the real solution, I've fixed numerous resolution issues for various people in a minute or less.

The Ubuntu community is also very easily offended.  Even the moderators are quick to respond to any criticisms of Ubuntu or minority views.  I've seen comments from Ubuntu critics get edited by moderators for being offensive, etc, when little in their content could be considered offensive, yet that same moderator will respond with sarcasm and arrogance and let Ubuntu supporters respond to the critic with name-calling, insults, sarcasm, etc.  All-in-all, the community is great.  As long as you don't get involved in it.  Perhaps many of the Ubuntu laypeople problems are due to the explosive growth of Ubuntu, but that's not all of it.  And that doesn't account for the fascist moderators that are given power and authority in the community.

The Fedora community is different, though still has problems.  The users and developers both seem to be quite a bit more arrogant and condescending than the Ubuntu guys.  In general, however, the Fedora community seems to be a bit more knowledgeable.  This could be because the Ubuntu community is flooded with too many "newbies" that make the noob-to-nonnoob ratio so lopsided, thus drowning out the voices of the more knowledgeable, but regardless the reason, the outcome is what matters.

Fedora's guides were very poor in quality compared to even the average noobie's self-written Ubuntu guide.  This needs to change.  However, it seems that part of the problem with Fedora's guides is Fedora itself!  Adding repos, installing programs, configuring settings, using Beryl...all this is very complicated in Fedora.

Both communities need a makeover.  A more organized, yet perhaps less centralized approach to community support would be best.  Sites such as ubuntuguide.org are fantastic.  Unfortunately, the only site that seems to be included in such a statement is ubuntuguide.org itself.

[*]Finally

In short, I'll be sticking with Ubuntu.  There's a lot I wish would change about Ubuntu, and I think a lot of it has to do with Canonical's wanting Ubuntu to be a the user-friendly Windows replacement.  That's also where a lot of the GOOD stuff comes from, so it sort of a two-edged sword.  Fedora's live cd was fantastic, and I love having my kernel and packages up-to-date.  Fedora's aesthetic is pretty awesome, and it seems to pay more attention to what users actually want.  Ubuntu is better in general, but suffers due to Canonical's agenda.  What would be great is for someone to take the great things about Fedora--aesthetics, verbatim booting, up-to-date programs--and work them into an Ubuntu- (or Debian-) based distro.

[/LIST]

---

### Post by x64Jimbo on 2007-03-11
Interestingly, I don't think Fedora would even have a LiveCD if it weren't for Ubuntu's progress. They know they're losing ground (and users) to Ubuntu. I'm glad that Fedora's user experience has improved from the last time I used it (FC4) because that just means more good experiences for Linux newbies who choose a non-Ubuntu path.

---

### Post by esaym on 2007-03-11
Interesting.  I will be trying out fc6 soon.  Only because I need to help students at my local college install it :p

---

### Post by igknighted on 2007-03-12
Interesting... if you install via the DVD like I do you find a much different experience.  Gconf is there, OO.o is there, but no liveCD.  I have found that Fedora's gnome is more easy to skin than Ubuntu's.  No matter what I do, controls just don't change in Ubuntu like they should and Fedora's do.  That said, Fedora can be more work to set up.  This is a by product of a specific focus on up to date packages (as you noticed with Gaim and Kernel versions).  It is not a distro for those unfamiliar with linux, as life on the cutting edge sometimes requires some integral knowledge of the system to fix things, or set them up properly (case in point, ATI drivers on Fedora are much more difficult than Ubuntu, where I have never had issues until Fiesty).

Yum is always a constant catch for debian users.  They claim it is slow, and compared to apt it is.  However, RPMs are more complicated than DEBs so there is more for yum to take care of.  This primarily centers around the multi-arch nature of RPMs.  Sure, debian does a little multi arch stuff, but when was the last package for Debian you saw that differentiated between i386 i586 and i686?  Fedora handles all these architectures via yum as well, hence some of the slowness.  Overall, I like yum.  My one complaint is the lack of  a "pretend" option, although I could just be ignorant and missing it.  I find that if you don't tell it to assume yes it works like this some times, but with Gentoo's emerge you can tell it to "pretend" and it assembles all the dependencies to show you what would happen if you did the install and then quits out, so you can determine if you want to actually do the install.  If yum had this it would be the perfect RPM manager, IMO.

Sidenote, post #1000... w00t
</sidenote>

---

### Post by x64Jimbo on 2007-03-12
I've never seen a package for debian that differentiated between different instruction sets, but I have seen repositories that cater specifically to different architectures, which is basically the same thing, but implemented differently.

---

### Post by igknighted on 2007-03-12
> **x64Jimbo said:**
> I've never seen a package for debian that differentiated between different instruction sets, but I have seen repositories that cater specifically to different architectures, which is basically the same thing, but implemented differently.

I suppose, but there is a value and a reason for attempting to install packages of various architectures on a system (say if 64bit is unavailable).  Also, Ubuntu simply uses i386 for the x86 architecture.  Most users probably have i686 systems and could take advantage of i686 packages and the associated (sometimes imperceptible) speed increase with appropriately compiled packages.  As stated above, Fedora likes to give options as it caters to a user more familiar with linux than Ubuntu does, so it is not a knock on either, but rather illustrating the different goals.  If you asked me to choose between yum and apt, I couldn't, I like them each for their own reasons (although portage/emerge >> all others).

---

### Post by rennen01 on 2007-03-12
Could installing FC6 harm the stability of my Ubuntu? Assuming the the FC6 is isntalled properly?

I am planning on installing FC6 tomorrow night just to test it.  I will do a backup first though of my Ubuntu data :)

---

### Post by CocoAUS on 2007-03-12
Ubuntu shouldn't be affected by your Fedora install, no.

---

### Post by x64Jimbo on 2007-03-12
Well, that really depends on whether FC6's GRUB install properly detects your Ubuntu installation. It won't harm your data if you install on a different partition, but you could certainly lose your ability to boot it if FC6 fails to put the correct entries into the menu.lst file. Just make sure that you back up your current menu.lst file and then copy over the sections about Ubuntu if the FC6 install neglects to add them itself. This is entirely possible, as I have seen the GRUB installer completely ignore my dual booted Windows XP installation whenever a kernel upgrade is processed and the menu.lst file needs to be updated accordingly. I always have to add WinXP back in manually.

---

### Post by Atreus12 on 2007-03-12
I'll second the 'yum being slow' comment. I installed FC6, used if for about 2 days and gave up. Yum was so rediculously slow. I figured it was just my computer though. Is this normal?

Updates took ages and ages.

---

### Post by x64Jimbo on 2007-03-12
> **Atreus12 said:**
> I'll second the 'yum being slow' comment. I installed FC6, used if for about 2 days and gave up. Yum was so rediculously slow. I figured it was just my computer though. Is this normal?

Updates took ages and ages.
Depends on your definition of Normal. Normal as in "par for the course," yes. Normal as in "what you should expect," no. Yum should not be as slow as it is. You shouldn't have to refresh your repositories every time you want to do an operation, for starters.

---

### Post by igknighted on 2007-03-12
> **x64Jimbo said:**
> Depends on your definition of Normal. Normal as in "par for the course," yes. Normal as in "what you should expect," no. Yum should not be as slow as it is. You shouldn't have to refresh your repositories every time you want to do an operation, for starters.

Then tell it not to.  You can tell it to use the cached repository lists if you want.  You can even alias the yum install command to default to this.  I forget the exact flag, but I think its yum -c install or yum -C install.  Also note that if you yum search as a user it wont update, but if you do it as root it will.  Again, tell it not to with the proper flag if you don't want that.  Type "yum --help" for more info on what yum can do.

---

### Post by x64Jimbo on 2007-03-15
Shouldn't the efficient methods of installing software be the defaults? I don't think there should have to be a separate command switch to make sure that it installs from a cached list of software rather than the online version. Even then, however... Why does my aptitude update take considerably less time than yum's update?

---

### Post by jinx099 on 2007-03-15
the grub issue is easily fixed with the grub shell.  You can repair from a LiveCD, or from one of your installed OSes.  For example, if you are dual booting FC6 on sda1 and Ubuntu on sda2, and you wanted to restore Ubuntu's boot loader that FC6 wiped out, you would just run:

```

sudo grub

grub> root(hd0,1)
grub> setup(hd0)

```

The weird thing in FC6 is the grub shell doesn't tab-complete.  In other distros you can tab to see all the different partitions and their info.

---

### Post by CocoAUS on 2007-03-16
I ended up installing Fedora again for a bit.  Basically, Ubuntu's Gnome panel crashed and killed the whole Gnome install, and then did it again when I reinstalled.  The Ubuntu guys know about it, but the fix is only in Feisty, not Edgy.  Anyway, Fedora was incredibly slow updating and installing everything.  I keep hearing people make excuses for yum and say that people shouldn't complain about it (seems to be Fedora's motto--"don't complain, it's just different").  If you go on the Fedora forums, they'll actually tell you NOT to update your entire system, or even too many programs at once!  Seriously, no joke.  They know it'll mess up your system.  Not only that, but just trying to install Epiphany (Gnome's native web browser), I had dependency problems!  I shouldn't EVER have to worry about dependencies when installing software using a package manager.  What's the point of a package manager that doesn't manage packages?  And then Fedora is missing some key things, like a number of fonts, and calendar, contacts, and notes in Evolution.

So, I used Fedora to download and burn Herd 5.  Much happier now.  :)

---

### Post by igknighted on 2007-03-16
> **x64Jimbo said:**
> Shouldn't the efficient methods of installing software be the defaults? I don't think there should have to be a separate command switch to make sure that it installs from a cached list of software rather than the online version. Even then, however... Why does my aptitude update take considerably less time than yum's update?

As for the speed of the update, I have two theories.  #1... Fedora updates software in repo's regularly while Ubuntu does not (bleeding edge vs. stability).  Any change made has to be downloaded in yum update, therefor, you download much more in Fedora.  #2... Fedora's repos are not set up in a way that is easy to search/update (many packages are duplicated in Core/Extras).  This should be improved in Fedora 7.

See my above reasoning on the frequent update of packages.  In Ubuntu think how often the kernel is upgraded... maybe once over the life of the release.  Since FC6 has been out I have upgraded to several 2.6.18 kernels and have now had two 2.6.19 kernels as well.  This is but one example.  Since the packages change so often, it is a good idea to always update before an install.  As a result, yum defaults to updating.  If you feel comfortable not updating this is your prerogative, just add -c.

---

### Post by CocoAUS on 2007-03-16
Hah!  My Fedora update involved about 245 megs.  My Ubuntu update was over 600, and STILL got done in a little over half the time.  yum is just slow.

---

### Post by karellen on 2007-03-16
> **CocoAUS said:**
> Hah!  My Fedora update involved about 245 megs.  My Ubuntu update was over 600, and STILL got done in a little over half the time.  yum is just slow.

yes, yum it's the main reason that keeps me from using fedora. besides .rpm and the smaller community compared to ubuntu ;)

---

### Post by igknighted on 2007-03-16
I don't understand how the speed of a package manager is everyones top complaint about a distro.  I mean, you use it so rarely once the system is set up.  I can understand it as an annoyance, but as a reason to avoid a distro?

^^^ Note, this is apart from my defense of Fedora... I really just want to know why this is so big a deal to people

---

### Post by CocoAUS on 2007-03-16
yum's (lack of) speed wouldn't be enough on its own to keep me from using Fedora.  But it is more than an annoyance; it is an EXTREME annoyance, at least.  The same as if it took me 15 seconds to save a document in OpenOffice while Word did it instantly.  The same as if it took me 5 minutes to change the icon theme in Fedora while Ubuntu did so almost instantly.  Would you like to compile your entire operating system from source?  Why not?  Why aren't you using Gentoo?  After all, it just takes longer to install things...a small price to pay for having up-to-date software of any kind you'd like, right?

Speed is a big deal.  If it were only slightly slower, it would be less of an issue.  With Fedora, the slowness of yum only adds to the other frustrations.

By the way, yum also has problems resolving dependencies.  Which sucks when you wait 3 or 4 minutes for yum just to tell you, "Hey, I can't actually do anything.  Sorry to keep you waiting."

---

### Post by igknighted on 2007-03-16
> **CocoAUS said:**
> yum's (lack of) speed wouldn't be enough on its own to keep me from using Fedora.  But it is more than an annoyance; it is an EXTREME annoyance, at least.  The same as if it took me 15 seconds to save a document in OpenOffice while Word did it instantly.  The same as if it took me 5 minutes to change the icon theme in Fedora while Ubuntu did so almost instantly.  Would you like to compile your entire operating system from source?  Why not?  Why aren't you using Gentoo?  After all, it just takes longer to install things...a small price to pay for having up-to-date software of any kind you'd like, right?

Speed is a big deal.  If it were only slightly slower, it would be less of an issue.  With Fedora, the slowness of yum only adds to the other frustrations.

By the way, yum also has problems resolving dependencies.  Which sucks when you wait 3 or 4 minutes for yum just to tell you, "Hey, I can't actually do anything.  Sorry to keep you waiting."

:) I do use Gentoo, and my Ubuntu has a custom compiled kernel.  I think the saving a document comparison is unfair.  I write those all the time, and saving them slower would cut into productivity (FWIW, I find OO.o painfully slow, and if gnumeric had the functions I need I would ditch OO.o).  But a package manager?  How often is it used?  I use it to configure when I install, and then it takes care of updates every night at 3am while I sleep.  I never see it.  As long as its done by noon the next day I could care less.

---

### Post by Genecks on 2007-03-18
I started at Knoppix, went to Ubuntu, got sick of Ubuntu, and went to Fedora Core. However, after noticing all the annoying things I had to deal with in Fedora Core and the annoying loading of the operating system and much, much more, I decided to move back to Ubuntu.

I don't plan on going back to Fedora Core anytime soon. I personally like Xubuntu because it has a mouse. That's all I need in an operating system: A mouse. Not something with an x-y coordinate movement, but a picture of a mouse when I'm loading the operating system.

But... maybe it was this: [http://video.google.com/videoplay?docid=-6104490811311898236](http://video.google.com/videoplay?docid=-6104490811311898236)

---

### Post by CocoAUS on 2007-03-19
@Genecks

Wow, those kids bother me so much.  From the lameness of the video, to the mundane topic, to the pointless and unintelligent explanations they give, to the mispronunciation of "Ubuntu"...

---

### Post by x64Jimbo on 2007-03-20
> **CocoAUS said:**
> @Genecks

Wow, those kids bother me so much.  From the lameness of the video, to the mundane topic, to the pointless and unintelligent explanations they give, to the mispronunciation of "Ubuntu"...
Agreed on all counts. I mean, what is this "Linux will ensure you never get a date again - the ladies don't like Linux" crap? Apparently, they've never met my ex or current girlfriends, both of which find it simple and intuitive, and they're not even techie types. 
These guys are using a WAY outdated version of Ubuntu too.

---

### Post by civilwarlord on 2007-03-20
To all you people whining about yum being slow, how about installing the latest version? It's much more faster than the old version.  Unless that would give you people one less thing to complain about.

---

### Post by CocoAUS on 2007-03-21
@civilwarlord

Tried the most current yum (as available in F7).  Um...being faster than it was (if it is faster) doesn't mean it's up to par.  A slug might be faster than a snail, but it's still far from fast.

Why do Fedora fans always get so defensive?

---

### Post by civilwarlord on 2007-03-21
> **CocoAUS said:**
> @civilwarlord

Tried the most current yum (as available in F7).  Um...being faster than it was (if it is faster) doesn't mean it's up to par.  A slug might be faster than a snail, but it's still far from fast.

Why do Fedora fans always get so defensive?

It's ubuntu fanboys that get defensive when you say anything remotely bad about their precious distro.  Maybe if you had a fast computer, yum would run better.

---

### Post by Lord Illidan on 2007-03-21
> **x64Jimbo said:**
> Agreed on all counts. I mean, what is this "Linux will ensure you never get a date again - the ladies don't like Linux" crap? Apparently, they've never met my ex or current girlfriends, both of which find it simple and intuitive, and they're not even techie types. 
These guys are using a WAY outdated version of Ubuntu too.

Exactly. My sister uses Linux, she likes it, and yesterday I had an interesting conversation about Linux with two girls, none of whom is a techie type.

Regarding the OP, I also tried FC6, and while it was an experience, I still preferred Zenwalk Linux or Ubuntu for that matter. I didn't test the live cd, but Ubuntu's livecd is a bit slow, that's sure.
> [LIST=1]
[*]Defaults

Fedora's default look is much better than Ubuntu's. This is just opinion, but I'm sure it's in the majority. Fedora also included the Beagle extension in Firefox by default, which was a pleasant surprise. Fedora, however, had an absolutely horrid default Gnome setup. Really, I couldn't stand it. And no Gconf tool is included to fix it.

Ubuntu to this day remains the ONLY distribution that doesn't properly configure my monitor. I run at 1280x1024, Ubuntu, NOT 1024x780! What's more, Ubuntu's xorg.conf display section is full of mostly useless values. Fedora not only got my monitor working without any tinkering on my part, but it did it without all the extra junk in my xorg.conf. C'mon, Ubuntu. I'm sure the meta-packages for codecs and whatnot are great, but can you fix the basics please?

Ubuntu maps my ATi Remote Wonder's buttons quite well. Volume, mute, mouse.... Fedora, on the other hand, did a horrible job with this, making the remote almost completely unusable.

Fedora uses su - to run terminal commands as root. Ubuntu's sudo is much nicer. sudo runs commands as the user, not root. You can keep track of which user (on a multi-user system) is running commands this way, whereas su - shows all the commands as being done by root. sudo also keeps you from having to hand out the root password to anyway. For some reason, when I tried setting up a user as a sudoer in Fedora, it wouldn't let him sudo. Not sure what the deal was there, but I assume it was an isolated occurrence.[/LIST]Ubuntu and Fedora worked perfectly with all my hardware, but then I have an NVIDIA card. I concur with you about sudo...it felt strange to be working as root. Regarding the default look, that's just a matter of tase.
> Aesthetics

Fedora has a better color scheme, login (gdm), and wallpaper, while Ubuntu has a better Gtk theme and icon set. Again, opinion, but probably more common than not. Brown is just not an attractive color.
Here, it is a matter of opinion. However, I think that the consensus in Ubuntu is that the colour set is moving towards a more orangey look, which I like very much. Again, it is easy to change.

> 
Other
Fedora provided me with a very sexy bootup. GRUB was skinned, I was presented with a verbatim boot display. The entire boot process was sexified, and I was able to view or hide the load process with a mouse click.AFAIK, the Ubuntu's GRUB is not skinned because of reported problems with GRUB on some machines where it was skinned, otherwise I am sure they would try and skin it..

> 
Programs

Fedora included much more up-to-date programs, with the exception of Firefox 1.5 (2 was installable using a single command). Fedora included Linux kernel 2.6.19, while Ubuntu Edgy still uses 2.6.17. The Gaim package in Ubuntu is outdated as well. 

As for options, Fedora did not include a Gconf tool. This is extremely valuable for configuring Gnome, especially when Fedora comes with such a horrid Gnome desktop. If Fedora is where people get their Gnome experience from, no WONDER they like KDE better! Fedora also included AbiWord instead of OpenOffice, which is included in Ubuntu. Opinions may vary here, but I believe (as do the majority of people I've talked to) that OpenOffice Writer is leaps and bounds ahead of AbiWord.In general, the packages were much more solid. 

Ubuntu has had problems with Ekiga not allowing people through the entire initial setup, but this was no problem in Fedora. Ubuntu's tvtime package, ever since Dapper, has been defaulted to root ownership, making it impossible for the user to save channels, pictures settings, etc. This is completely unacceptable and has been reported as a bug. Fedora doesn't have this problem. Ubuntu has also had problems with ndiswrapper and Azureus, yet both of these are wonderful in Fedora. From my experience, Fedora's packages are current, stable, and properly configured. The same can generally be said of Ubuntu, minus a few hiccups.
Hmm, Azureus works without probs here, and as for packages being out of date, it's not too important to me...

> 
Package managers

Yum is incredibly slow. Just a check-update takes a long time. I did full system updates on both Ubuntu and Fedora. In Ubuntu, my system was fully updated in 45 minutes. In Fedora, a yum update took 10 minutes. ...TO FIGURE OUT WHAT PACKAGES TO INSTALL. It took 10 minutes, and hadn't even downloaded anything yet! It took a full 10 minutes to merely report back to me what it was THINKING about doing! After telling it to actually please DO the update, I had to wait another hour and 10 minutes for the update to finish. This is simply unacceptable. Installing anything using yum takes an incredibly long time. In fact, yum gave me a number of errors installing things like the nVidia driver. I shouldn't have to worry about conflicts and dependencies when I'm using a package manager, and I never do when I use apt.

Yum is also a mess with its configuration file and various repo files. Ubuntu's apt uses a single sources.list file, and this consists of essentially nothing more than just URIs for the repositories.

Perhaps yum isn't that bad.  Maybe Ubuntu just has me spoiled with apt.  I don't care.  Fedora needs to get its act together.

I used Smart in Fedora...but you're right, the default package manager is excruciatingly slow, and the way of installing repos is much more complex than in Ubuntu...

But this is IMHO the more important part of the OS...leave out the iconset or gdm theme, they can be changed very easily. But problems with packagemanagers are quite serious imho. 

> Community

Ubuntu is generally praised for its amazing community. I don't want to bash anyone, but I've found that this is nothing more than hype. Ubuntu's community is helpful in offering "how-to" help. But for those of us who have moved beyond "How do I play DVDs?" and "How do I install Beryl?" type questions, the community doesn't offer much in the way of real troubleshooting support. I understand why this is, but the point remains that the community offers very limited support. Aye, I agree with you, but what can we do here? The problem is the noobs:experts ratio here...and the fact that Ubuntu is growing very fast.

---

### Post by arbulus on 2007-03-21
My first experience with Linux was an Ubuntu live CD, but never got around to installing it.  I thought it was an incredible system.  Later, I was given a server as a gift that had 4 HDDs, and I wanted to use it as my learning tool, but needed a distro to install on a RAID, so I tried Fedora Core 5.  While the install went great, it seemed impossible to configure the services I wanted to use.  Samba, NFS, CUPS, SSH:  all of them were impossible to set up.  I followed instructions that I found to the letter, with no success.  So finally, I gave up.  I abandoned the idea of RAID and just installed Ubuntu on one drive.  I found it incredibly easy to use and configure.  I was able to set up all the services I wanted easily and quickly, with little to no hastle.  As time has passed and I've become more knowledgeable with Linux systems, i thought that I would give Fedora Core 6 a try again, believing that my inability to configure it was due to my lack of experience with Linux.  No dice.  No more luck than before.  

It was at this time that I discovered that Ubuntu's alternate install disc allowed for RAID installations and had a go at it.  It was brilliant.  Not one problem.  I had and new install on a RAID 0 with Ubuntu and all of my network services configured in less than 2 hours, while doing the exact same thing with Fedora took me over 2 days, with no success.  

So my conclusion was that Fedora is by no means a distro for a new comer to Linux.  It may be usable and configurable to someone who has many years of experience in the Linux world, but I don't know.

---

### Post by x64Jimbo on 2007-03-22
For a rock-solid server distro, I go with Debian, which is the basis for Ubuntu. If you go with the stable branch of Debian, you will only get the most critical security updates, but other than that, you don't have to worry about updates breaking stuff like sometimes happens in Ubuntu due to it being based on a non-stable version of Debian. 
I have a friend who has been using FC for his home-grown LAMP server since core 4, and he has been loving it since day 1. It's gotta be about user preference. I love aptitude, and he is obsessed with Yum. The most important aspect of all this is that we are both using the Linux kernel, and neither of us has paid a single cent to MS in years, and we both plan to keep it that way.

---

### Post by CocoAUS on 2007-03-26
@civilwarlord

Wow, you need to get a grip.  The Ubuntuforums mods tend to, yes, get very defensive when you criticize Ubuntu.  But from my experience, the users are much better.

And my computer is plenty fast.  Why can't you guys just admit that yum is slow?  Denial.

---

### Post by igknighted on 2007-03-26
> **CocoAUS said:**
> @civilwarlord

Wow, you need to get a grip.  The Ubuntuforums mods tend to, yes, get very defensive when you criticize Ubuntu.  But from my experience, the users are much better.

And my computer is plenty fast.  Why can't you guys just admit that yum is slow?  Denial.

YUM IS SLOWER THAN APT!!!  ZOMG!!!

read my comments in your other thread.

---

### Post by x64Jimbo on 2007-03-26
Whoa there, people. Let's just use whatever distro we prefer and stop bashing each other's decisions. Of course we prefer our own choice, or we wouldn't have made it in the first place. Linux needs infighting like a gaping wound in the head.

---

