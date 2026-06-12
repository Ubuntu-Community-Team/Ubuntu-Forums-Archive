---
title: "Improving Ubuntu: A Beginners Guide to Filing Bug Reports"
date: 2008-12-14
forum: General Help
---

### Post by Rocket2DMn on 2008-12-14
**OK stop!**  It looks like there is a lot of text here, but I promise you that [COLOR="Blue"]submitting bug reports is **not complicated**[/COLOR].  This post will attempt to walk you through filing [COLOR="Red"]_good bug reports_[/COLOR] in Ubuntu's bug tracker, called [Launchpad]("https://launchpad.net/") - specifically at [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/). Understanding the process will help you get your "bug" solved as quickly as possible.

Due to the large volume of bugs that get reported, it is important that you file bugs correctly and with as much information as possible.  As a bug triager, I assure you that this will *significantly* improve the chances of getting your bug looked at and fixed in a timely manner!

[COLOR="DarkSlateBlue"]_**[SIZE="4"]A Brief Background on Bugs:[/SIZE]**_[/COLOR]

_[SIZE="3"]What a bug is:[/SIZE]_

A "[bug](http://en.wikipedia.org/wiki/Software_bug)" exists in software when a program does something unexpected, usually causing problems for the user.  *Some* examples include:
[LIST]
[*]a program crashing or closing unexpectedly
[*]a (simple) missing feature
[*]unexpected error messages, often preventing a program from continuing normal operation
[*]other unexpected behavior
[/LIST]

_[SIZE="3"]What a bug is not:[/SIZE]_
[LIST]
[*]a support request (use the forums!)
[*]a missing feature that requires more than minimal work to implement
[*]a bad configuration on your machine (ask here on the forums for help tracking it down)
[/LIST]

_[SIZE="3"]How do I know?[/SIZE]_

Those who are very new to Ubuntu and/or Linux in general should make posts here on the forums before filing bug reports.  Many people run into problems that aren't really bugs, and many common problems that are bugs have already been filed (but please check for yourself!).
The forum community members can often help you work around bugs - *please ask* if they think you should file a bug report.

