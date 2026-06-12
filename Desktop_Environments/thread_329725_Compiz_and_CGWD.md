---
title: "Compiz and CGWD?"
date: 2007-01-02
forum: Desktop Environments
---

### Post by rayzon on 2007-01-02
Greetings,

I have spent several hours now trying to resolve this Compiz issue.

I had a successful install, but when I try to change themes, I get nothing.  I can click on the theme I want to use, but nothing happens.

While digging around for posts with similar issues, I found a few that helped me along.  The fix I have tried to utilize (seems most like my problem) requires that I do the following:

> --------------------------------------------------------------------------------

When you have all setup and you have the repo's enabled you should install

sudo aptitude install cgwd cgwd-themes cgwd-themes-extra

And the latest compiz works with csm.

needed repo's:

deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main

Put this to your sources.list and

sudo aptitude update

Now you can install the latest compiz packages like csm and cgwd etc.

Go to your sessions and remove everything what points to compiz like compiz-start or compiz-start.py or the future.

Put /usr/bin/compiz-start in your sessions menu and logout and login.

Now you should have in preferences two new Icons,Compiz Settings Manager and CGWD Themer.


(from the thread [http://www.ubuntuforums.org/showthread.php?t=259661&highlight=from+the+compiz+installation+walkthrough]("http://www.ubuntuforums.org/showthread.php?t=259661&highlight=from+the+compiz+installation+walkthrough") )

My problem is that every repo that I have found that offers the cgwd-themes and cgwd-themes-extra is a NO GO.

I added the repos in the quoted thread and dug around for others.  However, after reloading the packages in Synaptic, a search for cgwd comes up with nothing.

I managed to find cgwd-themes_0.16.orig.tar.gz  &  cgwd-themes-extra_0.3.orig.tar.gz and save them in my home folder.  I figure I can use these, but how do I implement them?

Thanks.

(p.s.  I didn't want to mention this with my first post, but I am a newbie, so please have some mercy and overlook my ability to ramble.)  :D

---

### Post by rayzon on 2007-01-06
WOW!!  Is the question difficult? retarded? played out?  Not so much as a "look here" or "piss off"

Thanks.

---

### Post by face4radio on 2007-01-07
Hmm, I would tell you where to look, but I dont know...soooo...how about PISS OFF!!

Smooches,
Turtle Jelly

---

### Post by rayzon on 2007-01-07
AWESOME!!!! A reply, finally.

Well, since anticipating  help within these forums is fruitless, how about we talk about something more likely to produce a reply.

How about guacamole?  Is it strictly a dip? or can it also be classified as a spread?  Discuss.

](*,)

---

### Post by face4radio on 2007-01-07
I LOVE guacamole!! Perhaps your last post rendered no responses because you werent detailed enough in your question. In an effort to assist you on your latest quest, here is a little information about Guacamole for the "UMPFH" readers!

Guacamole, a dip made from avocados, is originally from Mexico. The name is derived from two Aztec Nahuatl words - ahuacatl (avocado) and molli (sauce). The trick to perfect guacamole is using good, ripe avocados. Check for ripeness by gently pressing the outside of the avocado. If there is no give, the avocado is not ripe yet and will not taste good. If there is a little give, the avocado is ripe. If there is a lot of give, the avocado may be past ripe and not good. In this case, taste test first before using.

2 ripe avocados
½ red onion, minced (about 1/2 cup)
1-2 serrano chiles, stems and seeds removed, minced
2 tablespoons cilantro leaves, finely chopped
1 tablespoon of fresh lime or lemon juice
1/2 teaspoon coarse salt
A dash of freshly grated black pepper
1/2 ripe tomato, seeds and pulp removed, chopped

Garnish with red radishes or jicama. Serve with tortilla chips.

1 Cut avocados in half. Remove seed. Scoop out avacado from the peel, put in a mixing bowl. (See How to Cut and Peel an Avocado.)

2 Using a fork, mash the avocado. Add the chopped onion, cilantro, lime or lemon, salt and pepper and mash some more. Chili peppers vary individually in their hotness. So, start with a half of one chili pepper and add to the guacamole to your desired degree of hotness. Be careful handling the peppers; wash your hands thoroughly after handling and do not touch your eyes or the area near your eyes with your hands for several hours.

Keep the tomatoes separate until ready to serve.

Remember that much of this is done to taste because of the variability in the fresh ingredients. Start with this recipe and adjust to your taste.

3 Cover with plastic wrap directly on the surface of the guacamole to prevent oxidation from the air reaching it. Refrigerate until ready.

4 Just before serving, add the chopped tomato to the guacamole and mix.

Serves 2-4.

Variations

For a very quick "guac" just take a 1/4 cup of salsa and mix it in with your mashed avocados.

You don't need to have tomatoes in your guacamole. 

To extend a limited supply of avocados, add either sour cream or cottage cheese to your guacamole dip. Purists may be horrified, but so what? It tastes great. In fact, guac with some cottage cheese added to it is my favorite.

---

### Post by rayzon on 2007-01-07
man, I can taste the green goodness already.  I'm off to the store.  Thanks for the info!!!

---

### Post by face4radio on 2007-01-07
Glad to be of service. If we cant help each other, what is the purpose of this message board? 

Eat some gwak-uh-mole-ee for me muh kneegrow!

---

### Post by g8m on 2007-01-08
This is/was a "read the source Luke" question. How about starting with unpacking those zipped files and look what's in them. Maybe there's a source in them you have to compile and set up. Maybe there's a README in it what will tell you what to do. Maybe there's a .deb file in them which can be installed with dpkg. 

Read the source, do some digging, experiment, crash it, learn. Don't depend on others to do your thinking.

No flame intended.

---

### Post by rayzon on 2007-01-08
> I have spent several hours now trying to resolve this Compiz issue.


I did do my own work.  I did unpack the files.  I am new to Ubuntu and Linux altogether (as noted in the third quote) so of course when I unpacked the zipped files, my **new user** self looked for anything to execute.  After wondering if I was ever going to get a reply, I just executed anything I could find in the unzipped folder (I figured I was going to re-install Ubuntu anyway) but nothing worked for me.  The readme files were worthless as far as i could tell (they listed ppl getting props and other info that didn't offer any installation/utlization help).  

Now see, the .deb file you mention, .deb + dpkg (new guy here knows absolutely nothing about making these connections, simple as they may be, and appreciates getting something from anybody.  Now I can add this to my list of commands and pages of notes.)


> I managed to find cgwd-themes_0.16.orig.tar.gz & cgwd-themes-extra_0.3.orig.tar.gz and save them in my home folder. I figure I can use these, **but how do I implement them?**but how do I implement them?

Here, **how do I implement them?** Like I said, I unpacked them, but, well, I think you get the picture.


> (p.s. I didn't want to mention this with my first post, but I am a newbie, so please have some mercy and overlook my ability to ramble.):confused: :confused: :confused: confused new user :confused: :confused: :confused: :confused: 



I was hoping to have someone point me in the right direction and tell me **how** to implement a zipped file that is in my home folder or at least give me a lead as to where to find the information so I can learn it myself.



Believe it or not, your "reprimand" gave me a little more info in order to try to solve the problem.  I understand that you were not flaming me and I am certain that you will not interpret my reply in such a manner.

As I said, I did dig.  I spent many hours (on this forum and others) trying to find anything that would help me figure out what I was doing wrong.

Thanks ;)

---

### Post by mannheim on 2007-01-08
"cgwd" became "emerald", which is now the default themer for beryl.

So, to use cgwd themes, you need to use beryl in place of compiz, and then import the cgwd themes using the emerald theme manager.

---

### Post by rayzon on 2007-01-08
NOW were cooking with Crisco.

Thanks.

I will give that a shot.

(next cup is on me :)  )

---

### Post by face4radio on 2007-01-08
HA! Now THERE is a good response!:)

---

### Post by itsjustarumour on 2007-01-13
Another noob here, and I've been having the same problem...  I installed Compiz/XGL using the howto at [http://doc.gwos.org/index.php/XGL_Compiz(32bit)Nvidia](http://doc.gwos.org/index.php/XGL_Compiz(32bit)Nvidia)   This gave me my lovely 3D cube and wibbly wobbly windows and stuff, but no means of changing Compiz themes.  Checking back, I realised that when I'd typed

sudo apt-get install xserver-xgl compiz-gnome cgwd cgwd-themes

into the terminal, it gave me this:

ian@COOLERMASTER:~$ sudo apt-get install xserver-xgl compiz-gnome cgwd cgwd-themes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xgl is already the newest version.
compiz-gnome is already the newest version.
Package cgwd is a virtual package provided by:
  emerald 0.1.1-0ubuntu1
You should explicitly select one to install.
E: Package cgwd has no installation candidate
ian@COOLERMASTER:~$ 

Aha!  thinks I. Theres my answer, cgwd now replaced by emerald, so off I went to Synaptic and downloaded and installed emerald 0.1.1-0ubuntu1.  This created the emerald menu, with lots of tasty looking themes to try out - yay!  But of course, as soon as I try and select any of them, absolutely nothing happens...

Now this is where I suddenly feel a bit nervous...  

> **mannheim said:**
> "cgwd" became "emerald", which is now the default themer for beryl.

So, to use cgwd themes, you need to use beryl in place of compiz, and then import the cgwd themes using the emerald theme manager.

I've been reading a lot on these forums like the good conscientious student of Ubuntu magic that I at least endeavour to be, and seen many times that installing Compiz and Beryl at the same time is A Very Bad Idea Indeed.  So whats the best (ie safest) way "to use beryl in place of compiz, and then import the cgwd themes using the emerald theme manager"? Do I have to install the whole of Beryl first to do this? :-k

---

### Post by itsjustarumour on 2007-01-13
Well, I've been through the forums for a second time and can't find an answer to this.  Although I have discovered that by opening a terminal and typing:

$ emerald --replace

or

$ metacity --replace

I can switch between the two themers.  Presumably my system is still defaulting to Metacity, however when I type $ emerald --replace this removes the title bars from all my windows!  And even with this, I still can't change the Emerald themes :-| 

I'm now getting rather confused as so many of the howtos seem to be out of date, and there are so many conflicting opinions on what and what not to do.  Many people seem to be using Beryl, but I'd originally gone for Compiz because I want stability more than the bleeding-edge option and consensus seemed to be that Compiz was more stable than Beryl.  

I know its getting late and I haven't had my mug of Ovaltine yet... or is there something really obvious I'm missing.  :confused:

(Edgy, Gnome 2.16, NVidia 8776 driver btw...)

---

### Post by itsjustarumour on 2007-01-14
BUMP.  

Anyone?  Is Compiz on Ubuntu now a dead project, and everyone using Beryl?  Does CGWD still exist? Do I have to go back to openSUSE if I want to use Compiz? :-|

---

### Post by itsjustarumour on 2007-01-14
Bump Bump.

---

### Post by itsjustarumour on 2007-01-14
OK, I've been over to the official Compiz Forums at  [http://forum.go-compiz.org](http://forum.go-compiz.org) and now see that what Mannheim was saying in his earlier post was basically "scrap Compiz altogether, and use Beryl". There are several other posts on these forums talking about Compiz/CGWD/Emerald, which are very misleading or just plain WRONG (often because they are completely out of date!)

And then theres this, from elsewhere in these forums [http://www.ubuntuforums.org/showthread.php?t=308606&page=5&highlight=compiz](http://www.ubuntuforums.org/showthread.php?t=308606&page=5&highlight=compiz)

>>>"The "compiz" packages in edgy's universe repo are actually beryl from back when it was called compiz-quinn."<<<

So - "Compiz" from the official Edgy Repositories is actually an old version of Beryl!  NO WONDER I WAS CONFUSED!!!  

Anyways, THANKFULLY theres a new up-to-date howto at:

[http://forum.go-compiz.org/viewtopic.php?t=90](http://forum.go-compiz.org/viewtopic.php?t=90)

This is aimed at getting Compiz running on Edgy 6.10 with the latest NVidia driver, and looks much more promising than any of the howto's I've found on the Ubuntu Forum pages!

I'll be giving it a shot and and will report back on the results... :)

---

### Post by mannheim on 2007-01-19
itsjustarumor, I wasn't advocating beryl over compiz. I'm actually using a recent version of compiz myself at the moment. My earlier post was just to explain the cgwd theme issue.

My own experience right now is that compiz has fewer bugs than beryl -- or at least, fewer bugs that affect me. But this changes from version to version.

---

### Post by rayzon on 2007-01-31
itsjustarumor, thanks for all the input.  It seems you can feel the pain I was enduring dealing with this problem.  Your research and updates are helpful

So, the machine I was working on had to go back to my buddy's house (it was his and I was taking advantage of the opportunity to learn on his stuff before damaging mine ;) ), anyway I am about to take on the task of Ubuntu-ing my own comp.

What would you recommend as your final solution to this whole debacle?  Compiz? Beryl?

---

### Post by tim356 on 2007-02-01
I too would like to hear your opinion/advice on which to go with (although after reading all of that, beryl seems like the way to go, does it not?).

---

### Post by joecoin on 2007-02-01
I've spent a lot of hours attempting to get Beryl installed. I have tried 3 different Nvidia cards. I have tried all the Nvidia drivers with each card, just to make certain that I tested all possibilites.

The open source community is a wonderful thing. The biggest issue I have with it is the lack of cohesive, current support. No, I don't want someone to hold my hand and do all the work for me. It's just that with all the differing "how to's" out there, I've become disilluisioned.


And I hate Guacamole.

---

### Post by itsjustarumour on 2007-02-01
Mannheim &#8211; OK, point taken, and thanks for your comments :) 

Rayzon (and Tim) &#8211; I never actually managed to resolve this unfortunately.  After posting here I took advice from the experts on the official Compiz forum at [www.go-compiz.org](www.go-compiz.org) but hit more problems that eventually broke my system. My strong suspicion is that I had THREE separate issues:

1. There are lots of bugs in Compiz!  (OK, no news there then&#8230; ;-)  )
2. When I tried installing newer versions of Compiz along with the updated NVidia 9631 and 9746 drivers, I made myself vulnerable to this issue here [http://ubuntuforums.org/showthread.php?t=318206&highlight=compiz+kernel+update+NVIDIA](http://ubuntuforums.org/showthread.php?t=318206&highlight=compiz+kernel+update+NVIDIA) (I&#8217;d previously updated my system with all the Ubuntu automatic updates, which didn&#8217;t cause any problems with my old 8776 driver, just the newer ones)
3. For some unfathomable reason, the official NVidia drivers don&#8217;t like my particular graphics card (a Leadtek GeForce 6800LE) when used together with Compiz (also my card never seemed to be officially recognised by Alberto Milone&#8217;s &#8220;Envy&#8221; program etc etc &#8211; a possible clue?)

Anyway, after at least seven re-installs, trying three different versions of Compiz (and also Beryl, which reproduced exactly the same problems as Compiz), repeated issues with xorg.conf, xserver, blue screens, blank white screens instead of a desktop and &#8220;mismatched kernel modules&#8221; &#8211; not to mention almost 50 hours of my life in effort, research and experimentation - I&#8217;ve finally had to admit defeat.  ](*,)  Frankly, I&#8217;d reached the point where I was starting to smell a bit, my girlfriend was threatening to leave me and I needed to catch up with all the other things in my life!  :roll:  There may well be (kernel-related?) solutions to my problems, but right now unfortunately I can&#8217;t afford to spend any more time on it.

So - I&#8217;ve put my Ubuntu box to one side - for now!  To be honest, after 3 months of effort I&#8217;ve never managed to produce a system that had 3D acceleration, wireless networking and Compiz/Beryl all working at the same time.  I DO love Ubuntu, but I think I&#8217;ll wait for Feisty to see if these things work a bit more smoothly there.  In the meantime I don&#8217;t think Edgy 6.10 is quite close enough to being a workable desktop replacement for the dreaded Windows (unless you&#8217;re either a software engineer/developer or else have huge amounts of spare time to devote to it), which at least I know I can rely on to actually boot to a Desktop every morning and allows me to Just Get Things Done &#8482;&#8230; 

So &#8211; sorry if this wasn&#8217;t quite the answer you needed, but back to openSUSE 10.2 and WinXP/Vista for me!  In the meantime, my advice to anybody contemplating Compiz /Beryl is - if you want to use it on your day-to-day main desktop PC &#8211; don&#8217;t!!  Incredibly beautiful and tempting as the bait maybe, read the words CLEARLY STATED on both the official Compiz and Beryl sites &#8211; &#8220;This software is VERY ALPHA, and NOT to be used on PRODUCTION MACHINES&#8221; &#8211; and believe every one of those words!! 

Anyway, good luck with your own efforts on this - I'll still be keeping on eye on the posts here to see how Ubuntu/Compiz develops - and not too long unitl Feisty now, I can't help feeling excited about it, despite my above comments!  :biggrin:

---

### Post by itsjustarumour on 2007-02-01
My biggest problem with guacamole is, its so easy to mistake it for mushy peas...  :mrgreen:

---

