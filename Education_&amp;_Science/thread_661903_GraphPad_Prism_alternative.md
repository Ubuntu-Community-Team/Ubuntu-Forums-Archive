---
title: "GraphPad Prism alternative?"
date: 2008-01-08
forum: Education &amp; Science
---

### Post by rmores on 2008-01-08
I'm currently looking for a substitute for GraphPad Prism software(Windows/MAC) in linux for a friend that wants to use linux in her home/work computer, I wonder if anyone out there knows about it, or has worked with similar software in the past.

From their website:
"GraphPad Prism is a powerful combination of basic biostatistics, curve                                   fitting and scientific graphing in one comprehensive                                   program. More than 100,000 scientists in over 100 countries rely on                                 Prism to analyze, graph and present their scientific data."

The software is different from similar Office suits for Graphs because it has specific biochemistry uses.

---

### Post by thisismalhotra on 2008-01-08
Did you try GNUplot or SCILAB yet??
Don't know if they work for you but they work for me fine in signal processing

---

### Post by rmores on 2008-01-10
I'll have a look at those and post my opinion here, then. Thanks :)

---

### Post by plvera on 2008-01-10
I guess it depends on how much work with statistics your friend does. I recommend R because is free and it's a far more powerful (and flexible) program than Prism.  I used Prism for many years but then found R.

The downside is that the learning curve for R is rather steep. At any rate, it's worth examining as an option.

Good luck!

---

### Post by rmores on 2008-01-12
Thanks for the tip. Can you give me a link to that one? R is too short to search for it...

---

### Post by rmores on 2008-01-12
Nevermind, I found it at [http://www.r-project.org/](http://www.r-project.org/)
I'll look into it tomorrow.
GNUplot and Scilab won't be much useful but look interesting for other areas.

Cheers

---

### Post by jwferk on 2008-08-16
I use GraphPad as the company standard (pharmaceutical industry) when I'm at work.

I use LabPlot at home.  Xdrawchem in place of ChemDraw.

Both can be found in the ubuntu repositories.

---

### Post by lunatico on 2008-08-21
Hi!

I'm in the exact situation here. My nerd friend wanted Linux on her computer but now she needs something similar to GraphPad Prism. She is into Neuroscience in case it matters. So what is the best option so far?

Cheers!

---

### Post by NikoC on 2008-08-22
Well I'm a biologist/biochemist doing his phd in the field of ecotoxicology and so far R has fulfilled all my needs (statistics, plotting, making high quality graphs).
You just have to put in some effort but once you've got the hang of it, it's awesome!
And you can use it anywhere by which I mean: no expensive licensing, available for any platform...

---

### Post by lunatico on 2008-08-23
Hey! Just a heads-up on this. My friend is a neuroscientist and I'm a computer scientist so when I asked her what she needed this for she started explaining me and my brain went BSOD as in: windows blue screen... :confused:
So... she wanted GraphPad Prism, well GraphPad Prism she gets...
Installed Wine... downloaded GraphPad windows version and installed it. It work like a charm and she was happy. :)
Of course this is not an open source software, licensing issues and all that... but that is a different story... ;)

---

### Post by paulchinnz on 2009-11-06
Hi which version of Prism worked with Wine? I've heard some versions install fine but then have some memory problems when you actually try to create a graph and you can't actually do anything.

---

### Post by dunkeld on 2010-01-17
Hello
I think I have good news to all GraphPad enthusiasts missing it on Ubuntu.
I was checking different versions of wine, and its setups but finally it turned out that  application called PlayOnLinux ([http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)) was the solution. It was enough to install GraphPad (5.03) trough it by choosing option "install application not mentioned on the list" and next just keep clicking "next" button. When POL asked for environment name I just wrote "windows" and when it asked to setup wine, I just left it as it was by default. Amazingly after that GraphPad works as well as under windows. I can save and open documents and export plots or graphs to all supported graphical formats.  I was able to do nonlinear fit to my data, transform them, do basic statistics on columns, anova, copy table of results to layout, use greek symbols in axes description and export final graph to pdf and jpg. Everything I have tried until now works perfectly! I am looking forward to see if it will work for others. I know R is cool, but not everyone has time to get know it and for many purposes GraphPad is more than enough. My wine version is 1.1.25.
best regards
chris

---

### Post by Maxei on 2010-04-14
@Dunkeld,

Thanks for the information. I am a graphpad prism5 user and need to work under windows at the job. This is one of the few windows applications that push me to stick on windows. With wine I can run Photoshop and a few others under Ubuntu. Because I have not tried Prism5 under wine (I thought it would be impossible yet), I'm very curious about the PlayOnLinux thing. Can you explain why it is needed? I thought that just installing wine then run your application would do it. Please post more details as it seems that you need to create scripts, if-INW. Thanks.

---

### Post by meborc on 2010-04-15
> **Maxei said:**
> @Dunkeld,

Thanks for the information. I am a graphpad prism5 user and need to work under windows at the job. This is one of the few windows applications that push me to stick on windows. With wine I can run Photoshop and a few others under Ubuntu. Because I have not tried Prism5 under wine (I thought it would be impossible yet), I'm very curious about the PlayOnLinux thing. Can you explain why it is needed? I thought that just installing wine then run your application would do it. Please post more details as it seems that you need to create scripts, if-INW. Thanks.

try wine first... [http://appdb.winehq.org/objectManager.php?sClass=version&iId=7362&iTestingId=40686](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7362&iTestingId=40686) (seems to be some problems with creating new files, but that can be related to older wine)

be sure to use the latest wine!

---

### Post by dunkeld on 2011-06-24
Yes, with new wine it works even without PlayOnLinux. There are some minor issues with exporting graphs to pictures but the rest works perfectly and I just use the taking screen-shots applet. To get high quality picture I just increase the view of graph as much as I can and use the option allowing to define the area of the shot. Copy it to clipboard and paste in Gimp to save it next in any format I wish.

---

### Post by LadderGoat on 2012-08-04
I've stumbled upon SciDAVis while browsing the repositories and it seems to be a reasonable alternative. Lacks some features of Prism, but does most things I needed Prism for.

[http://scidavis.sourceforge.net/](http://scidavis.sourceforge.net/)

---

### Post by overdrank on 2012-08-04
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

