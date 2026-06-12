---
title: "Stable but lacks a couple important features."
date: 2006-02-13
forum: Desktop Environments
---

### Post by exofire on 2006-02-13
I tried Ubuntu for the first time. I found it to be a stable distribution but there were a couple necessary features that I found missing:

File search : Other than using a terminal, there is no simple way to search for files, I am curious as to how this was over looked by developers. Any distribution that lacks this feature is simply unusable in my opinion.

Compiling : I also noticed compiling software is a pain as it requires unnecessary steps to be able to compile. I was going to link /usr/src/"*linux-<kernel-version>*" /lib/modules/"*version*"/build --- so I could compile some modules, but found that none of necessary config files were present.

To me, these functions should be present and made available in any distribution as compiling and file searching are a necessary Linux tool.

Once these two issues are fixed, I think Ubuntu will be a worthy distribution to use.

To be fair, Ubuntu is one of the few distributions that has picked up both my Sound (Audigy 2) and Video (Radeon 9800 PRO) cards. :KS

---

### Post by aysiu on 2006-02-13
[QUOTE=exofire]I tried Ubuntu for the first time. I found it to be a stable distribution but there were a couple necessary features that I found missing:

File search : Other than using a terminal, there is no simple way to search for files, I am curious as to how this was over looked by developers. Any distribution that lacks this feature is simply unusable in my opinion.[/quote] Huh? Go to Places > Search for Files. You can also Alt-F2 ```
gnome-search-tool
```

> 
Compiling : I also noticed compiling software is a pain as it requires unnecessary steps to be able to compile. I was going to link /usr/src/"*linux-<kernel-version>*" /lib/modules/"*version*"/build --- so I could compile some modules, but found that none of necessary config files were present. So don't compile. Or just install *build-essential* through apt-get.

> 
Once these two issues are fixed, I think Ubuntu will be a worthy distribution to use. Why are you posting this in desktop support?

---

### Post by exofire on 2006-02-13
Then I must have a damaged ISO, because there is no "file search" and as for hitting "F2," nothing happens. Since this is a desktop feature, I suspect that posting here is appropriate.

As for the "don't compile" - that would be great except many Linux programs require them to be compiled into the kernel and since I have no desire to limit myself to what Linux software I can use, this is not an option - not mention the packaging program for Ubuntu is limited. If limiting myself was my goal, I would simply go back to a propeitary OS like Windows, which I havn't used in years (since 1997).

---

### Post by nalmeth on 2006-02-13
He meant alt-f2, to bring up the run command dialogue. If you're using gnome, click on the places button on the toolbar, and you will see search for files, or something like that. It wasn't overlooked. I never even use it though, so it wouldn't be too important for me.

Whenever you're comiling a program, it is always part of the process to make sure you have the correct libraries and dependencies installed, and in my experience a list of this is available for whatever you're compiling. 

Also there is becoming less and less need to compile because apt is so powerful and easy, and ubuntu is geared for user-friendlyness, and compiling isn't friendly to noobies. That's why most of the tools you need won't be there. You can easily get them with apt though.

Yeah, I see no problem posting this here..

BTW what are you used to using? Gentoo or something? Naturally it is easier to compile with gentoo, because thats how everything is installed, and why it uses emerge.

Ubuntu is all about apt

---

### Post by cwaldbieser on 2006-02-13
[QUOTE=exofire]Then I must have a damaged ISO, because there is no "file search" and as for hitting "F2," nothing happens. Since this is a desktop feature, I suspect that posting here is appropriate.

As for the "don't compile" - that would be great except many Linux programs require them to be compiled into the kernel and since I have no desire to limit myself to what Linux software I can use, this is not an option - not mention the packaging program for Ubuntu is limited. If limiting myself was my goal, I would simply go back to a propeitary OS like Windows, which I havn't used in years (since 1997).[/QUOTE]
Pressing **Alt-F2** causes the Run Dialog (similar to Windows Start -> Run) to appear.  You can type "gnome-search-tool" in there .  Or From the menu, it is Places ->Search for Files as aysiu mentioned.

The compiler is not installed by default, as many casual desktop users never have a need to use it.  For folks who do want to use it, you can install the entire tool chain by installing the "build-essentials" package, either using apt-get, or one of the GUI front-ends (e.g. Synaptic Package Manager).

If you use kubuntu, the find utility is called "kfind".  It is accessible from the K-menu ("Find Files / Folders").

So as you can see, the GUI sort utilities are already there, and the lack of a compiler is easily remedied.

---

### Post by exofire on 2006-02-13
[QUOTE=nalmeth]He meant alt-f2, to bring up the run command dialogue. If you're using gnome, click on the places button on the toolbar, and you will see search for files, or something like that. It wasn't overlooked. I never even use it though, so it wouldn't be too important for me.

Whenever you're comiling a program, it is always part of the process to make sure you have the correct libraries and dependencies installed, and in my experience a list of this is available for whatever you're compiling. 

Also there is becoming less and less need to compile because apt is so powerful and easy, and ubuntu is geared for user-friendlyness, and compiling isn't friendly to noobies. That's why most of the tools you need won't be there. You can easily get them with apt though.

Yeah, I see no problem posting this here..

BTW what are you used to using? Gentoo or something? Naturally it is easier to compile with gentoo, because thats how everything is installed, and why it uses emerge.

Ubuntu is all about apt[/QUOTE]

Thanx for the response ;)

Currently I am using Slackware and have for years, but I must admit I have an addiction when it comes to trying different Linux distributions, which is why I have a separate drive setup for that very reason.

I read a lot of good reviews for Ubuntu, so I decided to check it out. :)

---

### Post by exofire on 2006-02-13
[QUOTE=cwaldbieser]
The compiler is not installed by default, as many casual desktop users never have a need to use it.  For folks who do want to use it, you can install the entire tool chain by installing the "build-essentials" package, either using apt-get, or one of the GUI front-ends (e.g. Synaptic Package Manager).[/QUOTE]

Thank you for the explanation. :-D

My pickyness is a result of using Linux for so many years and having to rely on compiling to get every new up-to-date piece of hardware I purchase to work :cry: 

But like you said, it's easily fixed and yes, I do understand now why they did not include :)

---

### Post by aysiu on 2006-02-13
So you really didn't see this in your installation of Ubuntu?

---

### Post by exofire on 2006-02-13
[QUOTE=aysiu]So you really didn't see this in your installation of Ubuntu?[/QUOTE]

Obviously that is one of the first things I looked for and certainly if it was there, I would see it. Just about every Linux distro has placed a "search" button on the task panel.

But thanx anyway for the help.

I'll simply re-install Ubuntu it to see if it fixes the problem - it may simply be a glitch and considering I have nothing important for files to lose and installation is fast - it's shouldn't be a problem.

---

### Post by nalmeth on 2006-02-13
> Obviously that is one of the first things I looked for and certainly if it was there, I would see it.

I don't think asiyu is suggesting you are blind, but I too find my mind boggling at the thought that the install would leave this out, and not notify you that a portion or more of the installation had problems! 

Anyway good luck to ya, and hopefully you can dig ubuntu!

---

