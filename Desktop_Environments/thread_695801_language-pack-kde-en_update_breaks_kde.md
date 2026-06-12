---
title: "language-pack-kde-en* update breaks kde"
date: 2008-02-13
forum: Desktop Environments
---

### Post by SalsaDoom on 2008-02-13
Hi fellas,

An update today broke KDE :)

Working fine, an update to the kernel and to translation packages (English only computer btw) popped in today, and boom, it fails. When logging in KDE I get the error something like, "ksmserver cannot start. Check your installation." Well. I login with failsafe to see what ksmserver server has to say about all this and I get...

kdecore (KLocale): WARNING: Definition of PluralForm is none of NoPlural/TwoForms/French/OneTwoRest/Russian/Polish/Slovenian/Lithuanian/Czech/Slovak/Arabic/Balcan/Macedonian/Gaeilge/Maltese: Definition of PluralForm - to be set by the translator of kdelibs.po

Doesn't seem fatal exactly, but it does indeed not start.

Now, its one of these updates thats caused this: language-pack-kde-en language-pack-kde-en-base. Installing the rest of todays updates works just fine, including the "generic" language-pack-en*.

I don't know how to fix a problem like that, unfortunately, translation stuff is a mystery to me -- since well, I've never had to deal with it before. Anyone else?
--SD

EDIT: It occurs to me to post the package versions, the original version of language-pack-kde-en (that worked) was 20071120. The broken version is 20080205. language-pack-kde-en-base working version was 20071012 and broken is 20080205. Well, at least one of those packages is broken, I'm not sure which.

---

### Post by Helladog on 2008-02-13
Yep...I have the same problem, and I had someone else from kubuntu forums confirm it as well.  It's beyond our expertise to fix the problem, so hopefully there will be a fix soon.  

This is the first problem I've had with kubuntu in over a year.  It's this kind of problem that made me leave Windows behind in the first place.  It's got to be really troubling for new users.

Keep me updated in the event you find a fix for this plz.

---

### Post by SalsaDoom on 2008-02-13
Yeah, hmmm. Doesn't seem to be a lot of activity regarding this, all day and no posts about it. Maybe not everyone has it? I'll post here if I figure out a solution...

--SD

---

### Post by SalsaDoom on 2008-02-13
Here is a temporary fix :) This downgrades to the working versions... so it'll complain that there are updates available, but at least your system works until a real fix gets in the works. Awful that this happened in the first place though.

> sudo apt-get install language-pack-kde-en=1:7.10+20071120 language-pack-kde-en-base=1:7.10+20071012

Don't know why I didn't think of this earlier, but there it is :P

--SD

---

### Post by Helladog on 2008-02-13
Thanks!  Works now.  I'll pass this temp fix along...

---

### Post by daflame on 2008-02-13
It's not that not everyone doesn't have the problem, since ALL my computers (I have 4) have it as soon as I run the updates and I'm using both amd64 and i386 installations.  I think this problem is limited to Gutsy however since I manage a Feisty server that is fine.

I think the problem is that people are not finding this forum on the search engines yet.  It took me 15 minutes to find it and I had to use the cause of the problem (the language packs) to find it.  Most people wouldn't know the name of the language pack to search for it, let alone that that was the issue.

---

### Post by Zeroangel on 2008-02-14
I got this problem as well -- in fact I spent a great deal of yesterday panicking over it -- and had to end up booting into GNOME.

It seems that the *buntu KDE devs are trying to stop our plans for [Canadian World Domination]("http://ofrabjousday.blogspot.com/2007/03/canadian-world-domination.html").

Will downgrade the packages ASAP. Thanks.

(P.S.: Another Saskatoonian! Woohoo!)

(P.P.S.: Thanks Ken!)

---

### Post by luis_lopez on 2008-02-14
This problem is reported in launchpad:

