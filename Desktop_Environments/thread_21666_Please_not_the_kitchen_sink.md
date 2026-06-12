---
title: "Please not the kitchen sink"
date: 2005-03-23
forum: Desktop Environments
---

### Post by aramazan on 2005-03-23
I've observed and become concerned that when it comes to what packages to include in the CD, many of us usually can't resist the temptation and tend to wish for a personally pleasing distro, rather than a distro for the world at large. IMHO a good balance can be struck with some fundamental rules more or less along the lines of the following (just a wish-list :)

1. No package on the CD is left uninstalled at HDD installs. *All* of them installed without exception and without consulting the user. This would've been bloat, had package selection taken lightly. Otherwise this is a self-challenge to select the apps in such a perfect way that installing the whole CD wouldn't create bloat (which automatically translates into optimal package portfolio).  HDD is omittably cheap compared to the functionality gained, and if this approach doesn't (shouldn't) result in a "litter-rich" environment, then it ought to be a "real-rich" environment. So, it would both promote ease of installation, and provide a rich environment out of the box, and encourage serious self-control while including a package into the CD. Already Hoary-Preview didn't ask me which packages to install. I hope it has installed everything, and I hope this good trend goes on. This alone, I believe, may increase end user satisfaction tremendously (in terms of both functionality and quality).

2. No functional duplication. One and only one package, the best of the breed, for each genre. Extreme pessimism adopted for any functionality duplication offer, even if it's a partial duplication, and unavoidable exceptions (like Konqueror & Firefox) are accepted only with concensus, as opposed to majority vote.

3. More is not better, but more * good = better. That is, in (the very unlikely) case that there's not enough packages meeting stringent measures to fill the CD, then I believe it's better to ship it underfilled with golden packages than filled with gold mixed with litter. Duplication of functionality confuses, and unmet quality expectation frustrates a newbie. Whatever is shipped on the CD, IMHO it should be functionally non-duplicated, and be the very best of its kind. And I'm assured that even with stringent requirements, there will still be space shortage on the CD in quite a short time.

4. Assuming this is a client grade end-user distro for everyone. Neither server-grade, nor developer-grade, nor another vertical genre packages are appropriate on the CD. A point not to forget is that the repository is already there, a few clicks away. What is included in the CD should represent what packages would've been downloaded most from the repositories. This will also relieve considerable burden off the mirrors upon each new release.

5. That said, any Windows user tipping his toe into Kubuntu shouldn't find it lacking in terms of functionality. In this regard I would suggest (for Hoary) preparing a summary listing of top 50 select apps left out of the CD for various reasons[*] and spread it around as wide as possible (desktop shortcut, ubuntulinux.org, various forums & media outlets, etc.) Particularly important ones are Java, Flash, RealPlayer, some closed source drivers, proprietary codecs, some non-free packages, etc. Some might even miss Opera and AcrobatReader. While we're on it, I guess some categorized meta-packages might be a good idea. For instance everything regarding each and every language, including the kitchen sink, could be consolidated as relevant meta-packages so all one needs to do is installing turkish-all package to get whatever there is to install regarding the Turkish language. Other excluded apps could be likewise consolidated. E.g. web-extras-all would install Java, Flash, Real. Likewise multimedia-extras-all would install all the codecs, libdvdcss, etc. In this way, aforementioned top critical 50 packages (except i18n) could be reduced to a handful meta packages, and it would be quite newbie friendly. Even an "extras-all" package is conceivable which installs all these 50 packages over the 'net. Also, installer might offer a list containing the selected language (as opt-out: preselected) along with these meta packages (as opt-in: not selected) and the user could choose to install them over the 'net during the installation.
([*] Being second-best to some app already on the CD or due to license issues.)

Curbing my temptation, I won't suggest (for Hoary) a complementary "Kubuntu+" CD crammed with such apps (also including i18n/l10n packages) as far as it's not illegal to do so. Such a CD doesn't necessarily need to be released by Kubuntu team. Provided that any 3rd party prepares it, users would jump onto it, I guess. :)

BTW I would very much like to see popularity-contest in the "base" section, instead of the "misc" section. And an opt-out (even "struggle-out":) scheme with less frequent scheduling, instead of Debian's opt-in scheme with weekly run. Perhaps running monthly or bi-monthly (nevertheless running for sure) might be more suitable when it's made opt-out. I guess this is probably the absolute bare minimum contribution a user could do, so no Kubuntu user would object such a minimal "ubuntu" on their part, I hope. (As a one-CD distro, I think popularity-contest results are much more important for Kubuntu than it is for Debian.)