[CENTER][COLOR="Red"]_**[SIZE="5"]-> Before filing a bug report <-[/SIZE]**_[/COLOR][/CENTER]
[LIST]
[*]Make sure you have an account on [Launchpad]("https://launchpad.net/") - you can't file a report without one.  If you don't have one yet, go to "Log in / Register" at the top right of a Launchpad page, then follow the directions.
[*]Search [Launchpad's Bugs in Ubuntu]("https://bugs.launchpad.net/ubuntu/") for duplicate reports - is there already a bug open for your problem?  If so, respond to that bug report, and confirm it if possible (change the **Status** from *New* to *Confirmed*).  If you find such a report, please be sure that it is for the *exact* same problem that you have.  If it is a bug related to a specific piece of hardware, then you should also have that hardware (or one extremely similar).  If it's not the same, file a new report and mention that other bug as a similar problem - a triager can help you determine if the problem is actually the same.
[/LIST]

[CENTER][COLOR="Green"]_**[SIZE="5"]-> Steps for filing a bug report <-[/SIZE]**_[/COLOR][/CENTER]

[color=navy]**[size=2]Filing bug reports can be automated via the use of [uwiki]Apport[/uwiki].**[/color][/size]

Apport is a tool that ships with Ubuntu and can assist both end users and developers. It automatically attaches important data to the report, like version information and relevant logs.  In some cases, it will automatically appear to help you file reports (like after program or system crashes).

[LIST=1]
[*]In many programs in Ubuntu you can go to **Help -> Report a Problem** or **Help -> Report a Bug** and Apport will collect information automatically for you and take you to the bug filing page on Launchpad where you can elaborate on your problem.
[LIST]
[*]Alternatively, from the terminal you can run the following to have Apport collect information automatically for you:
```
ubuntu-bug *packagename*
```
It is important that you try to file the report under the [right package]("https://wiki.ubuntu.com/Bugs/FindRightPackage").  This can often be confusing, so try your best. If you really don't know, leave the package name off and you will be prompted about some common problem areas.
[/LIST]
[*]Apport will now collect some information and prompt you to to send the report. You may view what is being uploaded by expanding *Content of the report*. Now click "Send Report". A browser window will open and navigate to Launchpad.  If needed, login, then proceed.
[*]After Launchpad is finished processing, describe the bug in one short statement (this is the bug's title - be descriptive!). Click "Next".
[*]A list of bugs that Launchpad thinks might be similar are listed - check them.  If you don't find a match, click "No, I need to report a new bug".
[*]Now you can describe your bug in more detail. Include steps to reproduce the bug, and methods you've tried to solve the bug or work around it.
[*]If you need to attach any files (like screenshots) to the bug report, expand *Extra options* and go to the *Include an attachment* section at the bottom and browse for the file. You can only upload one file at a time, so if you have multiple files to upload, you will need to add them in Comments after submitting the bug report.
[*]When you believe there is enough information provided, click "Submit Bug Report".
[/LIST]

[CENTER][COLOR="Orange"]_**[SIZE="5"]-> After filing a bug report <-[/SIZE]**_[/COLOR][/CENTER]
[LIST]
[*]You can add extra comments at the bottom of the bug report. You can also add more attachments by clicking "Add attachment or patch".
[*]You should receive emails about changes and responses to the bug report - [COLOR="Red"]**follow up!**[/COLOR]  A bug can't be completed until you provide all information that has been requested.  Bookmark the bug report and check back regularly for updates.
[*]You may be asked to file a bug report *upstream* - this means doing something similar to what we did above, but at a website outside of Launchpad.  This can get a little complicated, so feel free to ask how to proceed - more information is available [here]("https://wiki.ubuntu.com/Bugs/Upstream").
[*]You may also be asked to check if the bug exists in the development version of Ubuntu by using a LiveCD.
[/LIST]

[COLOR="Indigo"]_**[SIZE="4"]Generic lifecycle of a bug report:[/SIZE]**_[/COLOR]
[LIST]
[*]User experiences a problem and files a bug report
[*]If lucky, somebody else will confirm the bug report (**do not** confirm your own bugs!)
[*]A triager looks at the bug report.  If more information is needed, the triager will request it.  The bug reporter will provide the requested information.  Repeat as necessary.
[*]When the triager is satisfied that there is enough data, the bug will be marked as *Confirmed* (or even better, as *Triaged*).  The triager should set an **Importance** on the bug in most cases, and possibly assign it to a developer or team.
[*]A developer looks at the bug report - they will either ask for more info, fix the bug or reject it (either because it's not worth fixing, or it's not actually a bug).
[*]The bug report is closed with a **Status** of *Fix Released*, *Won't Fix*, or *Invalid*.
[/LIST]
When fixes are released for bugs, the fixed version of the program is usually not made available in stable versions of Ubuntu unless it is a security fix or meets the criteria for a [Stable Release Update]("https://wiki.ubuntu.com/StableReleaseUpdates").  The fixed version of the program is usually placed into Ubuntu's development release (unstable).

[COLOR="DimGray"]_**[SIZE="4"]Some relevant and useful links:[/SIZE]**_[/COLOR]

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
[http://www.chiark.greenend.org.uk/~sgtatham/bugs.html](http://www.chiark.greenend.org.uk/~sgtatham/bugs.html)
[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)
[https://wiki.ubuntu.com/Bugs/Responses](https://wiki.ubuntu.com/Bugs/Responses)
[http://ubuntuforums.org/showthread.php?t=734460](http://ubuntuforums.org/showthread.php?t=734460) - This thread's predecessor (short and sweet)
**[Guia para reportar bugs]("http://ubuntuforums.org/showthread.php?t=1017604")** - This guide translated in Spanish, thanks to [sajnox]("http://ubuntuforums.org/member.php?u=362457").

-----------------------

If you have further questions or feedback about filing bug reports, please feel free to ask in this thread.

[RIGHT]Cheers,
[COLOR="DarkRed"]***[SIZE="3"]Rocket2DMn[/SIZE]***[/COLOR][/RIGHT]

[IMG]https://launchpadlibrarian.net/1812570/bugsquad.png[/IMG]

---

### Post by lukjad on 2008-12-14
Thank you Rocket2DMn! This will really be useful.

---

### Post by nhandler on 2008-12-14
Thanks Rocket2DMn! This is a really complete explanation about reporting bugs on Launchpad. I know you mentioned this in your post, but I would like to stress the importance of following up with your bug reports. If your bug disappears after an upgrade for the package or with a new Ubuntu release, please add a comment to the bug, and close it as 'Invalid'. This will prevent bug triagers and developers from wasting time on that bug report. Also, if someone asks a question in the bug report or requests more information, please try and respond as soon as possible. While the bug report requires additional information, it will have a status of 'Incomplete'. During this time, most developers will not look at the bug. As a result, if you want the bug fixed, it is imperative that you provide all requested material. If you do not provide the requested information for 4 weeks, it will be closed with a status of 'Invalid', and a comment like the following will be added:

> We are closing this bug report because it lacks the information we need to investigate the problem, as described in the previous comments. Please reopen it if you can give us the missing information, and don't hesitate to submit bug reports in the future. To reopen the bug report you can click on the current status, under the Status column, and change the Status back to "New". Thanks again!

Once a bug is closed (either as 'Fix Released', 'Invalid', or 'Won't Fix'), it no longer shows up in most of the listings on Launchpad. This means that if it was not closed with a status of 'Fix Released', it probably will not get fixed.

Hopefully, you can now see why it is very important to follow up with your bug reports on Launchpad.

---

### Post by bhadotia on 2008-12-15
> **Rocket2DMn said:**
>   As a bug triager
Thabks for the great info!
Just a question:
What does a "triager" mean? Found in my dictionary a noun "triage" meaning "sorting out and classyfing"- a medical  term. Couldn't find it on the web either.

---

### Post by Rocket2DMn on 2008-12-15
What you found in the dictionary is the same idea as what a bug triager does.  In an emergency situation (ER, battlefield, mass casualty natural disaster, etc), a medical triager is one who works ahead of the medics/nurses/doctors to essentially evaluate the situation and mark the wounded in order of how serious their injuries are (a high priority patient gets seen before a low priority one, and those with injuries too serious to deal with may not get treated at all - the "save as many as you can" mentality).  Patients may be grouped together based on the seriousness of their individual situations.

A bug triager looks at bug reports, collects information about the bug, then evaluates how important they are.  Developers then use that information to approach solving the problems that they are presented with.  A bug triaged with critical or high priority is given more attention than one with medium or low priority.  Bug reports that aren't actually bugs are rejected by the triager before developers even get to them (thus saving them time).  Esssentially, it would take too much time for developers to go through every bug report, so a triager does it for them so that the developer can spend time fixing bugs instead.

A triager doesn't have to know all the inner workings in order to make a judgment about the situation.  So, in medical terms a triager doesn't have to be a doctor (but can rather simply look at a person and with some very basic knowledge, decide how seriously hurt they are).  A bug triager doesn't have to know anything about coding, just whether how something reacts is really a bug or just a misconfiguration.

---

### Post by Izek on 2008-12-15
> **Rocket2DMn said:**
> A bug triager looks at bug reports, collects information about the bug, then evaluates how important they are.  Developers then use that information to approach solving the problems that they are presented with.  A bug triaged with critical or high priority is given more attention than one with medium or low priority.  Bug reports that aren't actually bugs are rejected by the triager before developers even get to them (thus saving them time).  Esssentially, it would take too much time for developers to go through every bug report, so a triager does it for them so that the developer can spend time fixing bugs instead.

Thanks for explaining. Since my two bugs got triaged for the random freezing with high CPU.

---

### Post by NewJack on 2008-12-15
Thanks for this useful information!!!

---

### Post by bhadotia on 2008-12-16
> **Rocket2DMn said:**
> What you found in the dictionary is the same idea as what a bug triager does.  In an emergency situation (ER, battlefield, mass casualty natural disaster, etc), a medical triager is one who works ahead of the medics/nurses/doctors to essentially evaluate the situation and mark the wounded in order of how serious their injuries are (a high priority patient gets seen before a low priority one, and those with injuries too serious to deal with may not get treated at all - the "save as many as you can" mentality).  Patients may be grouped together based on the seriousness of their individual situations.

A bug triager looks at bug reports, collects information about the bug, then evaluates how important they are.  Developers then use that information to approach solving the problems that they are presented with.  A bug triaged with critical or high priority is given more attention than one with medium or low priority.  Bug reports that aren't actually bugs are rejected by the triager before developers even get to them (thus saving them time).  Esssentially, it would take too much time for developers to go through every bug report, so a triager does it for them so that the developer can spend time fixing bugs instead.

A triager doesn't have to know all the inner workings in order to make a judgment about the situation.  So, in medical terms a triager doesn't have to be a doctor (but can rather simply look at a person and with some very basic knowledge, decide how seriously hurt they are).  A bug triager doesn't have to know anything about coding, just whether how something reacts is really a bug or just a misconfiguration.

> **Izek said:**
> Thanks for explaining. Since my two bugs got triaged for the random freezing with high CPU.

+thanks again:KS

---

### Post by hongri1998 on 2008-12-17
**[ball valve](http://www.valvesupplier.net/petro-valve.htm)** featuring with uni-body, top entry trunnion mounted ball. This type of valves gives convenient of in-line repair or replace valve internal components without dismantling it from pipeline. series [ball valve]("http://www.valvesupplier.net/petro-valve.htm") is all fire safe designed comply with API 607 & API 6FA.

---

### Post by roshanjose on 2008-12-17
Thanks for the info...

I have already worked on this a few days before and filed 2 bugs...

But what seems the problem is that I want to solve the bugs and I never know how to find a solution. I dont know the entire coding.. i have learnt the basic C, C++ and Java, had OS and Computer Networks as subjects in college,but how can I get into the depth of clearing bugs

and also write system programs that can be benefited by the community.
I have given a query of this in my thread 

[http://ubuntuforums.org/showthread.php?t=1011479](http://ubuntuforums.org/showthread.php?t=1011479)


Check this and tell me what you think can help me contribute

---

### Post by Rocket2DMn on 2008-12-17
> **roshanjose said:**
> Thanks for the info...

I have already worked on this a few days before and filed 2 bugs...

But what seems the problem is that I want to solve the bugs and I never know how to find a solution. I dont know the entire coding.. i have learnt the basic C, C++ and Java, had OS and Computer Networks as subjects in college,but how can I get into the depth of clearing bugs

and also write system programs that can be benefited by the community.
I have given a query of this in my thread 

[http://ubuntuforums.org/showthread.php?t=1011479](http://ubuntuforums.org/showthread.php?t=1011479)


Check this and tell me what you think can help me contribute

Well, this thread isn't about *fixing* bugs, just *reporting/filing* them.  However... Most software bugs require at least a moderate/good understanding of programming, and some familiarity with the code base with which you are working.  Sometimes experienced programmers and other users have the skills (using debuggers and tracing programs) to trace the source of a problem in unfamiliar code and suggest fixes, but we usually just leave it up to the developers of the respective project for which bugs are filed against.  

If you do want to fix bugs for a certain project, you should get in contact with the code maintainers (usually by looking at the project's homepage) and ask them directly how you can contribute.  Every project is different.

And for your last question, we encourage users to expand their skills and have a little fun by developing their own programs.  While most never make it mainstream, there are tons of open source projects out there that find niches, and you are welcome to start your own!  Launchpad provides their own revision control system called Bazaar where you can store your code branches.  

For more details on these questions, you might consider asking in the [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39") forum area.  Good luck and have fun!

---

### Post by OrangeCrate on 2008-12-17
Excellent!

:)

---

### Post by anim on 2008-12-18
As a longtime BugControl triager and especially a triager that focuses on New/No Package bugs I thank you for writing this. Makes my life a lot easier!

---

### Post by sajnox on 2008-12-19
Hi Rocket2DMn,

I find this post *very useful*, if you agree I would like to translate it to spanish and post it, at least in the Argentinean Forum, and I would like to promote it among the other spanish speaking forums.

I'm confident that you will agree on this but I just wanted to check before, obviusly the translation will have a link to this thread.

---

### Post by Rocket2DMn on 2008-12-19
> **sajnox said:**
> Hi Rocket2DMn,

I find this post *very useful*, if you agree I would like to translate it to spanish and post it, at least in the Argentinean Forum, and I would like to promote it among the other spanish speaking forums.

I'm confident that you will agree on this but I just wanted to check before, obviusly the translation will have a link to this thread.

¡por supuesto!  You should probably also include a note that bug reports should be filed in English if at all possible - I don't think bugs in other languages are supported very well or get much attention without a bit of luck involved.  This could even include translating critical output from the system, like terminal text or error messages relevant to the problem being reported.

When you are finished with your translation, post back here and I will include a link in the guide.  Thank you for asking in advance :)
Cheers!

---

### Post by sajnox on 2008-12-19
Perfect!!

My idea is to help people to understand what is a bug and how to report it, if they don't know english with the LoCo we can help with the translation

---

### Post by sdennie on 2008-12-20
> **Rocket2DMn said:**
> ¡por supuesto!  You should probably also include a note that bug reports should be filed in English if at all possible - I don't think bugs in other languages are supported very well or get much attention without a bit of luck involved.  This could even include translating critical output from the system, like terminal text or error messages relevant to the problem being reported.


A tip for getting error messages in English from the terminal is to set the language to blank before a command.  For example:

```

$ ls /foo
ls: no se puede acceder a /foo: No existe el fichero ó directorio
$ LANG= ls /foo
ls: cannot access /foo: No such file or directory

```

That might be useful to include in your translation, sajnox.

---

### Post by cprofitt on 2008-12-20
Posted this as a [resource]("https://wiki.ubuntu.com/BeginnersTeam/FocusGroups/Education/Resources") for the Beginners Team Education Focus Group. Great post.

---

### Post by sajnox on 2008-12-21
> **vor said:**
> A tip for getting error messages in English from the terminal is to set the language to blank before a command.  For example:

```

$ ls /foo
ls: no se puede acceder a /foo: No existe el fichero ó directorio
$ LANG= ls /foo
ls: cannot access /foo: No such file or directory

```

That might be useful to include in your translation, sajnox.

Thanks Vor!! You are always the best!!

Well, here [0] it is a first translation, I have asked the people in the LoCo to improve it and release it.

[0] [http://ubuntuforums.org/showthread.php?t=1017604](http://ubuntuforums.org/showthread.php?t=1017604)

---

### Post by Rocket2DMn on 2008-12-23
> **sajnox said:**
> Thanks Vor!! You are always the best!!

Well, here [0] it is a first translation, I have asked the people in the LoCo to improve it and release it.

[0] [http://ubuntuforums.org/showthread.php?t=1017604](http://ubuntuforums.org/showthread.php?t=1017604)

Cool.  I see you aren't using lists like I am, I find that formatting with them and using different colored and sized headers helps prevent guides from appearing too much like a wall of text, and thus easier to read and use.

List items work like so:

[noparse][LIST][/noparse]

[*] item 1

[*] item 2
[noparse][/LIST][/noparse]

or for numbered lists, just start with [noparse][LIST=1][/noparse] (numbers increment automatically)

If you'd like, I can email you the bbcode contents of my original post so you can apply the formatting and sized/colored section headers to your translated guide.  No need to post your email here, I can do it from your user profile, or you can PM me a different email address other than the one you are registered here with.  Just let me know!

---

### Post by drubin on 2008-12-23
> **Rocket2DMn said:**
> Cool.  I see you aren't using lists like I am, I find that formatting with them and using different colored and sized headers helps prevent guides from appearing too much like a wall of text, and thus easier to read and use.
....

He was not trying to list urls but rather link to them in his post :) 

I think that comes from mailing list etticet since it is not great idea to post HTML emails and having links in the middle of sentences can be disruptive to the train of thought.

---

### Post by Rocket2DMn on 2008-12-23
drubin,
In this case, the lists that I am talking about do not refer to email lists, I'm talking about bbcode lists, for the translated post.  I know the [0], [1], etc. markings for posting links in emails such that they are not embedded in the body of the email.  But that's not what I was talking about.  Compare the formatting in the first post of this thread (the guide) to sajnox's translation and you will see that he isn't using autoformatted indented lists (bullets and numbers).

---

### Post by drubin on 2008-12-23
Ye now I see what you are talking about... Kinda missed the post because it wasn't in english so didn't take notice of it enough to know you were talking about that.

---

### Post by sajnox on 2008-12-23
> **Rocket2DMn said:**
> If you'd like, I can email you the bbcode contents of my original post so you can apply the formatting and sized/colored section headers to your translated guide.  No need to post your email here, I can do it from your user profile, or you can PM me a different email address other than the one you are registered here with.  Just let me know!

Yes please!! It would be great!

Please send me your bbcode and I will apply it in my translation

---

### Post by Rocket2DMn on 2009-01-10
For those interested, at Brian Murray's suggestion I added a brief piece about using the program "ubuntu-bug" to have Apport help with filing bug reports.  From what I can tell, this tool exists in up-to-date versions of Hardy Heron and newer (in Intrepid and newer you don't need the -p flag to accompany the package name, but it doesn't hurt).  [Brian]("https://wiki.ubuntu.com/BrianMurray") is Ubuntu's resident bug god :)
Cheers.

---

### Post by bhadotia on 2009-01-11
> **Rocket2DMn said:**
> 
If you'd like, I can email you the bbcode contents of my original post so you can apply the formatting and sized/colored section headers to your translated guide.

You don't need to email the bbcode. Just tell sajnox to look at the toolbar of his post editor.:popcorn:
You can set your editor preferences in User CP (the first link in the grey bar above). Click on the 'Edit Options' under the heading 'Settings & Options' in the side bar. And in the page that opens sroll to the end of the page. You will find the editor preference in 'Message Editor Interface' under 'Miscellaneous Options' (its the only setting in the section :D)

---

### Post by jeterfan1 on 2009-02-15
thanks for clearing things up. i think i remember during my first install DEselecting a default option for automated reporting, because i had concerns about privacy. but after more than a year using ubuntu such concerns have receded and i'd like to enable auto-reporting -- but i can't find where the option is...much obliged if anyone could refresh my memory.

---

### Post by Rocket2DMn on 2009-02-16
Hey jeterfan, to enable apport, run
```
gksudo gedit /etc/default/apport
```
and change 
```
enabled=0
```
to
```
enabled=1
```
Save and close, then restart apport with
```
sudo /etc/init.d/apport restart
```
Apport should now be running, though some people have found that they can only get it working after a reboot.  You can read a bit more abbout [uwiki]Apport[/uwiki] on the wiki.

---

### Post by pidgey on 2009-02-20
Thank you! This is very useful.:D

---

### Post by jeterfan1 on 2009-02-20
> **Rocket2DMn said:**
> Hey jeterfan, to enable apport, run
```
gksudo gedit /etc/default/apport
```
and change 
```
enabled=0
```
to
```
enabled=1
```
Save and close, then restart apport with
```
sudo /etc/init.d/apport restart
```
Apport should now be running, though some people have found that they can only get it working after a reboot.  You can read a bit more abbout [uwiki]Apport[/uwiki] on the wiki.

thanks! I did all that and restarted, but still don't know if it's running or not (i don't see it listed in System Monitor under Processes). but i'm gonna read that wiki link you posted. domo arigato

---

### Post by alexcckll on 2009-02-23
Umm- please could someone walk through how a user should request an Application Add?

EG - I see an application available out on the Net, and it would fulfil a need... and I can't find that app within Synaptic...

What would be the format of an Enhancement Request?  So eventually I could just collect the app once it had been built and released for whichever version of Ubuntu I'd be on at the time?

---

### Post by nhandler on 2009-02-23
> **alexcckll said:**
> Umm- please could someone walk through how a user should request an Application Add?

EG - I see an application available out on the Net, and it would fulfil a need... and I can't find that app within Synaptic...

What would be the format of an Enhancement Request?  So eventually I could just collect the app once it had been built and released for whichever version of Ubuntu I'd be on at the time?

First, I would suggest you read [this]("https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages"). It explains the process of getting a new package added to the repositories.

The first thing I would suggest you do is search Launchpad to see if there are any needs-packaging bug reports for that package. If there aren't, please file one. An example needs-packaging request can be seen [here]("https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages/ExamplePackageRequest").

If you are interested in packaging the application yourself, please set the needs-packaging bug to 'In Progress', and assign yourself to it. The [Complete Packaging Guide]("https://wiki.ubuntu.com/PackagingGuide/Complete") will help teach you what you need to know to package the application. Once you have a working source package, you can upload it to REVU. Once it is up on REVU, you need to wait for 2 MOTUs to advocate the upload. If the package has some mistakes in it, the MOTUs will add a comment explaining what is wrong and how to fix it. Once you get 2 advocations, the package can be uploaded to the New queue. There, it needs to be approved by an Archive Admin. Once an Archive Admin approves it, it can enter the repositories.

One thing to keep in mind is that we are currently in Feature Freeze. This means that most MOTUs will be focusing on making Ubuntu more stable instead of reviewing packages on REVU. It also means that you will need a [Freeze Exception]("https://wiki.ubuntu.com/FreezeExceptionProcess#FeatureFreeze%20for%20new%20packages") in order for your package to be uploaded. If it is not urgent that your package be in Jaunty, I would suggest waiting until the Karmic repositories open up before trying to get the application uploaded to the repositories.

---

### Post by alexcckll on 2009-02-26
I've had a look at that guide... but it talks about getting source.

In my case - I won't necessarily know where to get that.  It may be a commercial app, it could be a freeware one.

I would want to raise what i know from work as a Complex Order - I might know the main website.. but nothing else.  Only that the app was "available for Linux".

I am an end-user at the moment.  But.. i am on 8.04.  How would I be able to ask for the app to be built for me, if I had a requirement for it?  Or would it be the case of raising the request and then eventually being able to apt-get the app on the next Major Release...

How long do apps normally take to be built for production?

---

### Post by Rocket2DMn on 2009-03-27
This thread has been updated to use Apport / ubuntu-bug as the primary method for reporting bugs to fully align with Ubuntu's best practices on bug reporting.  Cheers!

---

### Post by alexcckll on 2009-04-02
Umm - all of those guides talk from the perspective of a developer who wants to package up their application.

What about the end-user who sees or hears about an application... and would like ot raise what I know as a Complex Order?

From the basis of seeing an application advertised.. but has no clue about taking it further.

---

### Post by Rocket2DMn on 2009-04-02
> **alexcckll said:**
> Umm - all of those guides talk from the perspective of a developer who wants to package up their application.

What about the end-user who sees or hears about an application... and would like ot raise what I know as a Complex Order?

From the basis of seeing an application advertised.. but has no clue about taking it further.

I'm afraid I don't quite follow you.  Is there a question about reporting bugs in there?  I would be happy to explain any questions you have with respect to bug reports.

---

### Post by Rocket2DMn on 2009-04-14
> **billyg said:**
> is there any subscription needed for bug reporting?

You just need an account on Launchpad, which is free to register, and they never spam you with email or anything like that.  When you file a bug report, you are automatically subscribed to that bug, and will receive email updates about that bug report when others comment on it or change its status.  If you place comments on other bugs, you can click a checkbox to subscribe to it so that you also receive updates on that bug report.

---

### Post by ubuntu27 on 2009-05-09
> **Rocket2DMn said:**
> I'm afraid I don't quite follow you.  Is there a question about reporting bugs in there?  I would be happy to explain any questions you have with respect to bug reports.

He is asking how can he request a program to be added to the repositories.

---

### Post by alexcckll on 2009-05-10
> **ubuntu27 said:**
> He is asking how can he request a program to be added to the repositories.
Correct.. any chance instructions could follow?

---

### Post by Rocket2DMn on 2009-05-10
> **alexcckll said:**
> Correct.. any chance instructions could follow?

This was already explained in post 31.  Please see above.

---

### Post by techfanboy81 on 2009-05-18
It is a very detailed step by step guide on filing a bug report.  I have learned so many tips here and a new term like bug triager. How it works and what does it mean. Very useful to me. Thanks. :)

---

### Post by techfanboy81 on 2009-05-30
Excellent information.  I'm a new member of Ubuntu and I'm still exploring and learning too.  Reading your post is very interesting and helpful.

Thanks.

---

### Post by mevan_snp on 2009-06-02
thanks for good guied

---

### Post by hero1900 on 2009-06-12
thank you very much it was very helpful 10/10
:KS

---

### Post by Wim Sturkenboom on 2009-08-31
Can somebody indicate how long it takes before a bug-report is even noticed? Looks like it can be anything from immediate to eternity. Can a bug be kicked like a post here?

I logged [https://bugs.launchpad.net/ubuntu/+bug/389308](https://bugs.launchpad.net/ubuntu/+bug/389308) in june 2009 and after 2.5 month the status has not changed, no requests for extra info or whatever.

They don't seem to care at all and I'm getting pissed off with that.

---

### Post by slakkie on 2009-08-31
> **Wim Sturkenboom said:**
> Can somebody indicate how long it takes before a bug-report is even noticed? Looks like it can be anything from immediate to eternity. Can a bug be kicked like a post here?

I logged [https://bugs.launchpad.net/ubuntu/+bug/389308](https://bugs.launchpad.net/ubuntu/+bug/389308) in june 2009 and after 2.5 month the status has not changed, no requests for extra info or whatever.

They don't seem to care at all and I'm getting pissed off with that.

That sometimes happens, have had the same issues. I could check wheter I can reproduce the bug. You can bump it if you want, and/or hop on irc on the freenode servers and join the #ubuntu-bugs channel to ask around.

Are you aware of any upstream bugs? If so, post them in that bugreport.

I confirmed your bug, both 8.04 and 9.10 have the same issue, so 8.10/9.04 will experience the same.

---

### Post by Wim Sturkenboom on 2009-08-31
Slakkie, thanks

I'm glad that you could confirm. I've just checked launchpad and the status has changed to confirmed. Complaining here helps :scratch:

I will wait a few days to see if the packages will be updated. If not, I will manually edit the file as suggested in [http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/ef5774c9a6fd6c1e](http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/ef5774c9a6fd6c1e) . I did plan to do that but I was not sure if that would not break other stuff.
I also saw a (possible) solution/workaround and will try that soon. Any chance that it will break automatic updates through the package manager (because of a timestamp issue)?

---

### Post by slakkie on 2009-08-31
I changed the status to confirmed, since I was able to confirm it. If I was you, I would update the file - don't think they will update the package that quick ;)

Now we have to wait, but at least you can continue and don't have the error anymore. If you upgrade to another version (to 8.10 and up) you will need to update that file again, since the package manager will just override the file.

---

### Post by Rocket2DMn on 2009-08-31
> **Wim Sturkenboom said:**
> Can somebody indicate how long it takes before a bug-report is even noticed? Looks like it can be anything from immediate to eternity. Can a bug be kicked like a post here?

I logged [https://bugs.launchpad.net/ubuntu/+bug/389308](https://bugs.launchpad.net/ubuntu/+bug/389308) in june 2009 and after 2.5 month the status has not changed, no requests for extra info or whatever.

They don't seem to care at all and I'm getting pissed off with that.

Just for the record, it is generally bad etiquette to bump bugs, they aren't like forum threads.  However, it is OK to post to the bug if you have more or new relevant information or updates.  It's also OK to make note that a bug still exists after upgrading to a new version of Ubuntu and find that the bug is still present.

Also, bugs related to development release versions tend to get more attention - posting bugs from older versions of Ubuntu, even if they are supported like Hardy, don't tend to get as much love.  If possible, you should check to see if bugs exist in the development release as it is likely that a bug triager or developer will request this before proceeding further.

Cheers.

---

### Post by Wim Sturkenboom on 2009-09-01
@Slakkie
I thought it was you ;) One of the posts looked very familiar. I do not really understand how the whole launchpad works but it now seems to be gone upstream. Did you push it up as well? Or did that happen automatically.

The problem that I have with the solution is that I do not now if the sgmlparser version is actually a version 1.1. If it is, no problem, if it's not, there might be stuff that other tcl package require that is in version 1.1 and not in version 1.0. The other option would have been to tell  tclxml that it requires sgmlarser 1.0, but again, I don't know if it breaks something if the actual 1.0 would have been available instead of 1.1.

@Rocket2DMn
I understand that new developments get more attention and I'm not the type that will kick after a few days. However issues with LTS releases should definitely get more attention than issues with non-LTS releases (8.10 and 9.04) as they're aimed at the corporate world.

What would have happened if the bug was not in a newer releases? From your post I understand that there is a real chance that it would never be solved. A suggestion to upgrade to solve it will be out of the question as people have specific reasons to stick to LTS.
Slakkie has now confirmed that it's in 9.10 as well so we might be lucky.

It however leaves a very sour taste that one points out a possible problem and nobody seems to be interested. I admit, I'm probably the first one to benefit from it when it gets solved.

Further my confidence in Ubuntu has taken a serious hit as this could have easily been picked up by a simple testscript.

---

### Post by slakkie on 2009-09-01
> **Wim Sturkenboom said:**
> @Slakkie
I thought it was you ;) One of the posts looked very familiar. I do not really understand how the whole launchpad works but it now seems to be gone upstream. Did you push it up as well? Or did that happen automatically.


It didn't go upstream, I made a link to the Debian bugtracker where this bug is logged as well. So updates on the Debian bugtracker can be followed in Launchpad.

I'm thinking about updating the Debian bug, I use Lenny as well, so I should be able to confirm the bug on Debian as well.

> 
The problem that I have with the solution is that I do not now if the sgmlparser version is actually a version 1.1. If it is, no problem, if it's not, there might be stuff that other tcl package require that is in version 1.1 and not in version 1.0. The other option would have been to tell  tclxml that it requires sgmlarser 1.0, but again, I don't know if it breaks something if the actual 1.0 would have been available instead of 1.1.


You are telling libxml it must use v1.1 and not 1.0. So I think your concern is not needed. But test it, if it breaks other stuff then add this to the bugreport so actions can be taken.

> 
@Rocket2DMn
I understand that new developments get more attention and I'm not the type that will kick after a few days. However issues with LTS releases should definitely get more attention than issues with non-LTS releases (8.10 and 9.04) as they're aimed at the corporate world.

What would have happened if the bug was not in a newer releases? From your post I understand that there is a real chance that it would never be solved. A suggestion to upgrade to solve it will be out of the question as people have specific reasons to stick to LTS.
Slakkie has now confirmed that it's in 9.10 as well so we might be lucky.


I totally agree with you on your LTS standpoint. I have had a similar problem with zsh. I found a bug with zsh version 4.3.4 on Hardy and it was fixed in 4.3.9 which is in Jaunty. They asked me to upgrade to Jaunty from LTS... I was not really happy with that.

I did confirm that the bug was fixed in Karmic and they told me (they is someone in #ubuntu-bugs) that the zsh version of Karmic could end up in the backport section of Hardy. But I have to wait, since I haven't seen any updates so far.

But yeah, LTS and new releases should get more attention then the intermittent releases. I fully agree.

---

### Post by Rocket2DMn on 2009-09-01
> **Wim Sturkenboom said:**
> 
@Rocket2DMn
I understand that new developments get more attention and I'm not the type that will kick after a few days. However issues with LTS releases should definitely get more attention than issues with non-LTS releases (8.10 and 9.04) as they're aimed at the corporate world.

What would have happened if the bug was not in a newer releases? From your post I understand that there is a real chance that it would never be solved. A suggestion to upgrade to solve it will be out of the question as people have specific reasons to stick to LTS.
Slakkie has now confirmed that it's in 9.10 as well so we might be lucky.

It however leaves a very sour taste that one points out a possible problem and nobody seems to be interested. I admit, I'm probably the first one to benefit from it when it gets solved.

Further my confidence in Ubuntu has taken a serious hit as this could have easily been picked up by a simple testscript.

The thing about fixing bugs in already released versions of Ubuntu is that they need to qualify for SRU - Stable Release Update - see [uwiki]StableReleaseUpdates[/uwiki].  LTS releases do seem to get more SRUs, but the bug still needs to qualify.

---

### Post by guriinii on 2009-10-07
Ta very much.

---

### Post by rockstarrem on 2009-10-24
Thanks, this helped me out a lot.

---

### Post by Syed Kazim on 2009-11-24
Thanks for the information. Glad I read this...

---

### Post by kansasnoob on 2009-11-27
I'd appreciate any recommendations regarding filing a bug report against Karmic, I think the kernel itself. Just a bit of history; I began with Karmic about Alpha 4 and all throughout the Karmic dev process I experienced random "freezes" where the only option was to do a hard restart.

I once posted about that:

[http://ubuntuforums.org/showthread.php?t=1276146](http://ubuntuforums.org/showthread.php?t=1276146)

No point in reading all of that, but I continued to experience "random" hard-lockups or "freezes" where absolutely nothing works other than pushing the power button on the box!

Now, it's not a huge deal to me. Jaunty has always been incredibly stable for me, and I multi-boot so I never get stuck with a totally dead machine. (I also have spare parts on hand). But I notice this is still a problem for some.

Now I upgraded Karmic to Lucid as soon as the dev string became available and I don't see that with the new Lucid kernel. I recently reinstalled Karmic for grub2 testing purposes, and there it is! The same hard-lockups or freezes!

So what I don't know is how to file an effective bug report in this situation. I had just such a "freeze" this AM and since then have not booted into Karmic so if I knew what files to attach to a bug report and how to do it I certainly would.

As I said, I could really care less that Karmic doesn't work well for me, but I realize that's not true for everyone so I feel it's important to pursue this so the devs can work it out.

After all, we need to address everyone's issues, not just our own. And this may help with future development, but a poorly written bug report is only time consuming and basically worthless.

---

### Post by Rocket2DMn on 2009-11-28
Hi kansasnoob, freezes are some of the most difficult problems to track down.  I would suggest filing a bug report against the kernel, which would be the "linux" package.  Also consider what you are doing when you get freezes - are you playing video (esp. flash), is your screensaver kicking on, are you using Compiz, or are you doing a suspend/resume?  The triager will most likely ask you to test with Lucid, which you are doing, so if you can reproduce the problem there, that is the best approach.

---

### Post by kansasnoob on 2009-12-03
> **Rocket2DMn said:**
> Hi kansasnoob, freezes are some of the most difficult problems to track down.  I would suggest filing a bug report against the kernel, which would be the "linux" package.  Also consider what you are doing when you get freezes - are you playing video (esp. flash), is your screensaver kicking on, are you using Compiz, or are you doing a suspend/resume?  The triager will most likely ask you to test with Lucid, which you are doing, so if you can reproduce the problem there, that is the best approach.

Thanks for the reply. I did join an existing bug report that sounded very similar and I'm trying some unofficial updates from xorg-edgers that seem to be working well so far!

If the improvement seems to have solved this after about one week of testing I'll search for bugs filed against Karmic Xorg and see if I can help in that way.

---

### Post by jenelle on 2009-12-14
so if for some reason the web pages shut unexpectantly and when you click on the firefox icon to open again it comes up with some box saying there was a problem with a box that was just opened is that a bug ,i did have 2 or 3 boxs open have done so in past with no probs till now

or when it totally takes you out of the internet to just before you actually sign into your computer which you were in there in the first place and you have to re sign in is that a bug too ???

i did re start it so far so good i hope it doesn't do it ever again

very new at it and unsure of things when they go wrong sorry and usually wait for my brother to come over to fix it

---

### Post by Rocket2DMn on 2009-12-14
Yes, in theory any unexpected behavior is a bug, esp. if the program crashes.  If you are able to reproduce these crashes, then that is an excellent time to file a bug report.  Loss of network connection is also a bug, and has been known to happen with wireless more often than wired (some cards more than others, esp. Atheros cards).

---

### Post by jenelle on 2009-12-14
cool thanks , since posting that so far has not happened again , i would not know how to reproduce it either and it had never done it before and i will be quite happy if it never happens again , i do have wireless to the router [think that is right or modem ? ]
when i restarted it vanished so hope that means forever

---

### Post by Rocket2DMn on 2009-12-14
Sometimes certain websites will crash a browser, esp. if they have media like flash, music, or embedded videos.  Also, sometimes users with particular wireless cards will lose their wireless connection under load (that is to say, when they are downloading a lot).  These situations aren't all that common, but that are known to happen.  If you do experience these symptoms, you should file a bug report.  But here's to hoping you won't need to :D

---

### Post by jenelle on 2009-12-14
> **Rocket2DMn said:**
> Sometimes certain websites will crash a browser, esp. if they have media like flash, music, or embedded videos.  Also, sometimes users with particular wireless cards will lose their wireless connection under load (that is to say, when they are downloading a lot).  These situations aren't all that common, but that are known to happen.  If you do experience these symptoms, you should file a bug report.  But here's to hoping you won't need to :D

cheers thanks lets hope i don't need to either it may have been something i had down loaded that caused it cause after i downloaded the pic it closed the web pages, the other thing where it took me out of it totally and back to signing in i do not know what caused that but that has not re happened either .

thank you for your help in the info greatly appreciated , if i need to file a report ever will have to come back and ask how but hopefully never have to

---

### Post by Janeleaper on 2009-12-17
I'm trying to report a bug, but apport keeps crashing.  Apport seems to have a bug too!.  I've tried reporting manually but just keep getting referred back to the Ubuntu help page.  What do I do?

---

### Post by Rocket2DMn on 2009-12-18
Janeleaper, are you using ubuntu-bug to try and file the report, or are you opening a program and going to Help->Report a Problem?  If you know the package you are filing a report against, you can pull up that pacakge on LP and file a bug there.  I heard they recently introduced the feature to redirect you to the wiki page if you are filing a bug manually against Ubuntu, but I have not run into this (perhaps due to specific settings I have).  What package/program are you trying to file a report against?

---

### Post by Janeleaper on 2009-12-18
I am using ubuntu-bug.  It is a kernel problem.  Ubuntu freezes when in sleep mode, then refuses to boot up.

---

### Post by Rocket2DMn on 2009-12-18
Janeleaper, are you able to file a bug manually from here: [https://bugs.launchpad.net/ubuntu/+source/linux/+filebug](https://bugs.launchpad.net/ubuntu/+source/linux/+filebug)

It lets me go through the process of filing the bug.  You can then use
```
apport-collect *bugnumber*
```
to automatically attach information to the bug.

---

### Post by Janeleaper on 2009-12-19
Thanks, I'll try that.

---

### Post by bexpert on 2010-01-13
Forget it.

---

### Post by nutznboltz on 2010-01-19
Launchpad does not even support previewing a comment before entering it.  There is a bug report for this issue. 

Please consider clicking "affects me too" on this bug:
[https://bugs.edge.launchpad.net/malone/+bug/33796](https://bugs.edge.launchpad.net/malone/+bug/33796)

Thanks

---

### Post by kansasnoob on 2010-01-19
Rocket2DMn,

I wonder if you might be able to help me with this. I filed a bug report using "ubuntu-bug grub-pc" using Karmic:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/509438](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/509438)

So it is fixed in Lucid but not in Karmic and I'm told:

> If you want to have this fixed/changed in karmic you have to nominate this bug for it.

I might note here that I previously requested these packages be updated in Karmic:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/485457](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/485457)

And I was told:

> By the way, we're not going to do a full update in karmic-proposed; the changes are just too big and very many of them are not required in a stable release. If you want to help to identify individual isolated changes that are needed, feel free (in separate bugs).

So I've been Googling trying to figure out how to "nominate this bug" for Karmic. I've gotten as far as:

[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

But I still don't see how to file a request. I feel like I'm running in circles :D

---

### Post by Rocket2DMn on 2010-01-19
Hi kansasnoob,

To nominate a bug for a release, click the link "Nominate for release" in the line below the bug package/status/importance.  The wiki page you found for SRU is the correct page you need - more specifically, you want the Procedure section - [https://wiki.ubuntu.com/StableReleaseUpdates#Procedure](https://wiki.ubuntu.com/StableReleaseUpdates#Procedure)

You would do steps 1-3, at which point a member of the SRU team will decide whether to fix it or not.  It might also help if you find the version that the bug was first fixed in, and if you can find the changelog, that is helpful, too.

TBH, I would not be surprised if they decline to SRU this bug since they aren't likely to come out with a point release for Karmic as it is not LTS, and the bug applies during installation.  However, that doesn't mean you shouldn't try.

---

### Post by kansasnoob on 2010-01-19
Done! Thank you. Sometimes the simplest things escape my old eyeballs :D

I do realize that what I think may be a great idea may not truly be feasible but it's always worth a try.

---

### Post by kansasnoob on 2010-01-26
Well I'm a bit steamed this time :mad:

Look here:

[http://ubuntuforums.org/showthread.php?t=1391024](http://ubuntuforums.org/showthread.php?t=1391024)

So I can not even boot the "ill" OS.

Worse yet I can't report a failure at iso testing without filing a bug report.

All installations of 8.04.4 end up in a kernel panic. That's not very good.

That's a major failure in Ubuntu quality control!

BTW the bug is:

All installations of 8.04.4 result in kernel panic.

The primary bug was:

Someone included the wrong link in the iso testing notification.

Conclusion:

8.04.4 should be delayed!

---

### Post by rajasegar_c on 2010-03-20
Thanks for the info

---

### Post by jfreak_ on 2010-05-22
what do i do if the bug is related to installation wherein the live environment is not getting booted?

---

### Post by Rocket2DMn on 2010-05-22
> **jfreak_ said:**
> what do i do if the bug is related to installation wherein the live environment is not getting booted?

Are you saying you cannot access the desktop on an installation, or that you are unable to boot from a LiveCD?

---

### Post by jfreak_ on 2010-05-22
can't complete the boot from cd

---

### Post by Rocket2DMn on 2010-05-22
Do you see any errors when trying to boot from the LiveCD? This could help us determine which package is causing the issues.  If no errors, what other behavior are you seeing, i.e. in what way does the disc not complete its boot?

---

### Post by ranch hand on 2010-05-23
Did you check the md5sum of image that you downloaded?

---

### Post by kansasnoob on 2010-05-28
> **jfreak_ said:**
> can't complete the boot from cd

Need much more info. Exactly what happens?

---

### Post by kansasnoob on 2010-05-28
I'm wondering how to get some response to a really horrible bug:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

That's a killer and I was even bold enough to subscribe Colin Watson. BTW I'm Erick Brunzell there.

I'm in hopes that I can find a way of providing more focus on that during Maverick iso-testing (I'm tester Lance) but I'm doubtful.

IMHO that's the nastiest bug I've ever seen in Ubuntu.

---

### Post by karthick87 on 2010-06-07
Thanks..! Very helpful information..

---

### Post by Keith Myers on 2010-06-18
I've filed 4 bug reports so far on problems with random crashes.  All of the reports seem to get an automated response to try an "uplevel kernel"  I read through the links and can not understand what is required of me.  I'm a new Linux user.  I can't make sense of what is an uplevel kernel.  I can't make sense of the build matrices that supposedly tell me what kernel is equivalent to the stock kernel in Ubuntu 10.04 LTS.  I replied in several of the bug reports that I need help in determining just what uplevel kernel I am supposed to try to maintain the bug report as active.  I've never received any reply to my questions. From how I read the equivalency matrix, I gather I'm supposed to try an uplevel kernel from last year in August to replace the stock one issued in April of this year.  That kernel has numbering of less than the stock one. This makes no sense to me.

Keith
:confused:

---

### Post by Rocket2DMn on 2010-06-18
Are you talking about *upstream* bug reports? Do you have any links to some of the bug reports in question?

---

### Post by alexcckll on 2010-06-19
I have to ask... surely from the perspective of the Average User (which I count myself among, as both my Ubuntu machines were preinstalled), isn't a triage team better placed to file and chase incidents upstream?

---

### Post by Rocket2DMn on 2010-06-19
> **alexcckll said:**
> I have to ask... surely from the perspective of the Average User (which I count myself among, as both my Ubuntu machines were preinstalled), isn't a triage team better placed to file and chase incidents upstream?

Upstream developers often ask for more information, which a triager usually cannot provide.  Triagers do forward bugs upstream sometimes, but it is still up to the original reporter to follow up. Some upstream developers will post in the Launchpad bug report (assuming a link was provided in the upstream one), but most don't.

---

### Post by karthick87 on 2010-06-19
I have reported a bug to launchpad and the fix was committed but when it will be released..?

---

### Post by Rocket2DMn on 2010-06-19
> **getyourkarthick said:**
> I have reported a bug to launchpad and the fix was committed but when it will be released..?

Fix Committed usually means that the bug is fixed in Ubuntu's development release.  Occasionally bugs are released in the stable version, in which case it is a Stable Release Update.  See [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates) for more info about that.  Typically though, the bug will be fixed for you when you upgrade to the next Ubuntu version after it is releases (in this case, in October).

---

### Post by phendrome on 2010-06-21
Thanks for the **very informative** thread. Thumbs up!

---

### Post by alexcckll on 2010-06-24
> **Rocket2DMn said:**
> Fix Committed usually means that the bug is fixed in Ubuntu's development release.  Occasionally bugs are released in the stable version, in which case it is a Stable Release Update.  See [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates) for more info about that.  Typically though, the bug will be fixed for you when you upgrade to the next Ubuntu version after it is releases (in this case, in October).
Umm -but considering that the current release of Ubuntu is now a Long-Term-Support one... wouldn't many fixes be released in the next service pack (10.04.1), and made available for all Lucid users and find their way onto the new CDs?

---

### Post by Rocket2DMn on 2010-06-24
> **alexcckll said:**
> Umm -but considering that the current release of Ubuntu is now a Long-Term-Support one... wouldn't many fixes be released in the next service pack (10.04.1), and made available for all Lucid users and find their way onto the new CDs?

It really depends on the bug, they are more likely to fix bugs in LTS releases, but it still needs to meet the SRU requirements.  I would say the biggest exceptions to this would be kernel version upgrades and Firefox upgrades that make their way into LTS releases.  These provide better (and new) hardware support for web browsing security and functionality.

---

### Post by Richard1 on 2010-06-27
Thank for the Info:p

---

### Post by plurga on 2010-07-05
thanks for the info , it will help me alot , bcs i am a ubuntu's beginner and is important to know what's a bug and what is not a bug.

---

### Post by baz19 on 2010-07-27
Thanks this was very useful

---

### Post by purplegirl5 on 2010-08-10
Thank you. Very helpful.

---

### Post by Macbologos on 2010-08-12
I ( A NEWBEE) just joined and am not fond of bugs TUVM for the post.

Thinking about installing lucid on my Studio XPS 435MT. I just want to say NO to Vista! Booted what I think is the 64bitt version from flash drive and all ready have wireless connection issues on the 1505 draft 802.11 Wlan mini card (From Broad Comm I think)

Have to say though I like this QS!!

I'm not even smart enough to ask any questions yet, unless U think it's a bad idea to go with lucid on this machine? So back to the net, the posts, & the books.
Thanks again!

---

### Post by tailong168 on 2010-09-04
I am a beginner,thank you for you information, from wihch I know something about Bug.

---

### Post by Razor338 on 2010-12-27
thanx!

---

### Post by johny28 on 2011-01-11
is good for beginner ... thanx

---

### Post by telovin on 2011-04-06
Hi,
I have a doubt. My firefox icon is not showing the usual firefox logo, instead it just shows a small white pinned paper like thing on the panel. When I clicks on it, it opens the firefox browser but only the appearance of firefox button is changed.Its been there in lucid lynx also. But my karmic had proper firefox logo.Is this a bug? If so should I report through the bug filling form?

---

### Post by Rocket2DMn on 2011-04-06
> **telovin said:**
> Hi,
I have a doubt. My firefox icon is not showing the usual firefox logo, instead it just shows a small white pinned paper like thing on the panel. When I clicks on it, it opens the firefox browser but only the appearance of firefox button is changed.Its been there in lucid lynx also. But my karmic had proper firefox logo.Is this a bug? If so should I report through the bug filling form?

It sounds like the shortcut just doesn't know where the firefox icon is.  Right click and select Properties. In the window that pops up, click the icon box on the left and navigate to /usr/share/icons/balanzan/scalable/apps and select firefox.png.

---

### Post by telovin on 2011-04-08
Hi,
I am unable to find scalable inside icons. I could find scalable inside default.kde4. 
Scalable-apps-phonon-xine.svgz
there is no firefox.png there

---

### Post by Rocket2DMn on 2011-04-08
> **telovin said:**
> Hi,
I am unable to find scalable inside icons. I could find scalable inside default.kde4. 
Scalable-apps-phonon-xine.svgz
there is no firefox.png there

If they aren't there, then they must be somewhere else.  It doesn't sound like a bug to me, so please start a new thread and other forum members who know can help you.  Good luck.

---

### Post by telovin on 2011-04-08
Thank You Rocket2DMn. I will start a new thread.

---

### Post by telovin on 2011-04-10
Got my firefox logo back. It was there on usr/share/pixmaps/firefox.png.
Thanks a lot for your guidance RocketMn.:)

---

### Post by transeuro on 2011-09-09
Most of the information related to the bug is almost covered in the post mentioned int he forum. Great help for the beginner.

---

### Post by ahmed.cnbd on 2011-10-18
thanks that was really useful

---

### Post by MonolithImmortal on 2011-10-18
This was useful to me a good while back, just wanted to swing by and say thanks.

---

### Post by kral2008 on 2011-12-08
Hi,
I cant control my laptop screen brightness with "Fn+ F5/F6" key and also with Brightness control tool in settings.
I tried to edit xorg.conf file but it didn't work.
System info: VAIO F133FXB with NVIDIA 425M graphic card.


sorry for my English,
kral

---

### Post by Rocket2DMn on 2011-12-08
Kral, please start a new thread for your problem and the community will do their best to help you out. I recommend either the [Absolute Beginner Talk]("http://ubuntuforums.org/forumdisplay.php?f=326") forum.

---

### Post by kral2008 on 2011-12-09
> **Rocket2DMn said:**
> Kral, please start a new thread for your problem and the community will do their best to help you out. I recommend either the [Absolute Beginner Talk]("http://ubuntuforums.org/forumdisplay.php?f=326") forum.

Thanks, started: [http://ubuntuforums.org/showthread.php?p=11524462#post11524462](http://ubuntuforums.org/showthread.php?p=11524462#post11524462)

---

### Post by Sauce Boss on 2012-03-27
> **Rocket2DMn said:**
> **OK stop!**  It looks like there is a lot of text here, but I promise you that [COLOR="Blue"]submitting bug reports is **not complicated**[/COLOR].  This post will attempt to walk you through filing [COLOR="Red"]_good bug reports_[/COLOR] in Ubuntu's bug tracker, called [Launchpad]("https://launchpad.net/") - specifically at [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/). Understanding the process will help you get your "bug" solved as quickly as possible.

Due to the large volume of bugs that get reported, it is important that you file bugs correctly and with as much information as possible.  As a bug triager, I assure you that this will *significantly* improve the chances of getting your bug looked at and fixed in a timely manner!

[COLOR="DarkSlateBlue"]_**[SIZE="4"]A Brief Background on Bugs:[/SIZE]**_[/COLOR]

_[SIZE="3"]What a bug is:[/SIZE]_

A "[bug](http://en.wikipedia.org/wiki/Software_bug)" exists in software when a program does something unexpected, usually causing problems for the user.  *Some* examples include:
[LIST]
[*]a program crashing or closing unexpectedly
[*]a (simple) missing feature
[*]unexpected error messages, often preventing a program from continuing normal operation
[*]other unexpected behavior
[/LIST]

_[SIZE="3"]What a bug is not:[/SIZE]_
[LIST]
[*]a support request (use the forums!)
[*]a missing feature that requires more than minimal work to implement
[*]a bad configuration on your machine (ask here on the forums for help tracking it down)
[/LIST]

_[SIZE="3"]How do I know?[/SIZE]_

Those who are very new to Ubuntu and/or Linux in general should make posts here on the forums before filing bug reports.  Many people run into problems that aren't really bugs, and many common problems that are bugs have already been filed (but please check for yourself!).
The forum community members can often help you work around bugs - *please ask* if they think you should file a bug report.

[CENTER][COLOR="Red"]_**[SIZE="5"]-> Before filing a bug report <-[/SIZE]**_[/COLOR][/CENTER]
[LIST]
[*]Make sure you have an account on [Launchpad]("https://launchpad.net/") - you can't file a report without one.  If you don't have one yet, go to "Log in / Register" at the top right of a Launchpad page, then follow the directions.
[*]Search [Launchpad's Bugs in Ubuntu]("https://bugs.launchpad.net/ubuntu/") for duplicate reports - is there already a bug open for your problem?  If so, respond to that bug report, and confirm it if possible (change the **Status** from *New* to *Confirmed*).  If you find such a report, please be sure that it is for the *exact* same problem that you have.  If it is a bug related to a specific piece of hardware, then you should also have that hardware (or one extremely similar).  If it's not the same, file a new report and mention that other bug as a similar problem - a triager can help you determine if the problem is actually the same.
[/LIST]

[CENTER][COLOR="Green"]_**[SIZE="5"]-> Steps for filing a bug report <-[/SIZE]**_[/COLOR][/CENTER]

[color=navy]**[size=2]Filing bug reports can be automated via the use of [uwiki]Apport[/uwiki].**[/color][/size]

Apport is a tool that ships with Ubuntu and can assist both end users and developers. It automatically attaches important data to the report, like version information and relevant logs.  In some cases, it will automatically appear to help you file reports (like after program or system crashes).

[LIST=1]
[*]In many programs in Ubuntu you can go to **Help -> Report a Problem** or **Help -> Report a Bug** and Apport will collect information automatically for you and take you to the bug filing page on Launchpad where you can elaborate on your problem.
[LIST]
[*]Alternatively, from the terminal you can run the following to have Apport collect information automatically for you:
```
ubuntu-bug *packagename*
```
It is important that you try to file the report under the [right package]("https://wiki.ubuntu.com/Bugs/FindRightPackage").  This can often be confusing, so try your best. If you really don't know, leave the package name off and you will be prompted about some common problem areas.
[/LIST]
[*]Apport will now collect some information and prompt you to to send the report. You may view what is being uploaded by expanding *Content of the report*. Now click "Send Report". A browser window will open and navigate to Launchpad.  If needed, login, then proceed.
[*]After Launchpad is finished processing, describe the bug in one short statement (this is the bug's title - be descriptive!). Click "Next".
[*]A list of bugs that Launchpad thinks might be similar are listed - check them.  If you don't find a match, click "No, I need to report a new bug".
[*]Now you can describe your bug in more detail. Include steps to reproduce the bug, and methods you've tried to solve the bug or work around it.
[*]If you need to attach any files (like screenshots) to the bug report, expand *Extra options* and go to the *Include an attachment* section at the bottom and browse for the file. You can only upload one file at a time, so if you have multiple files to upload, you will need to add them in Comments after submitting the bug report.
[*]When you believe there is enough information provided, click "Submit Bug Report".
[/LIST]

[CENTER][COLOR="Orange"]_**[SIZE="5"]-> After filing a bug report <-[/SIZE]**_[/COLOR][/CENTER]
[LIST]
[*]You can add extra comments at the bottom of the bug report. You can also add more attachments by clicking "Add attachment or patch".
[*]You should receive emails about changes and responses to the bug report - [COLOR="Red"]**follow up!**[/COLOR]  A bug can't be completed until you provide all information that has been requested.  Bookmark the bug report and check back regularly for updates.
[*]You may be asked to file a bug report *upstream* - this means doing something similar to what we did above, but at a website outside of Launchpad.  This can get a little complicated, so feel free to ask how to proceed - more information is available [here]("https://wiki.ubuntu.com/Bugs/Upstream").
[*]You may also be asked to check if the bug exists in the development version of Ubuntu by using a LiveCD.
[/LIST]

[COLOR="Indigo"]_**[SIZE="4"]Generic lifecycle of a bug report:[/SIZE]**_[/COLOR]
[LIST]
[*]User experiences a problem and files a bug report
[*]If lucky, somebody else will confirm the bug report (**do not** confirm your own bugs!)
[*]A triager looks at the bug report.  If more information is needed, the triager will request it.  The bug reporter will provide the requested information.  Repeat as necessary.
[*]When the triager is satisfied that there is enough data, the bug will be marked as *Confirmed* (or even better, as *Triaged*).  The triager should set an **Importance** on the bug in most cases, and possibly assign it to a developer or team.
[*]A developer looks at the bug report - they will either ask for more info, fix the bug or reject it (either because it's not worth fixing, or it's not actually a bug).
[*]The bug report is closed with a **Status** of *Fix Released*, *Won't Fix*, or *Invalid*.
[/LIST]
When fixes are released for bugs, the fixed version of the program is usually not made available in stable versions of Ubuntu unless it is a security fix or meets the criteria for a [Stable Release Update]("https://wiki.ubuntu.com/StableReleaseUpdates").  The fixed version of the program is usually placed into Ubuntu's development release (unstable).

[COLOR="DimGray"]_**[SIZE="4"]Some relevant and useful links:[/SIZE]**_[/COLOR]

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
[http://www.chiark.greenend.org.uk/~sgtatham/bugs.html](http://www.chiark.greenend.org.uk/~sgtatham/bugs.html)
[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)
[https://wiki.ubuntu.com/Bugs/Responses](https://wiki.ubuntu.com/Bugs/Responses)
[http://ubuntuforums.org/showthread.php?t=734460](http://ubuntuforums.org/showthread.php?t=734460) - This thread's predecessor (short and sweet)
**[Guia para reportar bugs]("http://ubuntuforums.org/showthread.php?t=1017604")** - This guide translated in Spanish, thanks to [sajnox]("http://ubuntuforums.org/member.php?u=362457").

-----------------------

If you have further questions or feedback about filing bug reports, please feel free to ask in this thread.

[RIGHT]Cheers,
[COLOR="DarkRed"]***[SIZE="3"]Rocket2DMn[/SIZE]***[/COLOR][/RIGHT]

[IMG]https://launchpadlibrarian.net/1812570/bugsquad.png[/IMG]
Really useful, gonna try it as soon as I can.

---

### Post by gentryliving on 2012-03-27
This is a very detailed and complete explanation. Thanks for this post.

---

### Post by teward on 2012-05-30
Didn't search all the pages, but make sure you have included in "Filing a Bug" under Apport that it won't immediately be visible to everyone, as apport filed bugs are automatically marked as private, as they usually contain private data in the report (so only certain people can access).
 
Also, as I've been semi-alive-ish here, and I've been working towards getting more access to bugs, if there's any basic questions on bugs not explained here, or you want me to include additional information not listed here already, lemme know (I'm on the Bug Squad, so I'm somewhat well versed in bug-fu)

---

### Post by epikvision on 2012-07-16
Awesome guide. It makes bug reporting look easier than it seems. The only question is to encounter the bug...

---

### Post by EkiLibRiuM on 2012-09-28
thank you for this great tutorial for people like me it's realy very usefull...hope to see mooe sonn..thank's a lot .respect.

---

### Post by Peter Ketel on 2012-09-29
Nothing works. Just want to ask a simple question: Is there a GUI that enables one to do some programming. And by that I don't mean the kids stuff like Glade. GNOME is just too tedious to get under control for a nice GUI.

---

### Post by epikvision on 2012-10-22
Thank you for the guide! It cleared up some myths and may help prospective bug reporters!

---

### Post by Marcappuccino on 2012-10-26
Remember, you can use ```
ubuntu-bug -w
```, and click on the window of the buggy app if you don't know the package name or for simplicity.

---

### Post by VanillaMozilla on 2012-11-16
Could the first post please be edited to include the
ubuntu-bug -w command?  If it actually works, this is really important.

Another thing to point out is that you can convert Launchpad questions to bug reports, but if you do that, your bug report will probably be closed with a nasty canned note.  Should this be clarified in the first post (and in bug-reporting directions everywhere)?

---

### Post by Malsasa on 2012-11-27
Thank you, Rocket2DMn! It will be useful for me...

---

### Post by sujitbikash on 2013-02-01
Thank you very much to give me the basic need helpful guide line which is very important to for me to use ubuntuforums.

---

### Post by chahar on 2013-02-14
Thank you Rocket2DMn! This will really be useful.

---

### Post by Noelofkraal on 2013-02-19
thanks for the info 
I am in the process of getting a launchpad account and you will be hearing from me soon. Thank you for the great info though

---

### Post by david98 on 2014-04-20
Thank you for this information it is very easy to understand.

---

### Post by plurga on 2015-03-10
thanks a lot for the info.

---

### Post by melisang on 2017-12-13
thanks for clearing things up. i think i remember during my first install DEselecting a default option for automated reporting, because i had concerns about privacy. but after more than a year using ubuntu such concerns have receded and i'd like to enable auto-reporting -- but i can't find where the option is...much obliged if anyone could refresh my memory.

---

### Post by Rocket2DMn on 2017-12-19
On Ubuntu 16.04: System Settings -> Security and Privacy (under Personal), go to the Diagnostics tab and enable "Send error reports to Canonical"

---

### Post by dolios on 2019-04-30
Thank you a lot for the information. If I only knew this about 2 years ago :/

---

### Post by iamjessa on 2019-08-09
Hello!
It is very helpful to me! Glad I register to this site1

Best Regards,
Jessa

---

### Post by falloutboy2 on 2020-08-15
I have a bug report from dmesg, however I am not sure if it is a kernel bug report or a packaged based report.. 
I have included the text around it in case the message is related to the initialization of something else and I am asking because I don't want to get it wrong and waste developer time.
Thanks in advance.

[    1.460462] HugeTLB registered 2.00 MiB page size, pre-allocated 0 pages
[    1.464366] ACPI: Added _OSI(Module Device)
[    1.464367] ACPI: Added _OSI(Processor Device)
[    1.464367] ACPI: Added _OSI(3.0 _SCP Extensions)
[    1.464368] ACPI: Added _OSI(Processor Aggregator Device)
[    1.464369] ACPI: Added _OSI(Linux-Dell-Video)
[    1.464370] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[    1.464371] ACPI: Added _OSI(Linux-HPI-Hybrid-Graphics)
[    1.620100] ACPI: 2 ACPI AML tables successfully acquired and loaded
[    1.646358] ACPI: Dynamic OEM Table Load:
[    1.655974] ACPI: Interpreter enabled
[    1.655992] ACPI: (supports S0 S1 S4 S5)
[    1.655993] ACPI: Using IOAPIC for interrupt routing
[    1.656027] HEST: Enabling Firmware First mode for corrected errors.
[    1.656027] HEST: Table parsing has been initialized.

**[    1.656027] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug**

[    1.656027] ACPI: Enabled 4 GPEs in block 00 to 3F
[    1.674715] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-7e])
[    1.674721] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI HPX-Type3]
[    1.674946] acpi PNP0A08:00: _OSC: platform does not support [SHPCHotplug PME

---

