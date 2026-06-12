---
title: "For kopete's sake!"
date: 2005-08-23
forum: Desktop Environments
---

### Post by skoal on 2005-08-23
I'm trying real hard here to become a KDE fanboy, but kopete keeps puking out "You cannot add yourself to myself contact list", apparently ghosts all my responses in a window while other people say they receive it, and for the love of jebus won't let me move around my Group directories.

I seem to be up to date on kroakpete too: version 4:3.4.0-0ubuntu2.1 (0.10)

It looks like the [kopete](http://kopete.kde.org/) fellers have 0.10.3 out there for some download loving.  Anyone got a package build for this fubar'd app?  Backport? Dirty hacks for a quick fix? I'm open to suggestions (other than "gaim it j00 1u53r!")...

\\//_

---

### Post by 8FootSativa on 2005-08-23
10.3 comes with KDE 3.4.2, so you need to have that installed.

I really want to like Kopete as well....just not being able to set my user info irritates me enough to avoid it. Try a CVS build of SIM. You have to tweak it like crazy to make it not all goofy, but once you get that done, it's really nice.

---

### Post by f1dave on 2005-08-24
I know what you guys mean. Gaim is probably the only gnome app installed on my system... But i use it simply because it's so much better than kopete :S Meh, it's time will come no doubt.

---

### Post by Lord Illidan on 2005-08-24
I prefer GAIM, even though it lacks the funky KDE icons... 
Also, in Kopete the other guy's image in MSN is a small icon on the taskbar, ridiculous!!!

---

### Post by Mishura on 2005-08-24
Indeed, I keep trying, and trying to like Kopete.  It's integration with KDE makes it a huge selling point (Especially when a Mac using friend of mine showed off iChat's integration with OS X).  But, no matter what, I keep grugingly crawling back to Gaim.  Almost in a "Sorry I doubted you, plz forgive me!" kinda way.

Kopete needs some serious work, especially in the AIM section.  Gaim does too, but at least its mostly functional.  One thing missing is perfect Direct IM support (Gaim 2 iChat is buggy as all hell--untested with Gaim 2 Gaim).

I wonder why Kopete keeps wanting to use it's own implementation (Libkopete) instead of using LibGaim, that Both Gaim and Adium use?  Sounds like re-inventing the wheel to me.  There could be some serious collaboration between these products.  End result:  Two awsome IM clients for both Gnome and KDE, instead of two useful, but not spectacular programs for both DEs.

---

### Post by GeneralZod on 2005-08-24
[QUOTE=Mishura]
I wonder why Kopete keeps wanting to use it's own implementation (Libkopete) instead of using LibGaim, that Both Gaim and Adium use?  Sounds like re-inventing the wheel to me.  There could be some serious collaboration between these products.  End result:  Two awsome IM clients for both Gnome and KDE, instead of two useful, but not spectacular programs for both DEs.[/QUOTE]

The gaim developers appear to be fiercely opposed to using C++, and KDE developers have a tendency to prefer C, although I've not seen any real fanaticism on this point.  This could have something to do with it.  Also, are the gaim libs sufficiently extricated from gaim itself i.e. the GUI, etc? Last I heard, the gaim libs were difficult to use for anything other than gaim.

---

### Post by arcanistherogue on 2005-08-25
I tried to like Kopete.

I just use Gaim with the gtk themes, Clearlooks Quicksilver.

I love it.  Now, If I can only find a KDE theme for Gnome to apply to it....

---

### Post by skoal on 2005-08-25
Kroakpete ain't so bad, and I can manage it's pschizophrenia at times. I just don't wish to upgrade my entire KDE to 3.4.2 for kroakpete, if that means I pull in half of Breezy's deps too and possible beak something else.

Unfortunately, I'm tempted every so often to use gAIM anyhow.  Then, I peer over at my transparent kicker panel and see one big ugly gray block around that "yellow running man".  That's like hanging fuzzy dice from your Lexus. As George Bush Sr. (aka Dana Carvey on SNL) would say, "not gunna doit!"

