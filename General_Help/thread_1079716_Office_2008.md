---
title: "Office 2008?"
date: 2009-02-24
forum: General Help
---

### Post by coldmack on 2009-02-24
Pardon the newbish question as I am not sure where to ask. So my understanding is that osx is unix based and what not, and I have read you can get linux software to like work on osx and such. So what I want to know, is it possible to get Office 2008 for mac to somehow work on MIE? I know with like wine/darwine we can get office for windows to work but the thing is office for mac i feel is lighter and more efficient in my usage over the windows version and open office 2.x on my osx machine. Thanks.......

---

### Post by coldmack on 2009-02-24
Sorry anyone know?

---

### Post by mb_webguy on 2009-02-24
Mac OS X apps won't run on Linux.  While the underlying operating system is similar, Mac uses closed-source libraries (specifically Cocoa and Carbon) that aren't available for Linux.

I think there are a few projects working on this, but I haven't seen anything workable yet.

Oh, and btw -- it's generally frowned upon to bump your own threads more frequently than every 12 hours or so.  This is an international forum, so the person(s) who can answer your question may be asleep, at work, or otherwise not yet had the opportunity to read your post.

---

### Post by Nano_ext3 on 2009-02-24
What you want to do is install wine.  Here is a guide to install Office 2003 through wine:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992)

1. install wine by doing an apt-get install wine (tab to get an idea of all packages but just do "sudo apt-get install wine"
2. Insert windows disc.  CD to the directory that has the setup launcher.  
3. Do a "wine setup.exe"  And follow the prompts.

An easier way is to obtain Crossover Linux.  It is a commercialized version of wine, with better support.  However it is not free.  And I cannot condone piracy on this forum :)

PS. If using crossover I believe Office 2007 works better. 2003 may work fine.  Mac's Word 2008 is bloated slow and has a horrible web interface. Youd be kicking yourself in the foot by using it haha.

Regards,

Nano

---

### Post by bodhi.zazen on 2009-02-24
I suggest you try Open Office. It is open source and cross platform.

---

### Post by mb_webguy on 2009-02-24
Nano: The OP is asking about Office 2008 (the Mac OS X version of Office), not Office 2007.  Wine is great, but it won't help a bit with Office 2008.

And +1 to Bodhi's recommendation of OpenOffice.

---

### Post by coldmack on 2009-02-25
> **Nano_ext3 said:**
> 
An easier way is to obtain Crossover Linux.  It is a commercialized version of wine, with better support.  However it is not free.  And I cannot condone piracy on this forum :)

PS. If using crossover I believe Office 2007 works better. 2003 may work fine.  Mac's Word 2008 is bloated slow and has a horrible web interface. Youd be kicking yourself in the foot by using it haha.

Regards,

Nano

Well I have an unused Crossover key for my OSX machine(got it for free when they were offering it a while back), so do you think that it will work with the Linux version or if I can call them up to switch key for the Linux version? 

Well I thought Office 2008 for my intel mac was much better than all the versions of Openoffice I have used, not to mention it has more features than iWork. Well I do have a copy of 2007 on the Windows side, I can possible use on my comp(not sure if I can use the same key on two different computers). But thank you. 

As I stated twice Openoffice was not my cup of tea on my OSX machine, therefore would like to use something with a little more features(also I like how word has a grammar and spell checker that is fairly thorough). btw my post was like on page 7, but my mistake.

---

### Post by Nano_ext3 on 2009-02-25
I am just very serious in the fact that Office 2008 from MAC OSX is a horrible program in comparison to even office 2007 (apart from 2003).  Open office is great suggestion, it works and has a better interface than Office 2008 on OS X.

We have a Dual Socket G5 desktop in our Student Help desk at college where I work, IMO , all of us detest that, dont use iWorks either, its not that great.

Try Openoffice 3.  They have the .deb on the website under :

[http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=3.0.1](http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=3.0.1)

Thats the link.



Other than that, try my wine suggestion.  Im just still perplexed you want to use Office 2008 when its such a horrible interface + program.