[https://bugs.launchpad.net/ubuntu/+source/language-pack-kde-en/+bug/187602](https://bugs.launchpad.net/ubuntu/+source/language-pack-kde-en/+bug/187602)

There's a workaround: change the LANG variable to en.US.UTF8

LANG="en_US.UTF-8"

And KDE should work again... It worked for me!

Regards,

Luis

---

### Post by JeremyTheGeek on 2008-02-15
OMG!!!!

Thank you for the fix it worked like a charm. You and Gnome saved me from doing a complete reinstall of kubuntu!! THANK YOU!!!!!:guitar::guitar:

---

### Post by Zeroangel on 2008-02-15
HOLY CRAP, MELVILLE.

Say, do you work for L. Sapara? Runs a server reselling business called Sasktech as well as being on staff at the MEC. I worked alongside him at one point during a little stint I had at the old MEC.  :KS

---

### Post by Helladog on 2008-02-15
Adept still prompts me for the same update with the same date, why aren't they replacing it with a working update?

---

### Post by Zeroangel on 2008-02-16
Just out of curiosity. Has anyone here been having problems with Kopete Instant Messenger -- such as freeze ups? Its an elusive problem for me and hard to track down and i'm just trying to narrow down whether its a language related problem too (EN.CA)

---

### Post by JeremyTheGeek on 2008-02-16
@Zeroangel: I know L. Sapara but I don't work for him. Learned about Linux on my own and have been developing my skills ever since. User since August, Power to Saskatchewan!!!

BTW: Loved the reaction! :popcorn::popcorn:
Ubuntu Bug URL (Optional)

---

### Post by djgrant on 2008-02-17
> **SalsaDoom said:**
> Here is a temporary fix :) This downgrades to the working versions... so it'll complain that there are updates available, but at least your system works until a real fix gets in the works. Awful that this happened in the first place though.



Don't know why I didn't think of this earlier, but there it is :P

--SD

Can anyone tell me how to pin these packages? I used to do this kind of thing all the time when I used debian a long time ago but I can't remember how to do it.

---

### Post by Ubuntiac on 2008-02-18
> **Helladog said:**
> why aren't they replacing it with a working update?