\\//_

---

### Post by drizek on 2005-08-25
kopete is getting some improvements in 3.5. I agree its not as good as it should be, but it works fine for me. The integration of funtionality and look is reason enough for me to use it over gaim. although i have a copy of gaim installed just in case.

As for using libgaim, im sure there is a real reason behind that other than just fanboyism. it could be perfromance related or it might just be easier to recreate everything in libgaim into libkopete than it would be to rewrite kopete around libgaim. also, its not all wasted effort here, the sourcecode is still available to both developers, so any improvements made to gaim can be seen by the kopete devs and "ported" to kopete. a lot of the work in making an IM client is getting it to work with proprietary protocols, so that is something that benefits both kopete and gaim when they can see the others code.

---

### Post by Mishura on 2005-08-25
[QUOTE=drizek]kopete is getting some improvements in 3.5. I agree its not as good as it should be, but it works fine for me. The integration of funtionality and look is reason enough for me to use it over gaim. although i have a copy of gaim installed just in case.

As for using libgaim, im sure there is a real reason behind that other than just fanboyism. it could be perfromance related or it might just be easier to recreate everything in libgaim into libkopete than it would be to rewrite kopete around libgaim. also, its not all wasted effort here, the sourcecode is still available to both developers, so any improvements made to gaim can be seen by the kopete devs and "ported" to kopete. a lot of the work in making an IM client is getting it to work with proprietary protocols, so that is something that benefits both kopete and gaim when they can see the others code.[/QUOTE]

True, true.  However, there are things that Gaim has been capable of doing now for about a year such as File Transfering on the AIM protocol, (in fact, all but MSN so I hear), while Kopete can only File Transfer on the MSN protocol (And maybe Jabber).  Its funny, because, if they were to at least share some ideas together, then both clients would support FTs on all available protocols.   Not to mention that Gaim has buddy icon support (Needed unfortunately,  I got friends who are like "D00d, look at my 4vatar!!",)  and Kopete doesn't support any kind of that except maybe MSN.


To basically summarize (Long post I know..):

Kopete advantages:

1.  Integration with the KDE desktop, PIM, and other applications.
2.  Less memory usage (Subjective.  I think Kopete is "snappier". )
3.  Very good UI.
4.  Metacontacts.
5.  Themable.

Kopete disadvantages:

1.  No buddy icons
2.  No File Transfer
3.  No Direct IM
4.  I can't set my user alias like I can do with Gaim (I have 3 user accounts with different names.  I want all to say "Mishura")
5.  Doesn't share contact lists with AIM, or others.  Uses its own system.  (If I add a buddy in Kopete, it won't show up in Gaim, or AIM in Windows, and vice versa)

I look forward to future Kopete versions, in the hopes of ditching Gaim someday.  (Or, some Gaim integration with KDE?  Whichever comes first.)

---

### Post by Zinoc on 2005-08-25
Hello,
Kopete in kde 3.5 will have many new features, such as aim and yahoo icon support, yahoo and msn webcam, some features of msn 7, global identity...
So just keep waiting, it just a matter of time for you to leave definitely gkt  ;-) 
Bye !

kde 3.5 feature plan: [http://developer.kde.org/development-versions/kde-3.5-features.html](http://developer.kde.org/development-versions/kde-3.5-features.html)

---

### Post by skoal on 2005-08-25
[QUOTE=Zinoc][...]Kopete in kde 3.5 will have many new features, such as ... yahoo and msn webcam [...][/QUOTE]
Whoah! Where do I sign up for that?  Here's the keys to my car as a down payment to the devs...

\\//_

---

### Post by Mishura on 2005-08-26
<shocked type="OMG">
Whoa.. **"WEBCAM"** support?!?!  In LOONIX?!*
</shocked>

Very cool.  :) 

