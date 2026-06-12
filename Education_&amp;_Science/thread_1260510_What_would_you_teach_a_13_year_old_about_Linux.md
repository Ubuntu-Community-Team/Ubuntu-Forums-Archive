---
title: "What would you teach a 13 year old about Linux?"
date: 2009-09-07
forum: Education &amp; Science
---

### Post by Prospero2006 on 2009-09-07
Hello All,

This is my second year teaching a programming-Ubuntu/Linux management class at the middle school level. I'm looking for ideas on applications/concepts I can get the kids, who are smart and motivated, working with. 

**Here are my lesson plans from last year:**

[http://www.neisd.net/imak/lessonplans/beck](http://www.neisd.net/imak/lessonplans/beck) (Look for the Advanced Linux Programming section on the right)

In short, we learned how to manage the system, worked with C, and did a unit on php programming where we wrote a card game that utilizes mysql. 

[http://moodle.neisd.net/live/loginform.php](http://moodle.neisd.net/live/loginform.php)

--That's an example student project from our php unit.

Here are my lesson plans for this year:

[http://www.linuxclassroom.com/0910lessonplans](http://www.linuxclassroom.com/0910lessonplans)

In the first two weeks this year we have:
   -Learned about adduser
   -Configured ccsm and compiz from top to bottom
   -Worked with basic commands like cp, mv, ls, rm. 
   -Learned to burn a live cd.
   -(At Present) --We are learning to configure the live CD from
   the ground up.


I was thinking about teaching bash scripting followed by a unit on java/android programming:

[http://www.linuxclassroom.com/androidclass](http://www.linuxclassroom.com/androidclass)

However, I'm always interested in listening to the community here. These kids love fun applications that are relevant. 

So, my question:
  If you had a group of 12-13 year olds that really wanted to learn about Linux, what would you teach them?

Thanks!

---

### Post by denver on 2009-09-07
I hardly know any 13 year old that is interested in programming, but I'm happy to hear that kids are interested in such things.

I guess i would teach them how to navigate through the OS and get confortable for a while. Teach them every day tools and apps for web browsing and multimedia.

If they really are interested in programming, I personally would give them a short introduction into shell/perl scripting, maybe a little regular expressions (for those that like small and dirty scripts). If you are aiming for portabillity then Java is ok, so is Mono (C#). If you want to teach them web programming, go for python or ruby on rails. Its prety easy to learn and you get nice results, fast. A quick google search will give you a lor of webcasts on how to program in ruby.

> I was thinking about teaching bash scripting followed by a unit on java/android programming:

[http://www.linuxclassroom.com/androidclass](http://www.linuxclassroom.com/androidclass)

Thanks for the site. I'm getting an Android phone soon. This will come in handy :).

Best regards!

---

### Post by Prospero2006 on 2009-09-07
Ruby. I've thought about that. I'll have to give it some consideration.
Thanks,
Josh

---

### Post by Girya on 2009-09-08
I wasn't able to open the link to your last year's lesson plan so excuse me if my suggestions are redundant.

I've got a smart 12 yo. Too smart sometimes:). I've introduced linux to him through things that interest him: music and games. I've taught him shell scripting commands so he can listen to music then turn off the desktop automatically after he's gone to bed($shutdown -P 23:00). 

You might want to look at command line apps that they could use in everyday life: email mutt, music cmus, internet lynx. There's got to be hundreds of them: cal, calendar, todo.sh. Also I've got to throw in sed, awk and grep. 

One thing that really helped me to understand linux was grinding my way through linux from scratch: [http://www.linuxfromscratch.org/]("http://www.linuxfromscratch.org/")

---

### Post by meborc on 2009-09-09
+1 for Ruby - [http://www.ruby-lang.org/en/](http://www.ruby-lang.org/en/)

---

### Post by Prospero2006 on 2009-09-09
> **Girya said:**
> I wasn't able to open the link to your last year's lesson plan so excuse me if my suggestions are redundant.

I've got a smart 12 yo. Too smart sometimes:). I've introduced linux to him through things that interest him: music and games. I've taught him shell scripting commands so he can listen to music then turn off the desktop automatically after he's gone to bed($shutdown -P 23:00). 

You might want to look at command line apps that they could use in everyday life: email mutt, music cmus, internet lynx. There's got to be hundreds of them: cal, calendar, todo.sh. Also I've got to throw in sed, awk and grep. 

One thing that really helped me to understand linux was grinding my way through linux from scratch: [http://www.linuxfromscratch.org/]("http://www.linuxfromscratch.org/")

TY--
We're doing command line basics right now and I think a primer on sed and awk would definitely come in handy. Probably going to hit them with redirection using > and | first. Then do some basic parsing, searching, and replacing.... Build some solid proficiency before we jump into a language like python or whatever.

Thanks again,

---

### Post by hubie on 2009-09-11
Wouldn't teaching Ruby or web programming be going a bit far afield considering that it is an advanced linux class?  For instance, you can get a Ruby environment up and going on Windows.

I would think you would want to emphasize the things that make linux unique, or at least different than Windows, or work on the things that let you use linux in a general environment, such as surrounded by Windows users.  Basic unix skills, such as shell programming, is a must.

The things I think would be interesting:
[LIST]
[*]LiveCDs (which you mention)
[*]Minimal installs (different desktops, or switching and/or running desktops that aren't Gnome or KDE)
[*]Different distributions (such as, make sure things are installed such that you can easily switch distributions without killing your home partition, or your mp3 collection)
[*]File serving (for a home network, perhaps as the PDC for a home domain)
[*]Firewall/gateway with vpn access from outside
[*]RADIUS/LDAP server for wireless access authentication and/or captive portal application
[*]Multimedia platform and/or perhaps as a MythTV-like setup
[*]If you have any hardware resources (Playstation 3, or something like one of [these little guys]("http://www.marvell.com/products/embedded_processors/developer/kirkwood/sheevaplug.jsp") or some other kind of [plug computer]("http://www.openplug.org/")), then an "embedded"-like, or tiny install (or if you don't worry about splitting hairs between linux and bsd, then setting up one of the WRT-based systems)
[*]Cluster computing, even if it is only clustering a handfull of them
[*]Virtualization and Wine (maybe doing the clustering from within a completely virtualized network)
[/LIST]

In short, I would stay away from the program language things unless they are essential to what you want to accomplish.  Otherwise you risk losing the focus from "using linux to do X" to "how to do X on linux."  The latter is fine, but I would think it is not the intent of your course.  I think that no matter what your focus ends up being, it would be most useful to the students if they came away knowing how to set up and run linux in a Windows world without any hiccups, or at least knowing how to get around those hiccups.  We all know there are plenty of people who will tell you that they like the idea of linux, but they could never use it/switch to it because linux just can't do such-and-such.  A course like yours can show them that not only can they do pretty much whatever they want, but they perhaps can do it much better with linux than other ways.

---

### Post by aesis05401 on 2009-09-11
Teach pattern matching concepts, then choose a few different pattern matching mechanisms to practice.  Iptables rules, recursive text searching from the command line... 

I would use this foundation to illustrate the design philosophy behind *nix CLI tools.  A few ways to do this would be to pipe wget results through your favorite stream editor to manipulate/analyze web content, select files by matching magic numbers or mime types and then pipe to a format conversion utility etc..

This seems like the simplest of the truly powerful Linux technologies to teach.

---

### Post by tgalati4 on 2009-09-11
Have them set up their own facebook/blog/drupal server.  That would allow them to interact with the server from home and create their own content.

Kind of a 2009 version of [foxfire]("http://www.foxfire.org/magazine.html").

Some interesting trends in education:

[http://ia301514.us.archive.org/2/items/SouthEast_LinuxFest_2009/Greg_DeKoeningsberg_SouthEast_LinuxFest.ogg](http://ia301514.us.archive.org/2/items/SouthEast_LinuxFest_2009/Greg_DeKoeningsberg_SouthEast_LinuxFest.ogg)

[http://disruptingclass.mhprofessional.com/apps/ab/](http://disruptingclass.mhprofessional.com/apps/ab/)


&#729;&#477;s&#633;no&#596; &#607;o 'u&#653;op &#477;p&#305;sdn &#477;&#647;&#305;&#633;&#653; o&#647; &#653;o&#613;

---

### Post by -_- Joseph -_- on 2009-09-11
Pretty much whatevery one else says sounds pretty good but i wish got got to learn something like this when i was in middle school.
we just did binary and making webpages. (which i already new before hand)

---

### Post by Prospero2006 on 2009-09-11
Great responses:

Piping wget through a stream editor is a really great idea. I'm about to get to wget next week and that would make a really neat way to test their proficiency. (We spent the last 2 days talking about ip addresses and ports. --Used telnet to issue a GET request to a web server. I think wget like that would make a really good follow up.)

I agree that basic setup and installation is key, but I want the kids to learn basic programming languages, too. They're pumped up about learning to program for the Google phone and I'd like to follow up and get them to a point where they can handle basic Java.  (BTW: Right now the whole class can boot a live CD, update sources.list, configure firefox to use the school proxy, and show me 26,000 programs available for install on Synaptic in under 10 minutes. 26 kids. Every single one of them did it right today.)


I think maybe bash scripting would be a good start. Give them some basic commands and have them automate/improve the functionality through some basic scripting. --Get them used to variables and loops and such....

Anyway, keep the ideas coming. Any suggestions on bash scripting for beginners would be appreciated in particular. I'll be reviewing my own material this weekend and thinking about how to teach it.

Ty everyone,
Josh

---

### Post by shadow12 on 2009-09-20
Well I know that i liked the time that we spent on the mud last year. Maybe you should teach this years class some about the mud and then should teach some other type of programing other then php since you did that last year, something that would keep the students interested like php did for us last year.

---

### Post by Prospero2006 on 2009-11-23
Hey shadow,
Actually, Just put the mud back up. 
It's in much better shape. Lot of work went into it this year.

[http://www.imakmud.com](http://www.imakmud.com)

Mr. Beck

---

### Post by samden on 2009-11-23
iMak Mud looks pretty cool! 

It brings back memories of a text-based game I spent hours playing at primary school on an Apple IIGS (early '90s). You were marooned on an island by pirates and had 24 hours to explore the island and figure out a way to get off. I drew maps on maths paper to help me get around. Wish I could remember the name of it. Ah, the memories...

It even showed you colour pictures when you reached certain places. About 6 colour pictures I think in the entire game. We thought it was so flash!

---

### Post by spinoza666 on 2009-11-23
> **Girya said:**
> One thing that really helped me to understand linux was grinding my way through linux from scratch: [http://www.linuxfromscratch.org/]("http://www.linuxfromscratch.org/")

Thanx for the URL. Great site. Been wondering about doing something like that, to learn basically, and now it doesn't seem so impossible anymore.

---

