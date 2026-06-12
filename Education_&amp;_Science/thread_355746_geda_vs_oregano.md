---
title: "geda vs oregano"
date: 2007-02-07
forum: Education &amp; Science
---

### Post by LaserJock on 2007-02-07
Hi all!

  I need some help. I'd like to get an electronics app (circuit diagrams/simulations) into Edubuntu but I don't have much experience with them. geda and oregano look like decent apps but I only want to include one if they have similar features.

  So, what are your experiences? Do you think geda or oregano are good apps for Edubuntu? Is there another electroncic circuit app that's better?

-LaserJock

---

### Post by Adrian Nania on 2007-03-01
Try LTSwitcherCAD from Linear Technology. It is by far the best free tool, a powerful electronic spice simulator. I was extremely pleased to discover the full professional power this program has. As an example, a very complex project with 40Gb graphic file result was simulated faster by LTSpice than OrCAD, with the same precision! Looks like I am biased, but I assure you I am absolutely honest and I do have experience with OrCAD, Altium, and Mentor.
Many other companies (like ST, TI, NI, etc.) are pretending to offer "free" tools for circuit analyze/simulation. Check what those crocks are offering, crippled versions with "online" or limited functionality, only to ask you to pay for the working version.
If you need to complement your design tools with PCB, micro controllers, etc. options, check kicad, ktechlab, oregano, geda

Please have a look at ktechlab. Out of the blue somebody decided to scrap this project? It is really bad, this program is the most impressive I know for electronic simulation and micro controllers development, with very strong software tools (flow chart programming!). One can not get similar features from very expensive programs.

Best Regards,
Adrian Nania

---

### Post by outer_space on 2007-04-24
Is there LT SwitcherCAD that works with ubuntu?

---

### Post by penvzila on 2007-04-24
Run it in wine. It works 95% perfectly.  In fact, I think it's developer uses it in wine.

---

### Post by triplepoint on 2007-05-05
Depending on your philosophical goals, including a windows-based app with edubuntu might not be a very attractive option.  There're a few other options out there that are open source, but so far I haven't found the ideal package.

Last year I started down the road of finding an open-source schematic / circuit board layout package for use in a startup electronics company.  I wasn't as focused on simulation, though it would've been nice.  To calibrate my tolerance for clunkiness, I'm a capable linux enthusiast with a moderate level of experience over the past 6 or 7 years.  My day job is programming.  I don't mind a little 'personality' to software as long as it isn't painful.

The major contenders here as I see it are geda and kicad.  It's entirely possible I missed a worthy project, please oh please let that be the case.  And please oh please, if that is the case, let me know.

Geda is a loose association of programs that work together.  A few of them involve command line calls to get the job done.  Though you'll hear people violently disagree, I feel that geda is very much a work in progress that isn't really fit for prime time.  Any software project where a suggested process from the support forums is 'write a little perl script to convert the output of program A to the proper format to be loaded by program B" just isn't ready in my book.  Geda has buckets of modularity which appeals to the "if you don't like it, write a replacement" mentality, but as a software package, they're suffering from a lack of cohesiveness and integration which is keeping it very much in the realm of the tinkerer's plaything.  Supporters will call that a feature. You're mileage may vary.

Kicad is a bit further down the road of package integration, but it's still not the ideal.  I have to admit I didn't spend nearly as much time with kicad as I did trying to make geda work, so its possible I just didn't get used to it, but kicad's UI was full of features that left me guessing.  For instance, front and center on the button bar at the top are two buttons with indefinite icons titled 'run cvpcb' and 'run pcbnew'.  Anytime a UI has a command along the lines of 'run <some program name>', it's a sure thing that you'll spend several hours reading the faqs from several different development groups before you can start getting anything done.  While not as strung out as geda, I still got the feeling of ducttape and baling wire just under the hood.

So basically, and this is purely my opinion, neither of these options seemed reliable enough to have any real place in the business world.  Will they work for backyard-shed tinkering?  Yes, both can serve in that role, with some reading and some experimentation.

If full hardware production isn't your goal, I should mention that Oregano looks really promising.  Its a nice clean and simple UI with gnucap simulation under the hood.  I played with it briefly and it seemed simple and intuitive for basic circuit demonstration roles, but the lack of PCB layout provisions means you'd have to pair it up with some other package to obtain a full development suite.  Oregano would be ideal for a demonstration or exploration purpose though.

---