*My webcam actually does work in Linux.. spca50x drivers compiled nicely.. I just don't have a app to use it with other than Camstream (local only, no broadcast).

---

### Post by drizek on 2005-08-26
kopete 3.5 will also, IIRC, have skype support.

I just hope google talk kills off the competition so we dont have to deal with this crap anymore. :)

gtalk is the only IM protocol that actually encourages people to use alternative IM clients. theres a lot of talk about big bad google now, but until their competition can provide a good and _open_ alternative, im gonna support them.

---

### Post by f1dave on 2005-08-26
[QUOTE=drizek]kopete 3.5 will also, IIRC, have skype support.

I just hope google talk kills off the competition so we dont have to deal with this crap anymore. :)

gtalk is the only IM protocol that actually encourages people to use alternative IM clients. theres a lot of talk about big bad google now, but until their competition can provide a good and _open_ alternative, im gonna support them.[/QUOTE]

Hear, hear.

And what's more, can we PLEASE have a better buddy icon setup than what is in kopete now? What were they thinking?!? :(

---

### Post by drizek on 2005-08-26
no skype support, but

> 
New toolbar(widget) in main window to edit your global identity. Michaël Larouche <michael.larouche@kdemail.net>
Add support for multiples global identities(like KMail and Konversation) Michaël Larouche <michael.larouche@kdemail.net>
Allow select the media player in NowListening plugin. Michaël Larouche <michael.larouche@kdemail.net>
Set globally busy or invisible Olivier Goffart <ogoffart @ kde.org>
Set a nickname and a photo globally (called global identity) in a configuration module. Michaël Larouche <michael.larouche@kdemail.net>
Improve system tray flash notification behavior Jan Ritzerfeld <kde@bugs.jan.ritzerfeld.net>
Emoticon in the contact list, and in tooltips Engin Aydogan <engin @ bzzzt.biz>
Add dcc (p2p) facility to Gadu-Gadu, no voice messaging, only file transfer. Grzegorz Jaskiewicz <gj@pointblue.com.pl>
Add support for receiving Yahoo webcams Chetan Reddy <chetan13@gmail.com>
Add filetransfer Support Andre Duffeck <andre.duffeck@kdemail.net>
Add buddy icon support for Yahoo Andre Duffeck <andre.duffeck@kdemail.net>
Add Yahoo Stealth Feature Andre Duffeck <andre.duffeck@kdemail.net>
Add Buzz! Feature Andre Duffeck <andre.duffeck@kdemail.net>
Add Richtext formatting of Yahoo Messages Andre Duffeck <andre.duffeck@kdemail.net>
Support Yahoo Addressbook Andre Duffeck <andre.duffeck@kdemail.net>
Add buddy icon support (sending and receiving) to AIM Matt Rogers <mattr@kde.org>
Support of global identity (nickname) in Jabber. Michaël Larouche <michael.larouche@kdemail.net>
Port MSN plugin to use MSNP11 (MSN7) Michaël Larouche <michael.larouche@kdemail.net>, Gregg Edghill <gregg.edghill@gmail.com>
Support sending and receiving of personal messages in MSN plugin. Michaël Larouche <michael.larouche@kdemail.net>
Support of global identity (nickname and photo) in MSN. Michaël Larouche <michael.larouche@kdemail.net>
MSN HTTP support. Gregg Edghill <gregg.edghill@gmail.com>
Support of sending MSN Messenger 7 "Nudge" Olivier Goffart <ogoffart @ kde.org>
MSN webcam support Olivier Goffart <ogoffart @ kde.org>
Preview of latex formulas in messages. Olivier Goffart <ogoffart @ kde.org>


is a good start. a lot of the major problems will be dealt with, so im happy. kopete just lacked developers before, and after kde 3.4 was released, teh head dev asked for some help and a few new devs came on board and started helping out. the problem is that we wont be getting any feature updates for another year. however, they have already begun porting kopete to QT 4, so they have a whole year to improve and tweak kopete. I cant wait for kde 4 :)