My guess is because it "only" seems to be Canadians and it "only" seems to be Kubuntu. :(

Still, seems to me us Canadian Kubuntu users are rather fond of having our computers work, too...

---

### Post by brm on 2008-02-19
Thank you for identifying the cause of this problem.

The same problem also affects KDE4. I am about to add a note to the bug report to point this out.

---

### Post by Zeroangel on 2008-02-20
SOLUTION FOUND:

I recommend to remove or comment out the repository "gutsy-proposed" until further notice. You should then be able to unlock the packages and YAY! no more reminders about the kde-language packages needing to be updated.

---

### Post by bls0n on 2008-02-22
Any suggestions for resolving this issue in kde4?  Not being able to login seems like a pretty serious issue...

Thanks!

---

### Post by bls0n on 2008-02-22
Woohoo!  If you have this problem with kde4 (can't login), just delete /etc/kde4rc and you should be good to go!

[https://bugs.launchpad.net/ubuntu/+source/kubuntu-default-settings/+bug/193498](https://bugs.launchpad.net/ubuntu/+source/kubuntu-default-settings/+bug/193498)

---

### Post by daflame on 2008-02-22
Thanks for the notes above, I guess I really shouldn't use proposed packages on production machines.  I get what I deserve.

---

### Post by daflame on 2008-02-25
> **Zeroangel said:**
> SOLUTION FOUND:

I recommend to remove or comment out the repository "gutsy-proposed" until further notice. You should then be able to unlock the packages and YAY! no more reminders about the kde-language packages needing to be updated.

Until today, that proposed solution was fine, but as of today even main update repos are pushing these broken updates...  I'm not impressed...

---

### Post by sgrover on 2008-02-25
Just happened to me today with my 64bit install.  I ran the LANG= fix, but that only applies to the current session.  I know I *could* put that into my .bashrc or something similar but that defeats the purpose of keeping my box low maintenance.  (i.e. when I reinstall, I'll have to remember that tweak??). 

Anyone know if/when this is going to get fixed properly?

---

### Post by Zeroangel on 2008-02-25
Oh man, its moved out of proposed and now into mainstream?
> **daflame said:**
> Until today, that proposed solution was fine, but as of today even main update repos are pushing these broken updates... I'm not impressed...
Yep. Crap has officially hit the fan that is blowing in the general direction of English Canadian KDE users.

EDIT:
Added to Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/language-pack-kde-en/+bug/195647](https://bugs.launchpad.net/ubuntu/+source/language-pack-kde-en/+bug/195647)

---

### Post by apogee on 2008-02-26
> **SalsaDoom said:**
> 
sudo apt-get install language-pack-kde-en=1:7.10+20071120 language-pack-kde-en-base=1:7.10+20071012  

Don't know why I didn't think of this earlier, but there it is :P



me@apogee:~$ sudo apt-get install language-pack-kde-en=1:7.10+20071120 language-pack-kde-en-base=1:7.10+20071012 
[sudo] password for me:
Reading package lists... Done
Building dependency tree
Reading state information... Done
--------------------------

My Dell Inspirion 8100, Kubuntu 7.10 crashes at that point.

Please help: I'm not a terminal guru, just terminal. :-)
Thanks.

---

### Post by Kavi on 2008-02-26
Hey Guys,

I'm currently having this problem after updating the language packages.  I updated earlier today and after restarting I got the "could not start ksmserver".  This has to be the problem as I had just updated those packages.

I have logged in using failsafe and tried entering:
sudo apt-get install language-pack-kde-en=1:7.10+20071120 language-pack-kde-en-base=1:7.10+20071012 

This is what it returned:

E: Version '1:7.10+20071120' for 'language-pack-kde-en' was not found.

Why is this happening and how can I fix this problem?

Thanks,
-Kavi

---

### Post by CptFuzzy on 2008-02-26
Confirmed: this seems to fix it, temporarily.  But now my kde is hosed from my other attempts to fix this (lost dolphin somehow, among other things)...

aptitude install language-pack-kde-en=1:7.10+20071012
...
The following packages are BROKEN:
  language-pack-kde-en-base
The following packages will be DOWNGRADED:
  language-pack-kde-en
...
Downgrade the following packages:
language-pack-kde-en-base [1:7.10+20080205 (gutsy-updates, now) -> 1:7.10+20071012 (gutsy)]

Accept this solution? [Y/n/q/?] Y
The following packages will be DOWNGRADED:
  language-pack-kde-en language-pack-kde-en-base
Do you want to continue? [Y/n/?] Y
...
Get:1 http://archive.ubuntu.com gutsy/main language-pack-kde-en-base 1:7.10+20071012 [3144kB]
Get:2 http://archive.ubuntu.com gutsy/main language-pack-kde-en 1:7.10+20071012 [2078B]
Fetched 3146kB in 18s (174kB/s)
dpkg - warning: downgrading language-pack-kde-en-base from 1:7.10+20080205 to 1:7.10+20071012.

but now the same packages want to upgrade (is there a way to ignore specific packages?):

The following packages will be upgraded:
  language-pack-kde-en [1:7.10+20071012 -> 1:7.10+20080205]
  language-pack-kde-en-base [1:7.10+20071012 -> 1:7.10+20080205]

---

### Post by Alex_Perry on 2008-02-26
Just adding to this thread, my Kubuntu system is affected, too. Adept updater indicated 4 new packages this morning. After update was complete, a new Konqueror session wouldn't load. I restarted X, and wouldn't let me past KDM.

Temporarily changed the LANG variable until a fix is released.

---

### Post by crucial123 on 2008-02-26
Thanks for the solution to this.

I blame the problem on the South Park children.

I just went to adept and uninstaled the english language translations
and presto bingo.

This would be a bugger for my dear old mom to figure out though!

it is a shame that this has been released into the wild...at first I couldn't figure out why it first cropped up for some of you folks a couple of weeks back and only today on my 'puter.

I don't access proposed repositorys so as to avoid this kind of snafu.

oh well cheers all

---

### Post by Alex_Perry on 2008-02-26
> **Alex_Perry said:**
> Just adding to this thread, my Kubuntu system is affected, too. Adept updater indicated 4 new packages this morning. After update was complete, a new Konqueror session wouldn't load. I restarted X, and wouldn't let me past KDM.

Temporarily changed the LANG variable until a fix is released.

just to add, I just ran ```
sudo aptitude install language-pack-kde-en=1:7.10+20071012
``` and restarting X resolves the issue. Now, just to hold off on running Adept for the next while.

---

### Post by LarsO on 2008-02-26
For people like me, little new to Linux - I finally figured it out how to do it...
I logged on in recovery mode which gave me a root prompt terminal
My network card was disabled; there no ip-address when checking with ifconfig so the downgrade to the previous package didn't work.
I have no idea how to get the network card to renegotiate an IP address with my router in terminal mode so I solved this in the following way:
code:
```
LANG="en_US.UTF-8" startx
```

This gets a root xsession going
There I went to System Settings in the Kmenu and started the Network Settings
Select the interface card and click on Configure Interface.
Pick Automatic and DHCP and click OK
Then click on Enable Interface and you should see an IP address appear.
Exit out of the system settings and start a console.
In the console run code:
```
aptitude install language-pack-kde-en=1:7.10+20071012
```
(no need for sudo, you are already root)
log out of the xsession and reboot the computer.
This resolved the issue for me but I did have to go into the network settings and check the 'Activate when the computer starts' in the network interface configuration

---

### Post by Zeroangel on 2008-02-26
> **Alex_Perry said:**
> just to add, I just ran ```
sudo aptitude install language-pack-kde-en=1:7.10+20071012
``` and restarting X resolves the issue. Now, just to hold off on running Adept for the next while.
+1 for this solution.

Someone posted on launchpad that its not only affecting people using the EN_CA locale, but also some of the gutsy users who are using other locales too.
> Hi, I am not using the EN_CA locale. Yet I did experience similar
problems as described here (gradual slowdown of system --> complete
system lockup, unable to log in to KDE session (I am using Kubuntu 7.10
64 bit).

The problem was resolved by sudo apt-get remove language-pack-kde-en

I suggest that the bug is not specific to locale EN_CA locale, but may
be general to all users OR there are other problems related to same
package that affect users that does not use EN_CA locale.

My locale information:
LANG=nb_NO.UTF-8
LANGUAGE=nb_NO:nb:no_NO:no:nn_NO:nn:en

---

### Post by demarshall on 2008-02-27
Thank you very much, Alex_Perry!  :)

I didn't know what to do and the guy who I normally ask questions of had already given up and switched to Gnome.

---

### Post by euclidean on 2008-02-27
Well, a little too late in finding this thread, but it hit my wife's system as well. I am running feisty myslef so I dodged the bullet. I actually parallel installed the xubuntu-desktop just to have a running system for her. Finally ran across a post on here from 2006 where someone had the same thing happen.

I managed to force downgrade the language packs in synaptic and bingo, I was back into KDE.

Yeesh - this is why I jumped from Mandrake. I was tired of random breakages. It is a good thing I have held off setting up 3 or 4 other people's systems with kubuntu or they would all be screaming right now...

---

### Post by Zeroangel on 2008-02-27
Installing ubuntu-desktop or any of the other DE's is also useful. I've had to go into the GNOME desktop a few times through this ordeal. I'm always happy to be back in KDE when I can get it working. :)

Found a slightly easier way to change the language
```
sudo qt-language-selector --mode select
```Set it to "US English" for now, go ahead with the apt-get upgrade (I know ya wanna) -- then restart X, and move on with your life :)

---

### Post by apogee on 2008-02-27
Hi all

I have tried removing the language pack == does not work
I have tried rolling back to a previous version == does not work
I have tried changing the language setting == does not work
even updating does not work.

I am busy with a back-up, then I am going to format & re-install.

I am not in Canada...
cheers till later :-)

---

### Post by jamuir on 2008-02-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/language-pack-kde-en/+bug/195647](https://bugs.launchpad.net/ubuntu/+source/language-pack-kde-en/+bug/195647) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm glad I found this thread!

I am running gutsy with KDE.  I did an "apt-get update" Monday evening ( 25 Feb 2008 ) from the official apt sources and was not able to login to KDE on a subsequent reboot.  So, I can confirm the KDE language bug.  I was using the en_CA locale.  So it appears I'm another Canadian victim :)

After reading the reports on launchpad, I did a console login from KDM and ran
```

sudo apt-get remove language-pack-kde-en

```
This fixed the problem.

I imagine that there are quite a few people who think they have an unusable Kubuntu system right now.  And without KDE, it will be difficult for these people to access the web to find a solution.  Hopefully, they remember to use the Live-CD.

Let's hope language-pack-kde-en is fixed upstream soon!  Until then: take off, eh :)

-James

---

### Post by Marman on 2008-02-27
I had the same issue on both 32 & 64 bit systems even after the latest update to the kde language pack - basically kde weirdness/broken/unable to login.

Here is what solved it for me, edit the file /etc/default/locale and change the line from:

LANG="en_CA.UTF-8"

to

LANG="en_US.UTF-8"

restart X or reboot and kdm as well as kde work again.

cheers
-m

---

### Post by Zeroangel on 2008-02-27
Well. A programmer came across the bug and escalated it to "critical" status at 5:30am today. The affected package was fixed and released at 6:30. Thank you Mr Martin Pitt! :)

** Please disregard all previous workarounds -- and update and upgrade your packages!**

--------------------
More info:
> The cause has been identified: Some Canadian English translator actually
translated a plural form definition message against the prominent
warning:

msgid ""
"_: Dear translator, please do not translate this string in any form, but "
"pick the _right_ value out of NoPlural/TwoForms/French... If not sure what "
"to do mail [EMAIL="thd@kde.org"]thd@kde.org[/EMAIL] and [EMAIL="coolo@kde.org"]coolo@kde.org[/EMAIL], they will tell you. Better leave "
"that out if unsure, the programs will crash!!\n"
"Definition of PluralForm - to be set by the translator of kdelibs.po"
msgstr "Definition of PluralForm - to be set by the translator of kdelibs.po"

I verified that en_CA is the only affected language.

-- 
7.10: en_CA causes KDE apps to fail to start
[https://bugs.launchpad.net/bugs/191327](https://bugs.launchpad.net/bugs/191327)> I uploaded a fixed version, it should be available in about two hours.

For everyone who is affected by this and cannot log into the graphical
environment any more, you can do the following steps to recover:

  * Press Ctrl+Alt+F1 to get to a text console
  * Log in (type username, enter, password, enter)
  * run "sudo apt-get update" and enter your password
  * run "sudo apt-get upgrade".

The last step should fetch the updated language-pack-kde-en-base. Please
let me know if you still have troubles.

Thank you and sorry again for the inconvenience!


** Changed in: language-pack-kde-en (Ubuntu)
       Status: In Progress => Fix Committed

-- 
7.10: en_CA causes KDE apps to fail to start
[https://bugs.launchpad.net/bugs/191327](https://bugs.launchpad.net/bugs/191327)

---

### Post by Alex_Perry on 2008-02-27
Confirmed. Run apt-get update/upgrade and 'language-pack-kde-en-base 1:7.10+20080205**+1**' will be installed.

Problem solved!

---

