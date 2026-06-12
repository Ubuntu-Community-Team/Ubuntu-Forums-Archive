---
title: "Request for advise: Using Linux in a business environment"
date: 2009-04-29
forum: General Help
---

### Post by okdewit on 2009-04-29
Hey all,

Pretty new to these forums, so I hope this is in the right place... :)

Im a network administrator for a company that sets up networks for medium/large businesses. My job is to assemble and install high-end servers, and configure them. I am MS certified, so my mindset is pretty much infected with their ideas and conventions.

At home, I love to use linux. I am a free software enthousiast (as in freedom, not money-related). Free software is interesting for me, because it follows an evolutionary path. Most truly free software feels just so much better to work with, like everything your creative mind thinks of is eventually implementable. 

At work, I often run into walls, some things are just impossible to implement (for example, I configured an ISA server, but couldn't create the rules i needed, and although squid's config file needed much study, I could reach the solution with it way easier).

I never went beyond far beyond a few ubuntu (XFCE / Gnome) desktops, an SMB fileserver, some media apps, using openoffice, and wine for the occasional windows app, so my knowledge is limited, but always willing to learn.

My dream: Create a truly free linux business environment. My boss doesnt really believe in it, but I have a lot of testservers here and would like to create a complete test setup to demonstrate the power of linux, replacing:

- A Windows SBS2008 server with Active directory, centralised users/securitygroups, email, task planning/calendars, secure shared storage.

- A Terminal server / Citrix server for a large group of (external) users, being able to configure user access to apps and data.

- A backup solution (either to Ultrium tapes or external HD's, or even online) configurable with strategies.

I would love to test this, and while I can find a few apps replacing outlook/exchange/fileshares using google, I have no idea what a good professional solutions are (Is SMB the best way to create shares? How to set up users/securitygroups or group policies? etc.)

Im not getting my hopes up for ever implementing such a thing, because most customers wont accept ubuntu as an office desktop, but it would be a nice experiment for me to check out.

I hope this community can point my in the direction of good tutorials, books, (open) software and configuration examples :)
The idea is to impress a bunch of MS-professionals in dusty suits, so please pass me some ideas that could convince them that linux is not only suitable for nerdy hobbyists with insomnia. They want systems that can be deployed quickly, configured quickly, repaired quickly...

Thanks in advance,

okdewit.

---

### Post by 3Miro on 2009-04-29
If you ask me, business environment is exactly the spot where Ubuntu would excel right now. What do business people need, documents (Open Office can handle that with less compatibility issues than MS Office), e-mail, file servers, database servers. All of that has been Linux's strength for many years.

In 2001-2002, in my College, we had a Linux system. We had computers that worked as terminals connecting to a central server, we had file servers, e-mail server and web server, all belonging to a somewhat small department. Backups were done regularly.

Planning I guess can fall in the category of Chron. Everything in Unix is users/permissions based, so user administration shouldn't be a problem. I don't expect any problems there.

My knowledge is not top of the line to give practical advice, but I have seen all of what you describe being implemented in Colleges and Universities.

The biggest problem would be people complaining due to lack of understanding (Why did the icon on my button change? it is broken! Fix it!) Another problem is that everything in the setup is very different from MS. I believe the Linux way would make more sense, but that is for someone with free mind.

Businesses might like the cost, shoot for that.

---

### Post by sharkbite1414 on 2009-04-29
> **3Miro said:**
> Businesses might like the cost, shoot for that.

Many businesses may have all ready thought about using linux. However their IT department would probably convince them that retraining would be time consuming and more costly than the money saved using linux.

I don't say this to discourage you, only so you don't over look this problem.;)

---

### Post by Corvias on 2009-04-29
You have two fronts on which you need to work: Technical and Political. First, though, you need to realistic with the enormity of your goal. You will need to incrementally move things over to Ubuntu/FOSS very slowly, starting in the backroom first, then gradually moving to the client-side (that's the hardest part). Above all, don't let idealism cloud your judgement -- there's just some things that can only be done through proprietary means depending on your local resources (intellectual, political, and monetary). Forcing your ideas down your company's proverbial throat  will only get you in trouble, and make FOSS look bad.

On a technical level, read all you can about Samba. The fact that you are already (hopefully) familiar with SMB and NetBios will help you a lot in the beginning. "Samba by example" is a great book to get started.

Politically, you need to approach you boss with facts. Find out what your company is paying in software licenses. Once you have a proof-of-concept solution going, present the numbers your company can save through FOSS (if any), and present the real examples you've built. You might want to find some niche areas in your operation that you can slip FOSS into with little political friction. Be honest and open about caveats to your plan. Not doing so will just make FOSS look bad when an unexpected problem comes up. Many times the money saved in licenses must be transferred to training, but it is important to remember that training is ususally a one-time expense, while licenses must usually be renewed yearly. Finally, remember that management types like some sort of assurance of support. There is a major misconception that FOSS has no formal customer support. Explain that not only is there a community to rely on, but you can also buy support contracts from, for example, Canonical who sells contract for Ubuntu. (No, I am not a Canonical employee)

I wish you the best of luck. let me know if you need any clarification.

---

### Post by okdewit on 2009-04-30
Thanks a lot for the advise.

Im not trying to convert the whole company, believe me, I know that would get me fired :P Operating system preference can be like radical religious views, the only thing I'm hoping to accomplish is to show people that every OS has its power.

Is Samba the best way to set op fileshares? I always thought samba was kind of created as a compatibility thing for MS domains, isnt there a "native" unix/linux way to do this? Or is samba better anyway?

As for terminal servers / citrix replacement, could you give me a hint?
And group policies?

I convinced a few people at the company already that squid is more versatile than ISA, and since a proxy/gateway/NAT isnt something users "experience" directly it doesnt matter what OS it runs on, from their point of view.

We got a lot of requests for netbooks, so maybe there's a possibilty for change there too :)
Also, we use a central server at the company which uses a reverse VNC connection (every client calls in every 30 sec to check if a connection is needed) for management of the client servers. Does similar software exist for linux?

Sorry for asking so much questions, thanks for the answers I got so far :D

---