Most of these suggestions are too late for Hoary deadline, I appreciate, and I'm not generally targeting Hoary anyway. But at least I would particularly plead (for Hoary) that *please* no (L)AMP, no ClamAV, no other server class packages whatsoever. Samba is conceivable though (for 2-way file sharing with Windows). Also a means for Linux-Linux file sharing (ssh+fish?). Maybe a simple iptables GUI front-end for port blocking and "internet sharing" but no elaborate firewall package. No KDevelop, no Cervisia, no KBabel, no i18n/l10n (perhaps excepting the most used 3 languages among the user base). Only one of either Kate (my preference) or KWrite but no other GUI text editor, only one of either nano or pico but no other console text editor, including vi and emacs. No "mee too" package but only one best/golden app of each kind: I mean, best for its prospective user base, not best for *me* or *you*. That's why I promote nano/pico over vi/emacs - let alone their bulk. Also, we are really a fractional minority (I hope :) compared to Kubuntu's vast prospective user base. The correct approach is, majority is served by the CD, while minority installs their "vertical" apps over the 'net. So, no vi but Kivio, no KDevelop but kdeedu. Well, I guess everyone knows what I mean.

Last, but not the least, Kubuntu is a long sought for distro. Thanks to everyone who made it happen.

---

### Post by Buffalo Soldier on 2005-03-23
[QUOTE=aramazan]I've observed and become concerned that when it comes to what packages to include in the CD, many of us usually can't resist the temptation and tend to wish for a personally pleasing distro, rather than a distro for the world at large. IMHO a good balance can be struck with some fundamental rules more or less along the lines of the following (just a wish-list :)..[/QUOTE]A sensible approach and a sensible KDE user... I wish all were like you. (yes, there are insensible GNOME users too :p)

---

### Post by moopere on 2005-03-25
I'm particularly impressed with the idea of including only the current 'best of breed' in Kubuntu.  

Ubuntu with Gnome is currently very much streamlined with this type of idea. Have a look at a lot of the traffic in the constant gnome/KDE battlegrounds,  these days comments like 'crowded' and 'too many apps that do the same thing' are common amoungst the threads as a negative against KDE.

Nothing wrong with choice of course, everyone has their favourite app, and these should, by and large, be available in universe, but please, lets not clutter kubuntu with every app possibly available for kde.

Case in point...multimedia, perhaps I'm missing something important, but whats with amarok, kaffeine, juk??   All slightly different sure, but needlessly confusing.  Want streaming or other audio under Gnome/Ubuntu...use Rhythmbox, its that easy, under Kubuntu you _might_ want amarok _or_ kaffeine _or_ juk, depending on the type of audio.

Regards,
Craig

---

### Post by aramazan on 2005-03-27
Re: "lets not clutter kubuntu with every app possibly available for kde."

And this clutter not only confuses the user, but also wastes precious CD space that could otherwise be used for much needed packages. Duplicate functionality leads to a complex, yet poor environment, where functionality span is relatively narrower and average quality of applications is relatively lower. In contrast, non-duplicate functionality leads to simpler, yet richer environment.

-------

Re: "whats with amarok, kaffeine, juk??"

I'm not much into multimedia and probably any would satisfy my needs (std formats) anyway. But I'm under the impression that mplayer is one of the best, and xine (on which most players depend) comes next to my mind. I would suggest a final evaluation with *all* their plugins included, select the best to ship in the CD (in case it's xine, I believe it should be shipped along with a pretty front end like kaffeine), and try to include as much of those plugins (used while benchmarking) as possible into the CD, and put other plugins to universe/multiverse, and include them in the "multimedia-extras-all" metapackage.

-------

Re: No package on the CD is left uninstalled at HDD installs.

Another reason is the live-CD. Eventually "live" and "installable" branches would (I hope) merge, (a la Kanotix or Mepis). So, this would also ensure seamless and intuitive WYSIWYG relation between live and installed flavors.

Also some afterthought additions:

6. No NIH (Not Invented Here) syndrome:

6a) GNOME. There are killer Gnome applications that need to be included in the CD. Take Gimp, for example. It's a direct Photoshop rival. There are a lot of people who are interested in serious graphics manipulation. Many Gnome libraries are already included in Kubuntu (which also establishes a Gnome lib base which can be shared by many Gnome apps). So I assume exclusion of Gimp is not due to NIH, but due to mere space constraints. The space saved with mutually excluding duplication and completely excluding server/developer/vertical class packages could very well be used for really needed ones such as Gimp. Gimp is a killer app which delivers much more added value to Kubuntu than needlessly confusing and space hogging duplication.

