---
title: "Mangler - A native ventrilo linux client"
date: 2009-10-11
forum: Gaming &amp; Leisure
---

### Post by ekilfoil on 2009-10-11
<inigo montoya>lemme 'splain.... no wait.. there's too much... lemme sum up</inigo montoya>

This post seems to be the Ubuntu support thread for the time being, so here's the current situation:

Mangler 1.0 was released on 12/1/2009.   The current release version is 1.0.1 as of 1/8/2010 and both are fully functional.  This thread contains a lot of info dating back a few months.

For the latest information, visit the Mangler website at [http://www.mangler.org/](http://www.mangler.org/)

For the latest discussion, obviously, go to the last page of this thread.


---------------------------------------------------
[B]Original post from around october or so:
[/B]
Over the past couple of months, we have made great progress on implementing a native Ventrilo client for Linux.  We are happy to announce a release date of December 1st, 2009!

At long last, no more trying to get vent working in WINE.  No more scripts to make push to talk work properly.  No more hassle than installing a package.

If you have questions or comments, feel free to ask.  The source is 100% GPL.  The core of the application consists of a library that provides a simple backend API to a ventrilo connection.

For more information, screencasts, and SVN information, visit [http://www.mangler.org/](http://www.mangler.org/)

Update: 10/19/2009: Outbound GSM and keyboard push-to-talk are now functional.  We still need testers, so join us on IRC!  Outbound Speex hopefully tomorrow!

Update: 10/24/2009: Outbound speex is working now.  We need people to test it so we can release a decent SVN snapshot.  We need to make sure that it's stable, works with all sound cards, and most importantly doesn't crash.  Please test it out and file a bug at [http://www.mangler.org/](http://www.mangler.org/) if you have problems.  .deb packages are available on the website.

Update: 10/31/2009: I wish you guys that were testing karmic would have filed bugs.  The audio problems (as a result of the new version of PulseAudio) with 9.10 have been resolved as well as a number of other issues.  I could have fixed them sooner had you guys told me :).  At any rate, there's new packages on the website that should work perfectly with karmic.  Please let me know if something is not working for you.

Update: 11/13/2009: We've released 1.0rc1!

Update: 11/21/2009: 1.0rc3 is released and we have 9 more days of testing before release day.  Test it out and give us your feedback.

Update: 12/01/2009: As promised, 1.0.0 is released and ready for use!  Let us know if you run into problems.

---

### Post by bruno9779 on 2009-10-11
I am interested in testing it out.

I will join the freenode once i get home from work (can't do from here)

---

### Post by hikaricore on 2009-10-11
Sounds like a dream come true.
I'll finally stop getting calls from my ex saying her linux is broken becasue vent doesn't work.  :p

---

### Post by Catsluck on 2009-10-11
It's a good thing I had an urge to check up on native ventrilo clients this morning. Is this in any way related to [http://www.spuxproject.net/](http://www.spuxproject.net/) ?

---

### Post by ekilfoil on 2009-10-11
> **Catsluck said:**
> It's a good thing I had an urge to check up on native ventrilo clients this morning. Is this in any way related to [http://www.spuxproject.net/](http://www.spuxproject.net/) ?

Somewhat related.  Two of us were contributing to the Spux project, but we had design decision differences and different ideas on release quality levels.  As such, we broke off and started Mangler.  However, Spux (currently) does not use the same networking backend, which is about 75% of the code.  After the network code, the rest is all pretty pictures. :)

As I said, the core of it is a library we're building called libventrilo3.  Using that library, anyone should be able to implement a user interface or other apps (like a media streamer).  It's only a matter of time before someone builds an ncurses interface I suppose.

---

### Post by Vadi on 2009-10-11
Hm.. who are you exactly? I contributed to Spux too, in the interface department - but got fed up with their decisions, and asked that all my UI work be destroyed. And left! because you don't manage oss projects that way.

---

### Post by ekilfoil on 2009-10-12
> **Vadi said:**
> Hm.. who are you exactly? I contributed to Spux too, in the interface department - but got fed up with their decisions, and asked that all my UI work be destroyed. And left! because you don't manage oss projects that way.

They're good guys.  I don't wish them any ill will.  We just didn't agree on the best way to move forward on development.  If they continue, I imagine their next release will be based on libventrilo3 as well.  Either way, competition creates quality so we all win.

---

### Post by del_diablo on 2009-10-12
> **Vadi said:**
> Hm.. who are you exactly? I contributed to Spux too, in the interface department - but got fed up with their decisions, and asked that all my UI work be destroyed. And left! because you don't manage oss projects that way.

Without dictators, nothing ever gets done /rant

---

### Post by sulio on 2009-10-12
I really have no idea what I'm doing :) but here is what I did :
1.svn co [http://svn.mangler.org/mangler/](http://svn.mangler.org/mangler/)
2. ./configure 
 in the process it wanted to install libgsm,speex and gtkmm. But that's ok.
and I saw this in the process -  compiling without pulse.  you will not have sound support
which is strange 'cos I have pulseaudio installed.
anyway I continue to see what will happen :)
3.make - a lot of text
4.sudo make install
then I try to run it and get this :
mangler: error while loading shared libraries: libventrilo3.so.0: cannot open shared object file: No such file or directory
Any ideas how to fix it ?
the distro is ubuntu 9.04 i386

---

### Post by ekilfoil on 2009-10-12
> **sulio said:**
> I really have no idea what I'm doing :) but here is what I did :
1.svn co [http://svn.mangler.org/mangler/](http://svn.mangler.org/mangler/)
2. ./configure 
 in the process it wanted to install libgsm,speex and gtkmm. But that's ok.
and I saw this in the process -  compiling without pulse.  you will not have sound support
which is strange 'cos I have pulseaudio installed.
anyway I continue to see what will happen :)
3.make - a lot of text
4.sudo make install
then I try to run it and get this :
mangler: error while loading shared libraries: libventrilo3.so.0: cannot open shared object file: No such file or directory
Any ideas how to fix it ?
the distro is ubuntu 9.04 i386

You need to run the ldconfig command to update your runtime linker configuration so it sees the new library.  just run: sudo ldconfig

---

### Post by sulio on 2009-10-13
Thanks ekilfoil, "ldconfig" helped and I was able to install the program on another machine(amd64) too. After connecting to the vent server I was able to hear some voices, but they all were like Darth Vader on very very slow motion . I hope [-o< your team will finish this software soon 'cos a lot of player are waiting for it. Good luck !

---

### Post by ekilfoil on 2009-10-13
> **sulio said:**
> Thanks ekilfoil, "ldconfig" helped and I was able to install the program on another machine(amd64) too. After connecting to the vent server I was able to hear some voices, but they all were like Darth Vader on very very slow motion . I hope [-o< your team will finish this software soon 'cos a lot of player are waiting for it. Good luck !

That *should* be fixed in tonight's SVN build.  Drop by on IRC if it still isn't working.

---

### Post by ekilfoil on 2009-10-20
Bumping this thread for a status update.

Just wanted to let everyone know that we have outbound GSM working as well as keyboard push to talk in tonights build.  Also, there are .deb packages available on the website.  I *should* have outbound Speex working tomorrow (hopefully).

We're still looking for testers, so stop by on IRC if you want to help.

---

### Post by hikaricore on 2009-10-20
Sweet I may have to check it out.  :p

---

### Post by ekilfoil on 2009-10-24
Bump for latest update.

Please help us test if you can.  See the first post (or the website at [http://mangler.org/](http://mangler.org/)) for the latest updates.

---

### Post by ekilfoil on 2009-11-01
Another bump for an update.  Problems with Karmic 9.10 audio have been resolved.  You guys should submit bug reports if it's not working for you :)

---

### Post by inspiteofmyself on 2009-11-01
this has gotten insanely good. now if i can just find a way to make it stop being so quiet. lol...

really nice work, look forward to future releases :)

i have not tried building from source yet, but your debian packages worked fantastically for the most part. server "phonebook" thing didnt work, but im cool with being able to connect and talk without going through the hassles of getting ventrilo to work under wine.

again this is great... keep it up. :)

---

### Post by Glucklich on 2009-11-01
Ooooooh! Oh! Oh! I loved Ventrilo in my online-gaming days. Great initiative! Keep up with the good work.

---

### Post by inspiteofmyself on 2009-11-02
> **Glucklich said:**
> Ooooooh! Oh! Oh! I loved Ventrilo in my online-gaming days. Great initiative! Keep up with the good work.

eh i wouldnt go this far... i hate ventrilo lol..but EVERYBODY uses it in spite of mumble and teamspeak :(

---

### Post by gircintre on 2009-11-02
> **bruno9779 said:**
> I am interested in testing it out.

I will join the freenode once i get home from work (can't do from here)
i have not tried building from source yet, but your debian packages worked fantastically for the most part. server "phonebook" thing didnt work, but im cool with being able to connect and talk without going through the hassles of getting ventrilo to work under wine.

---

### Post by Glucklich on 2009-11-02
> **inspiteofmyself said:**
> eh i wouldnt go this far... i hate ventrilo lol..but EVERYBODY uses it in spite of mumble and teamspeak :(

Yes, it is (or it was, when I used it) less featured than Teamspeam. Though, I never tried Mumble, as I believe it didn't existed at the time. But one of my late clans had a Ventrilo server and it felt less laggy while playing than Teamspeak, at the time. Though, it might be one of those impression things.

But I understand your point of view. These days (and since it appears to be no or few difference between them), if you have good cross-platform options... why not use them? Unless your Game Server Provider is making one of those promotions that for a certain number of slots on the Game Server, they threw a Voice Server for a certain VoIP program.

---

### Post by u235sentinel on 2009-11-02
> **ekilfoil said:**
> Over the past couple of months, we have made great progress on implementing a native Ventrilo client for Linux.  We are happy to announce a release date of December 1st, 2009!

Update: 10/31/2009: I wish you guys that were testing karmic would have filed bugs.  The audio problems (as a result of the new version of PulseAudio) with 9.10 have been resolved as well as a number of other issues.  I could have fixed them sooner had you guys told me :).  At any rate, there's new packages on the website that should work perfectly with karmic.  Please let me know if something is not working for you.

I'll definitely be checking it out.  Awesome!

---

### Post by clearscreen on 2009-11-08
I'll give this a bump...

Many bugs fixed and our first release candidate will be available on the 13th!

---

### Post by doorknob60 on 2009-11-09
...like Spux? [http://www.spuxproject.net/](http://www.spuxproject.net/) Why does there really need to be two incomplete (but advancing nicely) projects working towards the same goal?

---

### Post by linkmaster03 on 2009-11-09
In short, Spux isn't advancing at all. Mangler uses the library that was being written for Spux, but as more work got done on the library for Mangler, the Spux team dropped it. Ekilfoil left the Spux development team to start Mangler after a disagreement over GtkBuilder.

---

### Post by clearscreen on 2009-11-09
> **doorknob60 said:**
> ...like Spux? [http://www.spuxproject.net/](http://www.spuxproject.net/) Why does there really need to be two incomplete (but advancing nicely) projects working towards the same goal?

The two main developers of Mangler were originally involved with the Spux project. Due to differences in direction and expectations we decided to go our separate way.

That being said, a quick look at the trac timeline for both projects will tell you which of the two projects is actively being worked on. Also, Mangler makes use libventrilo3, a stable and portable ventrilo library in C which would make it relatively easy to port Mangler to any platform as long as a C compiler is available. 

Take your pick ;)

---

### Post by mrjerryk on 2009-11-09
I would love to test it out.  I have used vent for several years now and have been waiting for a native linux client.

---

### Post by TobiasV on 2009-11-11
I wanted to test out Mangler, so I installed it (for 64 bit, I'm using 9.04), and first thing I tried to do was bind a push to talk key, I could bind a keyboard one, but nothing happened when I clicked the mouse one. That was fine with me though, so I went on to add a server, but none of the buttons in the server window are working for me. Nothing happens when I click them...

---

### Post by ekilfoil on 2009-11-11
> **TobiasV said:**
> I wanted to test out Mangler, so I installed it (for 64 bit, I'm using 9.04), and first thing I tried to do was bind a push to talk key, I could bind a keyboard one, but nothing happened when I clicked the mouse one. That was fine with me though, so I went on to add a server, but none of the buttons in the server window are working for me. Nothing happens when I click them...

This is covered on the support forums here:

[http://www.mangler.org/forums/?vasthtmlaction=viewtopic&t=1.0](http://www.mangler.org/forums/?vasthtmlaction=viewtopic&t=1.0)  :)

But to answer your question, the .deb you're probably using is the snapshot from 10/31.  Those features are not implemented in that snapshot.  There will be a new snapshot this Friday (11/13) with all of that stuff working.

---

### Post by TobiasV on 2009-11-12
Alright, thanks. Looking forward to trying it out.

---

### Post by clearscreen on 2009-11-13
We just released the first release candidate of mangler, among other things this release features:

[LIST=1]
[*]Per-user volume settings (double click a user in the channel list)
[*]Mouse button push-to-talk
[*]Fix all ticking audio in both Speex and GSM (in both directions)
[*]Added notification sounds for users joining your channel, login, logout, etc. (disable them in Settings -> Audio)
[*]The server list window is fully implemented
[*]The ability to set your comment, URL, and your music player text
[*]And of course, other minor bug fixes.
[/LIST]

Deb packages are available from the download page: 
[http://www.mangler.org/download/](http://www.mangler.org/download/)

---

### Post by joeelmex on 2009-11-13
great i need to try it.

---

### Post by radu_radu on 2009-11-13
I've checked out the unstable sources from SVN and noticed there's a "debian" directory inside, so I assume the sources must be "deb-friendly". I'd like to make myself a deb package rather than running make install.
Can anyone tell me how to make a deb file? Should I use checkinstall, or debuild?
Also, thank you ekilfoil for this great software - it was much needed!

---

### Post by clearscreen on 2009-11-13
> **radu_radu said:**
> I've checked out the unstable sources from SVN and noticed there's a "debian" directory inside, so I assume the sources must be "deb-friendly". I'd like to make myself a deb package rather than running make install.
Can anyone tell me how to make a deb file? Should I use checkinstall, or debuild?
Also, thank you ekilfoil for this great software - it was much needed!

As my last post (on the same page) points out, you can download deb packages from the following link:
[http://www.mangler.org/download/](http://www.mangler.org/download/)

---

### Post by ekilfoil on 2009-11-13
> **radu_radu said:**
> I've checked out the unstable sources from SVN and noticed there's a "debian" directory inside, so I assume the sources must be "deb-friendly". I'd like to make myself a deb package rather than running make install.
Can anyone tell me how to make a deb file? Should I use checkinstall, or debuild?
Also, thank you ekilfoil for this great software - it was much needed!

You don't want to make a .deb from unstable svn.  Just keep using the snapshots debs if you want packages.  But if you REALLY want to, i run this script to create snapshot packages:

```
cd ~/build-dir
today=`date +"%Y%m%d"`
ver=mangler-0.0.$today
rm -rf ~/build-dir/*
svn co http://svn.mangler.org/mangler/trunk $ver
perl -pi -e 's/20091012/'$today'/' ~/build-dir/$ver/debian/changelog
tar -cvzf  $ver.tar.gz  $ver
cd $ver
dpkg-buildpackage -rfakeroot -k4D414DD8
mv ~/build-dir/mangler_* ~/Builds/

```

That -k4D414DD8 is my key ID.  You'll need to create your own key to sign them (or don't sign them at all)

---

### Post by Aevum on 2009-11-17
I know this question may sound stupid but... is this "Mangler" version which is actually already released provided with a chat? I can hear everybody properly and connect and set my comment but I can't find any chat... if there is, am I to stupid not to find it?
Thank you!

---

### Post by mephisto1982 on 2009-11-17
Awesome, just heard of this software from a fellow wow player, and might try it out soon. My current (dead) guild uses TS, but the guild im thinking of joining uses vent instead. I'll let you know if i run into any issues.
Although i havent tested it on a server far (got no place to log in atm), thanks for the great work you've done on it.
One suggestion tho: i installed the RPM for Fedora and it didn't include a .desktop file for the menu entry. Although its easy enough to make my own menu entry, it would be nice if this "just works" and a .desktop file and icon are included by default.

---

### Post by ekilfoil on 2009-11-17
> **Aevum said:**
> I know this question may sound stupid but... is this "Mangler" version which is actually already released provided with a chat? I can hear everybody properly and connect and set my comment but I can't find any chat... if there is, am I to stupid not to find it?
Thank you!

If you're looking for a text chat, it is not (and will not be) implemented in 1.0.  That is on track for 1.1 (meaning it's already available in SVN unstable).

---

### Post by ElSlunko on 2009-11-17
Wow I can't believe this project flew under the radar for me. Going to have to try it out later this week!

---

### Post by inspiteofmyself on 2009-11-17
> **mephisto1982 said:**
> Awesome, just heard of this software from a fellow wow player, and might try it out soon. My current (dead) guild uses TS, but the guild im thinking of joining uses vent instead. I'll let you know if i run into any issues.
Although i havent tested it on a server far (got no place to log in atm), thanks for the great work you've done on it.
One suggestion tho: i installed the RPM for Fedora and it didn't include a .desktop file for the menu entry. Although its easy enough to make my own menu entry, it would be nice if this "just works" and a .desktop file and icon are included by default.

ill tell you that for me... under ubuntu (i just ditched gentoo for karmic), running pulseaudio with very few tweaks to pulseaudio (none i think to be honest) this thing works flawlessly.

my freaking hats off to the guys that work on it ... please dont stop. this is fantastic. id love to know when this officially was started in comparison to when ventrilo added the unlinked "linux" client in their download section god knows how many years ago :P

---

### Post by ekilfoil on 2009-11-17
> **inspiteofmyself said:**
> id love to know when this officially was started

Sept 13th... but there was a lot of work done by others (to decrypt/map the protocol) before then that made it possible.

---

### Post by hikaricore on 2009-11-17
Actually the Ventrilo website has simply said "Linux - In development" for years now.
Posts about the client on the forum have been brushed off or gone unanswered for the most part.

---

### Post by ekilfoil on 2009-11-17
> **hikaricore said:**
> Actually the Ventrilo website has simply said "Linux - In development" for years now.
Posts about the client on the forum have been brushed off or gone unanswered for the most part.

This is dated May 2005: [http://www.ventrilo.com/forums/showthread.php?t=7071](http://www.ventrilo.com/forums/showthread.php?t=7071)

---

### Post by hikaricore on 2009-11-18
And the site has basically said coming soon long before that.  *shrug*
I'm glad someone finally came along and picked up the obvious slack.

---

### Post by joeelmex on 2009-11-18
Guys how can I change which mic to use.  I have a mic on the webcam and seems the one it uses but I have have a mic in I use with a headset.  On other programs I can change which input to use, I don't see a settings tab for audio/mic.  Thanks and keep up the great work.

---

### Post by Aevum on 2009-11-18
> **ekilfoil said:**
> If you're looking for a text chat, it is not (and will not be) implemented in 1.0.  That is on track for 1.1 (meaning it's already available in SVN unstable).

Thanks for the information mate, looking forward to it!
And congratulations really for what you did, it's working amazingly.

---

### Post by ekilfoil on 2009-11-18
> **joeelmex said:**
> Guys how can I change which mic to use.  I have a mic on the webcam and seems the one it uses but I have have a mic in I use with a headset.  On other programs I can change which input to use, I don't see a settings tab for audio/mic.  Thanks and keep up the great work.

Click the Settings Button.  Go to the Audio tab.  Select your input device.

---

### Post by Scarlath on 2009-11-18
This looks really promising! I have been waiting and waiting for Spux to release any type of release for quite a while now... Will definately have a look at this Dec 1st! Does it support out of focus PPT?

---

### Post by ekilfoil on 2009-11-18
> **Scarlath said:**
> Does it support out of focus PPT?

Yes: [http://www.mangler.org/features/](http://www.mangler.org/features/)

---

### Post by inspiteofmyself on 2009-11-18
yeah that was kind of my point. these guys, without internal knowledge of the encryption methods ventrilo uses, or any other "inside" technical details have nailed this down in a very fast time.

kudos to you guys and many thanks. i still cant figure out what exactly it is people see in ventrilo but have definitely been feeling pain of running linux since people switched to it... having to run the thing under wine was horrible if even possible at times. lol.

ive watched 2 or 3 projects like this start...none of them ever went anywhere, or released even a non-working source. i take that back, i think one released a preview of the UI once. you would run it, and it looked like a voice chat client, but was not functional in any way...so anyway, i was filled with doubts when i saw this one...no more though. again, great work. it definitely goes appreciated :)

---

### Post by an0nu4nc3 on 2009-11-20
I'm having trouble with Mangler banning me from a chat server due in relation to me disconnecting frequently because of problems getting EVE running. Obviously every time i deactivate the network i have to drop from Mangler.

Weirdly, though, the first time i was banned for 390 minutes or something. The second time i was banned for around 900 minutes. And now i'm banned for over 1400 minutes. Is there a solution to this?

Are there some output logs i can post here that may help?

I'm running Karmic 2.6.31.15. Sorry i can't be of more use straight away as i'm reading through my syslog and going 'wtf?' and researching everything ^_^

---

### Post by ekilfoil on 2009-11-20
> **an0nu4nc3 said:**
> I'm having trouble with Mangler banning me from a chat server due in relation to me disconnecting frequently because of problems getting EVE running. Obviously every time i deactivate the network i have to drop from Mangler.

Weirdly, though, the first time i was banned for 390 minutes or something. The second time i was banned for around 900 minutes. And now i'm banned for over 1400 minutes. Is there a solution to this?

Are there some output logs i can post here that may help?

I'm running Karmic 2.6.31.15. Sorry i can't be of more use straight away as i'm reading through my syslog and going 'wtf?' and researching everything ^_^

We've had someone that reported a similar problem today and we're currently investigating that.  What codec does your server use?

And FYI, the only way to remove that ban is to restart the server :(

Update: I've released 1.0rc3 which may resolve your problem.

---

### Post by an0nu4nc3 on 2009-11-22
I've been waiting for the Corp leader to show up so i can ask him what codec he's using... but i've just realized it's displayed right infront of me :P

GSM 6.10 44Mhz

Hope that's of some help! I'll install the new RC now and will be back in touch if there are any further problems.

Thank you greatly! :KS

---

### Post by ekilfoil on 2009-11-22
> **an0nu4nc3 said:**
> I've been waiting for the Corp leader to show up so i can ask him what codec he's using... but i've just realized it's displayed right infront of me :P

GSM 6.10 44Mhz

Hope that's of some help! I'll install the new RC now and will be back in touch if there are any further problems.

Thank you greatly! :KS

If it's GSM, it's not the problem I was thinking of.  I don't know if there's any way to get around what you're seeing.  If you connect and disconnect too much, the server thinks you're "spamming" and bans you.

---

### Post by inspiteofmyself on 2009-11-22
> **ekilfoil said:**
> If it's GSM, it's not the problem I was thinking of.  I don't know if there's any way to get around what you're seeing.  If you connect and disconnect too much, the server thinks you're "spamming" and bans you.

i have not been disconnected while using this, but i would suggest adding a 20-30 second delay (the ventrilo has a delay if im not mistaken) if there is not already a delay present.

---

### Post by ekilfoil on 2009-11-23
> **inspiteofmyself said:**
> i have not been disconnected while using this, but i would suggest adding a 20-30 second delay (the ventrilo has a delay if im not mistaken) if there is not already a delay present.

We don't do auto-reconnect at all (although there is a feature request open for this).  It'd be up the user to click connect if they get disconnected.

---

### Post by SKLP on 2009-11-23
I added a mention of Mangler to [https://help.ubuntu.com/community/WorldofWarcraft#Voice chat](https://help.ubuntu.com/community/WorldofWarcraft#Voice chat)

---

### Post by inspiteofmyself on 2009-11-23
> **ekilfoil said:**
> We don't do auto-reconnect at all (although there is a feature request open for this).  It'd be up the user to click connect if they get disconnected.

ah i was misunderstanding the post about being banned for reconnecting.

---

### Post by Taylor13 on 2009-11-23
This has progressed quite a bit since I last tried it a couple months ago...it's now replaced Ventrilo running through wine (with some hacks to get PTT working) as my Vent client :D

Currently I'm running the latest SVN version and I only have 2 issues.

1.  Is there a way to copy the comment/comment url to the clipboard?
2.  Would it be possible to save the per-user volume settings?  It works great but reseting 10 or so volume settings every day is going to get old.

Nice work and thanks!

---

### Post by clearscreen on 2009-11-23
> **Taylor13 said:**
> 
1.  Is there a way to copy the comment/comment url to the clipboard?

[http://www.mangler.org/trac/ticket/48](http://www.mangler.org/trac/ticket/48)
[http://www.mangler.org/trac/ticket/49](http://www.mangler.org/trac/ticket/49)

> 
2.  Would it be possible to save the per-user volume settings?  It works great but reseting 10 or so volume settings every day is going to get old.
This will be possible soon (probably in 1.1).

---

### Post by thumpszilla on 2009-11-25
I was really glad to find this. I only have 1 question. When do expect to be adding the text chat to it as well? Btw great work and this has been long awaited by many.

---

### Post by clearscreen on 2009-11-25
> **thumpszilla said:**
> I was really glad to find this. I only have 1 question. When do expect to be adding the text chat to it as well? Btw great work and this has been long awaited by many.

Chat already works in subversion trunk, if you're feeling adventurous and desperately need chat you can manually compile from source.

It is scheduled for Mangler 1.1 which will probably be out around march.

---

### Post by ekilfoil on 2009-11-25
> **Taylor13 said:**
> 1.  Is there a way to copy the comment/comment url to the clipboard?

This is completed in latest SVN

---

### Post by MacLeod9 on 2009-11-25
Hi all, First off this program looks amazing compared to the hassle of getting vent to work in linux without issue. I do however have one question.

Once I installed and ran the program, I am unable to connect to my guilds vent server. Through my vent app installed with wine I can connect and have verified all information (ip, port, username, etc) to be correct but so far no dice. Im fairly new to linux and have checked other forums, but haven't found anything of use so far. Any ideas on what my problem may be? Any help would be greatly appreciated.

Thanks in advance.

---

### Post by inspiteofmyself on 2009-11-25
> **MacLeod9 said:**
> Hi all, First off this program looks amazing compared to the hassle of getting vent to work in linux without issue. I do however have one question.

Once I installed and ran the program, I am unable to connect to my guilds vent server. Through my vent app installed with wine I can connect and have verified all information (ip, port, username, etc) to be correct but so far no dice. Im fairly new to linux and have checked other forums, but haven't found anything of use so far. Any ideas on what my problem may be? Any help would be greatly appreciated.

Thanks in advance.

does your vent server use a password? i noticed i had to have something in username and something in password to get this to work. ive run pretty much svn everyday since i found this and i very well could be getting confused with an older version...but make sure that you try a private server with a password.

---

### Post by MacLeod9 on 2009-11-25
> **inspiteofmyself said:**
> does your vent server use a password? i noticed i had to have something in username and something in password to get this to work. ive run pretty much svn everyday since i found this and i very well could be getting confused with an older version...but make sure that you try a private server with a password.


thanx for responding. not sure what the problem was, but once I re-installed the program, its working like a champ. SO much better than Ventrilo imo.

Cheers

---

### Post by thumpszilla on 2009-11-26
> **clearscreen said:**
> Chat already works in subversion trunk, if you're feeling adventurous and desperately need chat you can manually compile from source.

It is scheduled for Mangler 1.1 which will probably be out around march.

I am afraid that is a little over my head. I just started using linux maybe a month ago. There is still alot I do not know how to do. I have posted a question or two to the forums here asking for info but no responses. I am still using the vesa driver for my video card cause everytime I installed the driver in 9.04 the system would freeze and I would have to reinstall. So since I don't know how to fix it if the driver messes up on 9.10 I have not installed it. So compiling this and that is just at this time out of my league.

---

### Post by Gluo on 2009-11-26
Hi all, when I use WoW and Mangler at the same time, people in channel hear  noise, when WoW is off or  minimized noise is gone, I tried to disable all audio  drivers in wine, but that didn't work.

---

### Post by ekilfoil on 2009-11-26
> **Gluo said:**
> Hi all, when I use WoW and Mangler at the same time, people in channel hear  noise, when WoW is off or  minimized noise is gone, I tried to disable all audio  drivers in wine, but that didn't work.

Recommended reading:

[http://www.mangler.org/forums/?vasthtmlaction=viewtopic&t=5.0](http://www.mangler.org/forums/?vasthtmlaction=viewtopic&t=5.0)

---

### Post by Gluo on 2009-11-27
> **ekilfoil said:**
> Recommended reading:

[http://www.mangler.org/forums/?vasthtmlaction=viewtopic&t=5.0](http://www.mangler.org/forums/?vasthtmlaction=viewtopic&t=5.0)

Thx for answer, but that didn't work. I'll try to explain my problem in detail. When I speak, my friends hear my voice and noise approximately at the same level (both with PulseAudio and without it) when WoW is working, in other times the sound is perfect.

---

### Post by ekilfoil on 2009-11-27
> **Gluo said:**
> Thx for answer, but that didn't work. I'll try to explain my problem in detail. When I speak, my friends hear my voice and noise approximately at the same level (both with PulseAudio and without it) when WoW is working, in other times the sound is perfect.

Is this present in other applications as well?  For example, when you record something with sound recorder while wow is open, do you hear the noise when you play it back?

---

### Post by MichiganMan on 2009-11-28
Works flawlessly outside of the game.  I can hear them and they can hear me.  But when I fire up Quake Wars they can no longer hear me.  I can still hear them.  The transmit button isn't bound to anything in the game, and I can hear the tone when I hit it, but my voice doesn't go out.  If I exit the game then they can hear me again.  I'm using an USB mic.  

Other than that its a great app, thanks!

---

### Post by ekilfoil on 2009-11-28
> **MichiganMan said:**
> Works flawlessly outside of the game.  I can hear them and they can hear me.  But when I fire up Quake Wars they can no longer hear me.  I can still hear them.  The transmit button isn't bound to anything in the game, and I can hear the tone when I hit it, but my voice doesn't go out.  If I exit the game then they can hear me again.  I'm using an USB mic.  

Other than that its a great app, thanks!

Is this another ID Tech3 game?  Try this:

[http://www.mangler.org/forums/?vasthtmlaction=viewtopic&t=6.0](http://www.mangler.org/forums/?vasthtmlaction=viewtopic&t=6.0)

---

### Post by Gluo on 2009-11-28
> **ekilfoil said:**
> Is this present in other applications as well?  For example, when you record something with sound recorder while wow is open, do you hear the noise when you play it back?

Yes, I'm hearing some noise in record, more than that, I'm hearing that noise in my headphones while playing, but it's much more lower(next to nothing) than my friends hear in channel.

---

### Post by ekilfoil on 2009-11-28
> **Gluo said:**
> Yes, I'm hearing some noise in record, more than that, I'm hearing that noise in my headphones while playing, but it's much more lower(next to nothing) than my friends hear in channel.

Sounds like your problem may be some combination of wow and your sound card.  You may want to try the Ubuntu WINE forums.

---

### Post by chousho on 2009-11-28
Apparently Mangler just doesn't want me to communicate.

After installation I could hear people, but not talk. I checked my input and set it to my USB mic, and now I can talk to people (they can hear me), but I can't hear anyone.

I just can't win ~_~

---

### Post by ekilfoil on 2009-11-28
> **chousho said:**
> Apparently Mangler just doesn't want me to communicate.

After installation I could hear people, but not talk. I checked my input and set it to my USB mic, and now I can talk to people (they can hear me), but I can't hear anyone.

I just can't win ~_~

I've heard of someone discussing a similar problem, and I think their issue was the sound card profile in the ubuntu sound preferences.

---

### Post by thumpszilla on 2009-12-02
A friend helped me install the svn and everything works great. The only thing that could be better is I get a loud pop through my speakers when someone keys thier mic. Is the a simple fix for this?

---

### Post by soneta on 2009-12-02
i will test , thanks for all

---

### Post by GregaG on 2009-12-05
i am looking forward to using it 

i just have 1 problem
i am using ubuntu 8.10 and the deb package says

Error: Dependacy is not satisfiable: libglibmm-2.4-1c2a

greetings GregaG

---

### Post by ekilfoil on 2009-12-05
> **thumpszilla said:**
> The only thing that could be better is I get a loud pop through my speakers when someone keys thier mic. Is the a simple fix for this?

This is likely a problem with Pulse and your specific soundcard.  At present, we open an audio stream for every user, so what you're hearing is probably pulse opening the stream.  I haven't heard anyone else report this, so it may be very limited.  In any case, it's not a simple fix, but we're going to have to do our own stream mixing internally anyway for other features, which will indirectly fix your problem.  No ETA though.


> **GregaG said:**
> i am looking forward to using it 

i just have 1 problem
i am using ubuntu 8.10 and the deb package says

Error: Dependacy is not satisfiable: libglibmm-2.4-1c2a

greetings GregaG

Mangler requires GTK+ 2.16 or higher and 8.10 only provides 2.14.  There are also PulseAudio requirements that are not met on 8.10.  The lowest supported version of Ubuntu would be 9.04.

---

### Post by inspiteofmyself on 2009-12-06
> **ekilfoil said:**
> This is likely a problem with Pulse and your specific soundcard.  At present, we open an audio stream for every user, so what you're hearing is probably pulse opening the stream.  I haven't heard anyone else report this, so it may be very limited.  In any case, it's not a simple fix, but we're going to have to do our own stream mixing internally anyway for other features, which will indirectly fix your problem.  No ETA though.




Mangler requires GTK+ 2.16 or higher and 8.10 only provides 2.14.  There are also PulseAudio requirements that are not met on 8.10.  The lowest supported version of Ubuntu would be 9.04.

so based on this the plan is to get away from opening a stream for every "cued" user and use a single mixed stream for the software? i think that will fix a few issues actually. pulse already burns a chunk of cpu when processing a stream, and it just gets more and more confounded the more streams that get opened. its not bad, but i do think a single stream would help a bit.

---

### Post by suzenon on 2009-12-08
You may believie it or not, but people still use 2.1... versions. Guess it's something with server files.
So... any native linux clients for 2.1. servers or i can forget it? I can figure mangler won't work with 2.1

---

### Post by clearscreen on 2009-12-08
> **suzenon said:**
> You may believie it or not, but people still use 2.1... versions. Guess it's something with server files.
So... any native linux clients for 2.1. servers or i can forget it? I can figure mangler won't work with 2.1

No native clients, not yet anyway.

Mangler [will support connecting to 2.x.x servers](http://www.mangler.org/trac/ticket/25) at some point, but it isn't high on our priority list and not scheduled until after release 1.1.

---

### Post by suzenon on 2009-12-08
You confirmed what i thought, at least it's not that bad via wine. 

I've tried connecting with 2.1 server and it didn't worked at all. If you'll implement such possibility to Mangler it would be great (sooner or later...). Good luck on that and keep up good work.

---

### Post by anthony.phipps on 2009-12-13
I LOVE YOU MANGLER TEAM!!! Where do I donate??

---

### Post by thumpszilla on 2009-12-14
> **ekilfoil said:**
> This is likely a problem with Pulse and your specific soundcard.  At present, we open an audio stream for every user, so what you're hearing is probably pulse opening the stream.  I haven't heard anyone else report this, so it may be very limited.  In any case, it's not a simple fix, but we're going to have to do our own stream mixing internally anyway for other features, which will indirectly fix your problem.  No ETA though. 


Thanks for your response and a great program.;)

---

### Post by ekilfoil on 2009-12-15
> **anthony.phipps said:**
> I LOVE YOU MANGLER TEAM!!! Where do I donate??

Thanks for the offer.  We're not asking for donations.  I'm only $25 out of pocket (not including time) so it's not that big a deal.

Or you can buy something for my girlfriend's amazon wishlist. :) She's still irritated that she didn't see me for the 3 months or so it took to write this thing.

---

### Post by Salpta on 2009-12-16
I look forward to using this... When it gets moved into the repositories.  Any idea on when that'll be?

---

### Post by clearscreen on 2009-12-17
> **Salpta said:**
> I look forward to using this... When it gets moved into the repositories.  Any idea on when that'll be?

We'd love to get Mangler into the main Ubuntu repositories, but we have no control over that, you should ask MoU about it. Closest we can get is set up a PPA, but that would require you to add another repo to your sources list. It is almost just as easy to download the deb file from our download page and install it that way.

---

### Post by Salpta on 2009-12-17
Please understand that I hold this team in very high reguard, as a working vent client is the **very** last thing handcuffing me to windows, but after 3+months of development I'm having trouble understanding why the team isn't taking the last step of getting it into universe at least!

I may be showing my noobness but the [Process]("https://wiki.kubuntu.org/UbuntuDevelopment/NewPackages") seems fairly straightforward, and would go a long way in proving the project's validity.  Not trying to be a "Stick-in-the-mud" but as a normal user who switched to linux for malware/viral reasons I don't install anything that I can't get from the repo's.

---

### Post by clearscreen on 2009-12-17
> **Salpta said:**
> Please understand that I hold this team in very high reguard, as a working vent client is the **very** last thing handcuffing me to windows, but after 3+months of development I'm having trouble understanding why the team isn't taking the last step of getting it into universe at least!


FYI, we'd much rather spend our time developing software than maintaining packages for several distributions. It only took a grand total of 5 posts on the Gentoo forums for a developer to pick up on it and get Mangler into portage. 

That being said, I [filed a bug](https://bugs.launchpad.net/ubuntu/+bug/497854) for packaging on launchpad. It's up to MotU now.

In regards to your security concerns, you can always grab the source and build it manually. Repository links are on our [download page](http://www.mangler.org/download/).

---

### Post by smqlf on 2009-12-26
Evening folks!

I have encountered this problem with Mangler. Both version 1.0 and 1.1. Reinstalled a couple of times. Searched the web for answers et cetera.
Since I can't find a solution, I will post it here, since I think it is more of an Ubuntu problem, than a Mangler.
I am quite new with linux in general, so I might need some guidence with walkthroughs.

Here it comes:

When opening Mangler the "normal" way, it closes as soon as it starts. In a blink of an eye.
So I tried to open Mangler with the terminal, and got this error message:


```
The program 'mangler' received an X Window System error.
This probably reflects a bug in the program.
The error was 'XI_BadDevice (invalid Device parameter)'.
  (Details: serial 1766 error_code 158 request_code 143 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```I can't seem to find the solution myself, so please, help me, kind people :)

Regards,
 annex
 smqlf

---

### Post by joeelmex on 2009-12-27
Just want to say, I used mangler for a 20 man raid last night and boy was I impress.  I usually use a cheap windows laptops as my ventrilio Client but no more need for that any more.  I know you are not accepting any donations but when you do, Ill be the first one to contribute.  Keep up the great work!

---

### Post by karlstad on 2009-12-28
> **smqlf said:**
> Evening folks!

I have encountered this problem with Mangler. Both version 1.0 and 1.1. Reinstalled a couple of times. Searched the web for answers et cetera.
Since I can't find a solution, I will post it here, since I think it is more of an Ubuntu problem, than a Mangler.
I am quite new with linux in general, so I might need some guidence with walkthroughs.

Here it comes:

When opening Mangler the "normal" way, it closes as soon as it starts. In a blink of an eye.
So I tried to open Mangler with the terminal, and got this error message:


```
The program 'mangler' received an X Window System error.
This probably reflects a bug in the program.
The error was 'XI_BadDevice (invalid Device parameter)'.
  (Details: serial 1766 error_code 158 request_code 143 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```I can't seem to find the solution myself, so please, help me, kind people :)

Regards,
 annex
 smqlf

Bumping this! I too got the same problem today and have no idea why.

---

### Post by karlstad on 2009-12-28
> **karlstad said:**
> Bumping this! I too got the same problem today and have no idea why.

Uhm, okay. No idea why, but it worked out after a reboot. *doh*

---

### Post by karlstad on 2009-12-28
> **karlstad said:**
> Uhm, okay. No idea why, but it worked out after a reboot. *doh*

Okay, sorry for spamming but this seems to be a bit unstable. Suddenly it stopped working. Again. So, if anyone happens to know what is causing this then please reply :-)

---

### Post by karlstad on 2009-12-28
> **karlstad said:**
> Okay, sorry for spamming but this seems to be a bit unstable. Suddenly it stopped working. Again. So, if anyone happens to know what is causing this then please reply :-)

Okay, last post. After talking to some people over at the #mangler irc channel on Freenode, I finally figured out that the problem occured when the mouse I've set up as "Mouse Button Push to Talk" was disconnected. Connecting the mouse again made mangler work again.

---

### Post by suzenon on 2010-01-05
So... i've finally tried mangler yesterday, but it wasn't working for me. :(

I've read on official site mangler is somehow based on pulseaudio. Thing is pulse audio mess with my sound (mutes programs etc.) so i've had to remove it. 

In audio settings i can only choose "Default" device (so no choice...). And no sound at all in mangler.

Do i get it right: i won't be able to use mangler without pulseaudio?

---

### Post by ekilfoil on 2010-01-05
> **suzenon said:**
> Do i get it right: i won't be able to use mangler without pulseaudio?

Correct.

---

### Post by suzenon on 2010-01-05
> **ekilfoil said:**
> Correct.
Awww you make my heart bleed confirming this. :D
I was sure i've get rid of pulseaudio and it's issues for good but now seems like painful days of googling and browsing forums are comming.

edit: damn, went smoother than i though

---

### Post by bxcrx on 2010-01-05
Awesome program.  Its 1000x better than Ventrilo with Wine.  

It just works.

A++

---

### Post by inspiteofmyself on 2010-01-05
> **suzenon said:**
> Awww you make my heart bleed confirming this. :D
I was sure i've get rid of pulseaudio and it's issues for good but now seems like painful days of googling and browsing forums are comming.

edit: damn, went smoother than i though

i have no issues at all with pulseaudio...i kinda like pulseaudio ;)

---

### Post by suzenon on 2010-01-06
> **inspiteofmyself said:**
> i have no issues at all with pulseaudio...i kinda like pulseaudio ;)
good for you
i've had issues with it since i've installed ubuntu, so it was way much easier for me to get rid of it instead of dealing with it's issues
after third install it seems to work way better than before, no clue why - maybe i'm too newb with linux to use pulseaudio properly yet

anyways, official mangler site says there's untested (?) alsa support mangler version
have anyone tried it?

---

### Post by ekilfoil on 2010-01-07
> **suzenon said:**
> anyways, official mangler site says there's untested (?) alsa support mangler version
have anyone tried it?

I would not recommend using ALSA if you have a functional PulseAudio system.  Furthermore, if you don't have a functional PulseAudio system, I would recommend fixing it rather than using ALSA directly.

We will *always* be more focused on supporting PulseAudio rather than direct ALSA (mostly because all of the devs use PulseAudio).

---

### Post by Salpta on 2010-01-07
Popping back in here to say that I bit the bullet and downloaded/installed Mangler despite my reservations.   I'm glad to report that my reservations were completely unwarented and that Mangler works *flawlessly!*

Thank you so very, *very* much for removing the very last thing tieing me to windows. =)

ps: GREAT choice in sound-bytes!  I chuckle each time I load it up now, which is a positive way to start any meeting. =)

---

### Post by inspiteofmyself on 2010-01-07
> **Salpta said:**
> Popping back in here to say that I bit the bullet and downloaded/installed Mangler despite my reservations.   I'm glad to report that my reservations were completely unwarented and that Mangler works *flawlessly!*

Thank you so very, *very* much for removing the very last thing tieing me to windows. =)

ps: GREAT choice in sound-bytes!  I chuckle each time I load it up now, which is a positive way to start any meeting. =)

yeah i have been known to reconnect to ventrilo just to hear the connection sound again :D

---

### Post by karlstad on 2010-01-07
> **suzenon said:**
> So... i've finally tried mangler yesterday, but it wasn't working for me. :(

I've read on official site mangler is somehow based on pulseaudio. Thing is pulse audio mess with my sound (mutes programs etc.) so i've had to remove it. 

In audio settings i can only choose "Default" device (so no choice...). And no sound at all in mangler.

Do i get it right: i won't be able to use mangler without pulseaudio?

Well, now some guy on IRC have hacked it so you can compile it with ALSA-support. Read more here: [http://www.mangler.org/2010/01/mangler-with-alsa-support/](http://www.mangler.org/2010/01/mangler-with-alsa-support/)

---

### Post by ekilfoil on 2010-01-08
> **Salpta said:**
> Popping back in here to say that I bit the bullet and downloaded/installed Mangler

:D

> despite my reservations.

[-X


> I'm glad to report that my reservations were completely unwarented

:lolflag:

> and that Mangler works *flawlessly!*

\\:D/

> Thank you so very, *very* much for removing the very last thing tieing me to windows. =)

If you want to say thanks, you could give us some more Diggs: [http://digg.com/linux_unix/Mangler_A_Ventrilo_Compatible_Client_for_Linux](http://digg.com/linux_unix/Mangler_A_Ventrilo_Compatible_Client_for_Linux) (or stumbles, or whatever is the hot thing these days)... or blog posts and incoming links, because our Google pagerank sucks.

---

### Post by suzenon on 2010-01-08
> **ekilfoil said:**
> I would not recommend using ALSA if you have a functional PulseAudio system.  Furthermore, if you don't have a functional PulseAudio system, I would recommend fixing it rather than using ALSA directly.

We will *always* be more focused on supporting PulseAudio rather than direct ALSA (mostly because all of the devs use PulseAudio).
Note taken.
But you know it's not that easy to tweak everything for a beginner. :)

I get mangler working, however my soundserver isn't fine enough yet. But mangler is doing fine, joy of using it, really. Thanks for this piece of soft.

Don't know how long your to-do list is, but i'm looking forward to see some muting options. ;)

btw. Can i somehow make mangler to be louder than rest of OS sounds?

---

### Post by ekilfoil on 2010-01-08
> **suzenon said:**
> btw. Can i somehow make mangler to be louder than rest of OS sounds?

Not in the currently released version.  The next version has a master volume control in the app.

edit: Oh... and muting individual users is available in the next release as well.

Both of those features are already implemented in SVN.

---

### Post by Saiko Berry on 2010-01-10
You can compile it with ALSA, but it doesn't work for my input. It lets me chose my device now, but it doesn't play sound through my USB Headset. It only works for my speakers, nothing else.

I get these errors.

snd_pcm_set_params() failed: Invalid argument
ALSA lib pcm.c:7326: (snd_pcm_set_params) Rate doesn't match (requested 32000Hz, get 0Hz)

snd_pcm_set_params() failed: Invalid argument
ALSA lib pcm.c:7315: (snd_pcm_set_params) Channels count (1) not available for PLAYBACK: Invalid argument

If anyone wants to know how to.. see my instructions below.

> Instructions for compiling Mangler with ALSA;

svn co [http://svn.mangler.org/mangler/trunk](http://svn.mangler.org/mangler/trunk) mangler
cd mangler
./configure --enable-alsa
make
cd src
nohup ./mangler &

---

### Post by ekilfoil on 2010-01-10
> **Saiko Berry said:**
> You can compile it with ALSA, but it doesn't work for my input. It lets me chose my device now, but it doesn't play sound through my USB Headset. It only works for my speakers, nothing else.

I get these errors.

snd_pcm_set_params() failed: Invalid argument
ALSA lib pcm.c:7326: (snd_pcm_set_params) Rate doesn't match (requested 32000Hz, get 0Hz)

snd_pcm_set_params() failed: Invalid argument
ALSA lib pcm.c:7315: (snd_pcm_set_params) Channels count (1) not available for PLAYBACK: Invalid argument

If anyone wants to know how to.. see my instructions below.

You may want to jump on IRC to troubleshoot.  We just committed a fix for ALSA input about 2 and half hours ago.

---

### Post by Falc7 on 2010-02-07
I am trying to install mangler in kubuntu, i click on it to install, it jumps up and down and trys to run, but then nothing happens, can someone help?

---

### Post by clearscreen on 2010-02-10
> **Falc7 said:**
> I am trying to install mangler in kubuntu, i click on it to install, it jumps up and down and trys to run, but then nothing happens, can someone help?

Try running 'mangler' from a console. Do you get any output?

---

### Post by Locke_99GS on 2010-02-18
Awesome. I've been working on a simple C program to forward x events (kbd, mouse, whatever) to the wine process running Ventrilo. It works, but I've been having some small issues that have broken my will. :)

If only I'd have been directed to this before. It works, and I love it!

My only issue with it is that while the key binding's setup does correctly detect the X86Close key, using it won't actually key up voice in Mangler. X86Close is otherwise a dead key, not beeing used by anything else in the system (that I'd discovered thus far) The same issue persists for mouse events. I'm using 1.1.2010116.

---

### Post by Locke_99GS on 2010-03-06
Mouse events I don't know why aren't being picked up by Mangler on my desktop. Still no luck with x-event keys on the keyboard. The mouse shows as a Mac compatible mouse though, may be the problem?

On the laptop, when I use a mouse it functions as expected.

---

### Post by ekilfoil on 2010-03-06
> **Locke_99GS said:**
> Mouse events I don't know why aren't being picked up by Mangler on my desktop. Still no luck with x-event keys on the keyboard. The mouse shows as a Mac compatible mouse though, may be the problem?

On the laptop, when I use a mouse it functions as expected.

Make sure you have the correct mouse selected in the settings window.  If your only available mouse is the "mac compatible mouse", you have bigger problems than can be diagnosed here.  Go to mangler.org's forums or our IRC channel.

---

### Post by Mr.SASQUATCH on 2010-03-08
Congrats on doing an awesome job with this guys, really good to see another option than running ventrilo through wine, gave me trouble for ages and even when I did get vent working it was never as smooth as what Mangler is now. I've just installed it and have the input working fine so I can hear people but whenever I attempt to transmit to others, all they can hear are beeps. Any ideas?

---

### Post by ekilfoil on 2010-03-08
> **Mr.SASQUATCH said:**
> Congrats on doing an awesome job with this guys, really good to see another option than running ventrilo through wine, gave me trouble for ages and even when I did get vent working it was never as smooth as what Mangler is now. I've just installed it and have the input working fine so I can hear people but whenever I attempt to transmit to others, all they can hear are beeps. Any ideas?

Sounds like your input device is set to be a monitor of your output device.

Select the appropriate input device in the settings.

---

### Post by Mr.SASQUATCH on 2010-03-09
> **ekilfoil said:**
> Sounds like your input device is set to be a monitor of your output device.

Select the appropriate input device in the settings.

Thanks mate working perfectly now. :P

---

### Post by ekilfoil on 2010-03-14
FYI: for those of you that have already upgraded to Lucid.  Mangler is going to be unstable on Lucid because of a bug in gtkmm.  I filed a bug against the gtkmm package, and they said an updated gtkmm is coming soon.

Also, some of you using some bizarre gaming super-mouse may have issues with mouse PTT.  If you do, please let us know.

---

### Post by reeceh on 2010-03-16
I've tried installing this on Kubuntu 9.10 but have problems running it. When running via the console i get this message:

```
reeceh@reeceh-desktop:~$ mangler
failed to get device list
```

If i then try to connect to a server, it gets refused and console shows this message:

```
mangleraudio.cpp: pa_simple_new() failed: Connection refused
```

Makes sense that its an audio issue. But how come it can't find any devices? If you need more info just ask!

---

### Post by ekilfoil on 2010-03-16
1.0.x only supports PulseAudio.  Use a developer snapshot version for ALSA support.

---

### Post by reeceh on 2010-03-16
God, I'm so stupid sometimes! :) thanks dude

---

### Post by EvilTchnlgy on 2010-03-29
Just installed on lucid from the ppa, working great so far. Ill let you know if I run into any issues :) I appreciate this so much, I play wc3 on ubuntu and the only thing missing was a solid native vent client :)

---

### Post by moffa on 2010-03-31
just found this thread using google, looking for a Ventrilo client.  I really appreciate your hard work, just one feature request please - have a "test" setup where you can record something and it plays it back. It makes it a lot easier to set volume levels.
thanks again!

---

### Post by ekilfoil on 2010-03-31
> **moffa said:**
> just found this thread using google, looking for a Ventrilo client.  I really appreciate your hard work, just one feature request please - have a "test" setup where you can record something and it plays it back. It makes it a lot easier to set volume levels.
thanks again!

If you're using the latest dev snapshot version, there's a VU meter to show you your transmit level.

---

### Post by moffa on 2010-03-31
Nice I added the PPA and installed mangler-dev package.  Works great! Thanks.
Using Ubuntu 10.04 x64

---

### Post by ekilfoil on 2010-03-31
> **moffa said:**
> Nice I added the PPA and installed mangler-dev package.  Works great! Thanks.
Using Ubuntu 10.04 x64

Cool.  And before you report the bug with the per-user volume slider thingie... [https://bugzilla.gnome.org/show_bug.cgi?id=614320](https://bugzilla.gnome.org/show_bug.cgi?id=614320)

---

### Post by XxBJDxX on 2010-05-18
works perfect on 9.10

---

### Post by Scazy on 2010-07-11
This works great!  Only change I had to make was to change the computer settings to use mic 2.
  
Ubuntu 10.04 LTS - the Lucid Lynx
emachines E520 (yes, yes, I know)
standard mic and speakers 
  
Thank you huge amounts!

---

### Post by Chuckaluphagus on 2010-07-13
Wanted to thank you for Mangler.  I've never used Ventrilo but found myself in a situation where I needed it to have voice chat in an online game.  Mangler on 10.04 (32-bit) works flawlessly for me.

---

### Post by reklan on 2010-07-15
Same here.. Many thanks for Mangler.

This has helped me move over to Ubuntu for nearly 50% of my computer needs..

---

### Post by HeadHunter00 on 2010-08-09
When playing games in full screen, i cant press the talk button, nor hear my friends talking. Is there any way to make mangler work while playing fullscreen?

---

### Post by HeadHunter00 on 2010-08-09
ok never mind, it randomly got fixed

---

### Post by G00D_GUY on 2010-08-26
Wooooooooo

Thank you SOOOOOO much.

I've been looking for this for a long time. :D

Works Great!

---

### Post by willhelmwr on 2011-01-18
I've just tried mangler but my company is using older version (2.1) of ventrilo, so mangler is giving up. Is there any possibility to make it working?

---

### Post by MikeyPooh on 2011-02-03
i got Mangler to connect to Server but People cant hear me when i talk

Anyone know how to get Mic Working?


Thanks

---

### Post by gintovan on 2011-02-04
hah, mangler means missing in danish... 

Missing - A native ventrilo linux client

Anyway sorry for off-topic  ):P

---

### Post by willhelmwr on 2011-02-05
You must set speaking key by yourself in settings. When you press it, people can hear you.

---

### Post by willhelmwr on 2011-02-05
how to delete post?

---

### Post by MikeyPooh on 2011-02-06
yes i did that 

Mic isnt working even in Sound Recorder

---

### Post by willhelmwr on 2011-02-08
so it's drivers fault

---

### Post by roma.hicks on 2011-09-27
Very nice program!  Works perfectly.

If you are like me and built it from source be sure to include pulseaudio-dev headers or the only sound system you get is OSS which does not work and is not practical with the padsp adapter.

It took me about 30 minutes messing with it before it ocured to me.  ./configure does not throw a warning because at least one sound developmental headers are present when built (which on my 11.04 was OSS, apparently).

---

### Post by chris282 on 2011-11-30
Hi, I've been trying to use the old Ubuntu version of Mangler (1.2.0), because I wasn't confident in my ability to compile from source, but I'm not able to use Push To Talk with my Logitech mouse; this appears to have been a known issue in 2010 - [http://www.mangler.org/forums/mangler-support/unable-to-set-mouse-ptt/](http://www.mangler.org/forums/mangler-support/unable-to-set-mouse-ptt/)

Does anyone know whether this is still an issue with the current release (1.2.2)?

Any information would be much appreciated.

---

### Post by chris282 on 2011-12-05
Anyone?

---