---

### Post by Haegin on 2005-08-29
EDIT: I'm an idiot. I retried the svn install and found ./compile wasn't finishing properly. Ok, you can all laugh now...

Is there any debain package around for the current development build of kopete? I see on the list on the kde website they have finished msn voice chat and I was hoping to be able to get hold of the svn version but when I went to download it I came across problems. The instructions from the kde website are as follows:

```
svn co -N svn://anonsvn.kde.org/home/kde/branches/KDE/3.5/kdenetwork
cd kdenetwork
svn up kopete
svn co svn://anonsvn.kde.org/home/kde/branches/KDE/3.5/kde-common/admin
make -f Makefile.cvs
./configure --enable-debug
[COLOR=Blue]cd kopete[/COLOR]
[COLOR=Green]make[/COLOR]
su -c "make install"
```

When I changed to the kopete directory (step highlighted in blue) it couldnt find the makefile and so could not complete the make command in the next step (in green).

Any ideas or debian packages?

---

### Post by skoal on 2005-08-29
[QUOTE=Human Prototype]Any ideas or debian packages?[/QUOTE]
You more than likely need some -dev packages.  I bet the ./configure script puked somewhere along the way before it actually gen'd the Makefiles.  Try this:

sudo apt-get install zlib1g-dev libjpeg62-dev libqt3-dev libqt3-mt-dev kde-devel

* That's a huge chunk of change there, and bound to take up several hundred more megabii on your drive.  That should get you through the ./configure section though, and fix your missing 'makefiles'...

\\//_

---

### Post by f1dave on 2005-09-03
Whilst waiting on the next version of kopete to judge, I've tried leaving gaim behind (as good as it is) for something I saw on kde-apps RSS feed the other day, KMess. Now this is of course useless for anyone using things other than msn, but it does it's job nicely for that protocol anyway.

Msn users may want to give it a go.

---

### Post by jaac on 2005-09-03
[QUOTE=Mishura]True, true.  However, there are things that Gaim has been capable of doing now for about a year such as File Transfering on the AIM protocol, (in fact, all but MSN so I hear), while Kopete can only File Transfer on the MSN protocol (And maybe Jabber).  Its funny, because, if they were to at least share some ideas together, then both clients would support FTs on all available protocols.   Not to mention that Gaim has buddy icon support (Needed unfortunately,  I got friends who are like "D00d, look at my 4vatar!!",)  and Kopete doesn't support any kind of that except maybe MSN.


To basically summarize (Long post I know..):

Kopete advantages:

1.  Integration with the KDE desktop, PIM, and other applications.
2.  Less memory usage (Subjective.  I think Kopete is "snappier". )
3.  Very good UI.
4.  Metacontacts.
5.  Themable.

Kopete disadvantages:

1.  No buddy icons
2.  No File Transfer
3.  No Direct IM
4.  I can't set my user alias like I can do with Gaim (I have 3 user accounts with different names.  I want all to say "Mishura")
5.  Doesn't share contact lists with AIM, or others.  Uses its own system.  (If I add a buddy in Kopete, it won't show up in Gaim, or AIM in Windows, and vice versa)[/QUOTE]

You can see the buddy's icons using a diferent style for the chat window, try this style: [http://www.kde-look.org/content/show.php?content=23473](http://www.kde-look.org/content/show.php?content=23473)

---

### Post by dcostelloe on 2005-09-05
Have you tried AMSN?

Works great I use it all the time to replace my win MSN Messenger.

 [-X 

You can download it from here [MSN Messenger for Linux](http://amsn.sourceforge.net/)

---

### Post by f1dave on 2005-09-06
aMSN is great except it looks ugly (although this is replaceable with gtk or qt-style addons i have now noticed) and last time I tried it it had a nasty habit of crashing and/or not starting up at login.

---