PS: Not that I'm a serious Gimp user. Much less am I a Gnome user. But there's a fine line between desktop environments and applications. My users (and serving them, so do I) prefer KDE as a desktop, but that's it. No particular preferences regarding the apps. Of course a KDE app is much more seamlessly integrated into KDE, and it's quite a serious asset. But then again, none of my users (neither I) would hesitate to use a Gnome app if it's the best one. The important conclusion I aim to draw is that neither KDE nor GNOME based distros should refrain from including the "other's" apps and libs for best user experience. Sticking to an all-KDE or all-GNOME strategy leads to a suboptimal distro at best, a fanatic and niche distro at worst.

6b) CSS. Our short term goal should be, IMHO, getting as much user base as possible. With this I'm referring to the 100s of millions of non-Linux users out there. I feel confident that Kubuntu will be one of the top Linux players in short time, but this is not enough. Everything is almost ready[*] for winning the grand masses out there, and we are in no position to adopt a picky stance at this point in time. I believe we should swallow our prides for the time being and play the game according to the marketing rules, and include whatever piece of software in the CD that would appeal to the masses, as long as it's not illegal to do so. To the extent that we can even maintain a small archive for packages not accepted to multiverse (if there's any such rejected ones). We can even go to some CSS vendors, should there be a need, and humbly request permission to include their packages in the CD. Naturally, this suggests also enabling universe and multiverse (and may be a Kubuntu-specific "extraverse") in default installation.

[*] Such as consolidated, centralized, and all-encompassing system management, or click-to-install-and-run applications (a la Linspire), etc. for which I will make some suggestions once the Hoary rush is over.

7. Non-us packages. I'm not quite sure how to approach this: At one hand US users are probably the biggest user base of Kubuntu, OTOH it's unnecessary to bog down a world-wide distro with legal requirements specific to any particular country. My resolution is that it would be suitable to prepare a master CD which liberally includes packages from non-us, and then cripple that CD (excluding the non-us packages) and thus produce a Kubuntu/non-us derivation to be distributed in the US. Otherwise, excluding the non-us packages from the main distro would seriously axe its sex-appeal down.

8. Other non-free packages. I believe the worthwhile ones should be included in the CD as long as it's possible. Talking to CSS vendors and getting into special agreements with them is also conceivable. Now, I'm not trying to bastardize OSS in general and Kubuntu in particular. I'm just suggesting to play according to marketing rules in order to get a strong enough foot-hold, before earning the m^Hright to impose our own perspectives to the IT world at large.

Let's look at Firefox and draw lessons from them. I believe we should be most flexible in satisfying user demands.

-------

Re: Summary listing of top critical 50 off-CD packages.

A typical user would install Kubuntu via the least resistance path (accepting/following defaults all the way), and then... what then? In Windows he was feeling at home, knew his ways around, what to find where and how to install, how to shape his system according to his needs. Now with Kubuntu what is he going to do? He desparately needs some quick and practical short cuts. We should proactively provide him with everything he would ask around anyway. Top of the list is the questions regarding how to access to a particular functionality. These questions can be divided to several categories:
a. What is the name of the app that does what I was doing with "foo" in Windows?
b. Where can find the program "foo"?
c. How do I install and set it up?

[a] is related to familiarity with the solutions base, and it's one of the biggest (and cheapest to overcome) blockers for newbies. The demand is there, the solutions are there, but package names are all cryptic to a newbie. In the windows world when you say "ACDSee", he instantly knows what you're talking about (Like you would recognize the KView/GQview). When he needs some particular functionality (say CD burning) several names would already come to his mind. But when he switches the platform, he becomes completely clueless. Problem is there, solution is there, but due to cluelessness, Linux becomes "difficult", cold and alien as he perceives it. Remedy is, proactively supplying him with a quick list of what is what, where to find, and how to get them all up and running. This list should cover *all* the solutions base Linux can cover: main, universe, multiverse, as well as OSS/CSS packages out of Kubuntu's domain, even commercial ones. The keyword is "demand" here. If there is demand in the user domain for a specific functionality, then I believe proper information should be given about it. Since this would be an immediate-critical list of select top 50 applications, no pretty multi-page html categorization or search etc. should be needed. Just a plain list of all in one place, summarizing what and where it is, and how to get and run it. (May be another -similar- list summarizing the GUI packages already installed)

---

### Post by bailout on 2005-03-27
[QUOTE=aramazan] unavoidable exceptions (like Konqueror & Firefox) [/QUOTE]

I don't know whether I am mis-reading the above but Firefox should not be installed by default. Konq is a great browser that I much prefer to ff. As an Opera user I just accept that I will have to install Opera myself. Firefox will be easy to install from deps by those who want it and there is no need for it in kubuntu when kde already has konq.

---

### Post by aramazan on 2005-03-27
[QUOTE=bailout]Konq is a great browser that I much prefer to ff.[/QUOTE]
Exactly. However, while I'm also using Konqueror exclusively, there are 3 resons why I consider Firefox as "unavoidable":

1. User domain wants it: As evident from download counts, browser statistics, and my personal observations. Even though Konqueror is much more seamlessly integrated into KDE and feels so smooth, for some reason I don't know, my users still prefer Firefox on Linux, and they're obviously very pleased and satisfied with it. For me there's no doubt about it: They want Firefox (they ask for it if I only install Konqueror and Mozilla).

2. It is one of the main bridges from Windows to Linux: In migrating, it's important to switch first to dual platform (bridge) applications as much as possible, (long) before the actual migration itself. While this is primarily a strategy for corporate/departmental migrations (who have an admin, anyway, to take care of Firefox post-installations), it is also important for individuals. I guess there's a high probability of a "potential switcher" already using (at least having been used) Firefox. So, having Firefox out of the box would add to smoothing out the change-shock and hence benefit Kubuntu. (BTW, more of the same applies to OO.o, and also this is why Opera and AcrobatReader should be included in the "50 top critical off-CD apps" list.)

3. Due to soon to be vanished IE domination (or IE-only webmasters?) there may still be glitches in some sites. Having an alternative-engine browser is very handy in such situations. I normally use Konq, but if I hit a site with rendering or JScript problems, probably Firefox would work well. And vice versa. (I think having both KHTML and Gecko at hand is actually an asset for KDE.)

---

### Post by dermotti on 2005-03-27
I couldnt use paypal with konqueror aomngst some othe rsites requiring you to "login" so i have to use firefox

---

### Post by Julius on 2005-03-28
What I don't like about konqueror is that it is too much integrated into KDE, and it's more than just a web browser. Konqueror is OK, I wouldn't mind using it, perhaps some details need to be polished. 
The thing is that Firefox is 'just a web browser' when it comes to answering the question "What is Firefox for?". In Konqueror some buttons in the toolbar that are exclusively used for file exploring will still be there when it's used as web browser. 
That's what I prefer Firefox: I used it in Windows, use it in Linux, it behaves the same way in both platforms, and it does its job. 

And about Kubuntu, I agree with your opinion about having two applications installed that do the same. This is the case of Amarok and Juk. I find the KDE menu *really* fuzzy, it's hard to find applications. Sometimes the name of the application is in brackets after the description of it, like this
"Terminal application (Konsole)"
"Multimedia player (Amarok)"
(Just made them up, not sure if they say that exactly).
And just causes confusion, and the icons won't help :P
Another thing that personally gets on my nerves is the fact of all applications starting with K, that's something I just can't stand :P Specially when the apps have names like "Kppp, Krdc, Krfb, KGpg, Ktip". Frustrating. That leaves the alphabetical order totally useless :P

I'd like to see a kubuntu with a selection of apps that people would actually use. Ubuntu with GNome comes with a very simple but sensible selection of applications. 

Gnome nowadays means simplicity. KDE doesn't. 
I think KDE it's full of buttons, toolbars, options that may be useful, and maybe they have to exist. But probably nobody will use them, at least not the average user. But it's good to have them, if what you want is customization.

---

### Post by J. S. Jackson on 2005-03-31
I don't care much for Firefox personally.  Everytime I try it I don't really understand what all the excitement is about.  Well, I suppose it's popular for Windows users, so they want it in Linux too.  Konq is superior in my view.

I do agree about the menus.. My god, i wish they'd give the "K" thing a rest.

The thing I dislike about Kubuntu is that it feels like I'm computing in tar.  Seems very sluggish.  Ubuntu (gnome) on the other hand is very snappy and responsive.  I'm not sure what the deal is there, but I'm not happy about it.  I've used KDE in Mandrake and Mepis, and neither felt so sluggish.

---

### Post by linuxfanatic1024 on 2006-05-27
What about [Gwenview](gwenview.sf.net)?

---