THE MAIN, reason, WHY it wont work, is because of the closed source aspect.  You know how the mac's have their programs compiled to all use the action bar at the top?  That would most certainly crash the program if you even attempted to do it on any linux distro apart from using VMware and installing Mac OSX in that vm machine.  The Linux distro would have no CLUE how to interpret the closed source code.

Hope this helps,

Nano

---

### Post by mb_webguy on 2009-02-25
OpenOffice 3 is great, but I'd install it from the [openoffice-pkgs PPA]("https://launchpad.net/~openoffice-pkgs/+archive/ppa") instead of from the debs.  That way you can automatically get updates as they're released.

---

### Post by coldmack on 2009-02-25
I guess I will try to see if I can get Crossover to let me swtich to their linux version or something. But thanks.

---

### Post by Nano_ext3 on 2009-02-25
> **mb_webguy said:**
> OpenOffice 3 is great, but I'd install it from the [openoffice-pkgs PPA]("https://launchpad.net/~openoffice-pkgs/+archive/ppa") instead of from the debs.  That way you can automatically get updates as they're released.

What is the advantage of that, and can you explain what files exactly you would be grabbing?  Thx m8 :)

On a side note:  NOTICE:  the default bulliting list behavior in 3.0 has changed, at least for now.  When you choose "bullets" in the bullets and numbering, enter some text hit enter, then tab, and ...UM.. it deletes the "indented bullet" and tabs over.  In 2.4 (current distros), you enable bulleting and enter text, hit enter, hit tab and the bullet is retained.

What they WANT you to do apparently in OOo 3.0, is use "outline" view, but there is no PLAIN bullet style in here, only some odd style sets that are not my cup of tea.

For this quirky reasoning (i used OOo ALOT to do reports and notes, so that bulleting feature is very important to me), I dont use 3.0, I dont see that much improvement in it , other than a slight speed increase and the "Starter app" that shows you all the programs.

Your better off doing a "sudo apt-get install openoffice" or use add/remove to find it.

---

### Post by mb_webguy on 2009-02-25
> **Nano_ext3 said:**
> What is the advantage of that, and can you explain what files exactly you would be grabbing?  Thx m8 :)

Well, just as I said, you'd automatically get updates as they're released, rather than having to go out and grab the deb packages again and again.  A PPA acts just like the repositories, so any security updates and new releases are detected and can be installed with Update Manager.

---

### Post by jgoguen on 2009-03-06
> **coldmack said:**
> Well I do have a copy of 2007 on the Windows side, I can possible use on my comp(not sure if I can use the same key on two different computers).
Some MS Office licences allow you to have more than one installation (MS Office 2007 Home & Student allows three IIRC) but most only allow one.  If you're not certain, check the documentation that came with MS Office.  As much as I hate to do this to you, your answer probably lies in the EULA...

> **coldmack said:**
> (also I like how word has a grammar and spell checker that is fairly thorough)
The OpenOffice.org spell checker is getting better all the time, but sometimes it depends on the language.  For some, yes MS Office has the better spell check.  If you're like me though and you want your spell check to work in Canadian English, MS Office is horribly lacking :)  Their grammar check is even worse, it marks perfectly valid grammar as wrong and marks grammar that would make English teachers cry as good.  As an example, this passed the MS Office 2003 grammar check [s](haven't checked if it's still true for MS Office 2007)[/s](still true for MS Office 2007):
> Microsoft the company need make good grammar checkWhile it's not the worst English grammar I've seen, it's not something a native English speaker would normally say :)  That said, grammar checking is supposedly very difficult to implement correctly, so the fact that Microsoft even has one is deserving of at least some kudos.

> **mb_webguy said:**
> OpenOffice 3 is great, but I'd install it from the [openoffice-pkgs PPA]("https://launchpad.net/%7Eopenoffice-pkgs/+archive/ppa") instead of from the debs.  That way you can automatically get updates as they're released.
I installed OpenOffice.org 3 from their debs, and I get automatic updates.  When updates are available, OpenOffice.org notifies me, I download them, and I apply them.  It's not as automated as using the PPA, but it's better than nothing.  Thanks for the PPA link though, I missed this in my travels and will probably use this option instead...because it's more automated and doesn't require me to start OpenOffice.org to check for updates :)

---

