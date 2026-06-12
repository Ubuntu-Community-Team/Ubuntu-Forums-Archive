---
title: "Piclens For Linux (let's Order Them To Do It)"
date: 2008-04-22
forum: Desktop Environments
---

### Post by bijeeshvs on 2008-04-22
hi guys i came across the piclens plugin for firefox and i found it really cool and amazing ( you can check it here  [http://www.piclens.com/site/firefox/win/](http://www.piclens.com/site/firefox/win/) ) 
but the sad thing is that they have not yet made a linux version an thats totally disgusting. I have send a mail to their feedback requesting a linux version. I know people here (linuxbees) can make more amazing things than piclens, but its also a matter of acceptance,  so i am asking you a hand in letting them know, there are people here still alive and we are not happy with their ignorance. Here is their mail ID   
[email]feedback@piclens.com[/email]



Lets Bombard Them..............................

---

### Post by mihai.ile on 2008-05-22
I already sent them an e-mail some months ago...
[http://www.piclens.com/site/support/feedback.php](http://www.piclens.com/site/support/feedback.php)
It seems that it works, they began thinking about Linux support which is not bad...

---

### Post by nite_monkey on 2008-06-16
They said that they haven't made it for linux yet because of "resource constraints," or at least that is what their FAQ page says. If someone could make something that would do the same thing as piclens (or better) that is only for linux, that would be pretty cool.

---

### Post by Keen101 on 2008-07-21
I've been trying to edit the windows version, to work in linux, but to no prevail. I really don't much about firefox add-ons, and i really can't program either. 

but, here are some files that i think may be helpful to porting a version to linux. I have tried to convert the DLL files into something linux can use, not sure if it helps or not.

---

### Post by bijeeshvs on 2008-07-23
> **Keen101 said:**
> I've been trying to edit the windows version, to work in linux, but to no prevail. I really don't much about firefox add-ons, and i really can't program either. 

but, here are some files that i think may be helpful to porting a version to linux. I have tried to convert the DLL files into something linux can use, not sure if it helps or not.

yes the files are here, but how to use it????????????????????

---

### Post by minhaaj on 2008-08-17
shouldn't the file be in xpi format ? a little how-to would be appreciated

---

### Post by rakan21 on 2008-08-18
K I just emailed Cooliris or whatever the company's name is. 
I asked them if its Open Source.

If it is I will work my *** off to try to get it to work with Linux.

I just need to get a reply and then I have to install Linux Ubuntu once again. Get the support and so on. So pretty much about a day.

But I can't do this on my own. I'm going to get some help here in Bahrain. (we have a Linux users group).
I"ll attend the meeting and bring this up as a discussion and see how can help.

and it also be great if we can get some help from you guys. If we can then that would be great. Many of you seem like you know what your doing and others seem to have some really good suggestions. 

SO Just think of this as a global Open Source project that we're all going to make.

Hopefully we will be successful. 

[CENTER]-Rabayah, Rakan
Best of luck to all of us.[/CENTER]

---

### Post by Prominence on 2008-08-30
Any progress on this?

---

### Post by Ms_Angel_D on 2008-08-30
This would be awesome I love piclense and would love to see it on linux. So I would like to echo Prominence and ask has there been any progress on this?

Angel

---

### Post by Keen101 on 2008-09-05
While it may not be fully open source (such as the source to the windows .DLL files) most of the code seems to be in plain text, and if you are a programmer, especially one who develops plugins to firefox, i would assume it would be faily easy to unzip the .xpi files, and decipher them.

That's what I tried to do, I tried to convert the .dll files in the windows version to a linux binary file, but it did not really work and if it did i really don't know how to use them.

---

### Post by bijeeshvs on 2008-09-07
> **Keen101 said:**
> While it may not be fully open source (such as the source to the windows .DLL files) most of the code seems to be in plain text, and if you are a programmer, especially one who develops plugins to firefox, i would assume it would be faily easy to unzip the .xpi files, and decipher them.

That's what I tried to do, I tried to convert the .dll files in the windows version to a linux binary file, but it did not really work and if it did i really don't know how to use them.

Great effort buddy ..........................
keep it up, I think we can bring this to life. I will try to get few help

---

### Post by nbiz on 2008-09-08
I really miss this, having ditched my last Windows machine. 

Given what progress has been made in Compiz Fusion etc, (even leading the way perhaps) and the 3D full-screen nature of this plugin, I'm thinking those guys may be the best ones to ask.. flickr results on the cube? Wobbly 3D google image  results? The possibilities...

---

### Post by petzworld999 on 2008-09-08
I just tried changing the build environment and got it to install in Firefox, but is not functioning at all. You need to modify the install.rdf file to say this:

```


<?xml version="1.0"?>

<RDF xmlns="http://www.w3.org/1999/02/22-rdf-syntax-ns#" 

     xmlns:em="http://www.mozilla.org/2004/em-rdf#">

    <Description about="urn:mozilla:install-manifest">

        <em:id>piclens@cooliris.com</em:id>

        <em:name>PicLens</em:name>

        <em:version>1.8.0.4280</em:version>

        <em:description>Discover More</em:description>

        <em:creator>Cooliris Inc.</em:creator>

        <em:targetApplication>

            <Description>

                <em:id>{ec8030f7-c20a-464f-9b0e-13a3a9e97384}</em:id>

                <em:minVersion>2.0</em:minVersion>

                <em:maxVersion>3.0.*</em:maxVersion>

            </Description>

        </em:targetApplication>

<em:targetPlatform>Linux_x86-gcc3</em:targetPlatform>

        <em:homepageURL>http://www.piclens.com/</em:homepageURL>

        <em:iconURL>chrome://piclens/content/piclens-32.png</em:iconURL>

    </Description>

</RDF>



```

Then, repackage and install. Like I said, it installs, but does not work.

---

### Post by bijeeshvs on 2008-09-08
hello guys, is there any programmers out there who can build this from scratch rather than converting from the windows version...........

---

### Post by Zynaps on 2008-09-14
Hi all,

New Ubuntu user here, I have been hunting for an answer to this very question.

I will take a look at the archive someone posted before to see if there is anything usable in it.  Here is a progress log of how far I got with the problem before thinking "gee, I wonder if someone has already thought about this..." :)

Download cooliris windows / firefox 3 version, save the installer to your local machine by right clicking and saving link.

Open the xpi file in the archive manager and delete the meta_inf folder.

Edit the install.rdf file, simply change:

<em:targetPlatform>Linux_x86-gcc3</em:targetPlatform>

Then open the xpi in firefox.  Install as normal, restart firefox.

Firefox reports that Cooliris is installed, however the icon does not appear and it seems like it can't be used.

On investigation it's because Cooliris uses some DLL's to extend its features.  The following DLL's are used:

avcodec-51.dll
avformat-52.dll
avutil-49.dll
cooliris19.dll
freetype.dll
pixomatic.dll
coolirisstub.dll


Tackle these one at a time to see if a suitable replacement can be found

avcodec-51.dll
Googled for avcodec-51.so
Appears to be part of the libavcodec51 package
[http://packages.ubuntu.com/intrepid/i386/libavcodec51/download](http://packages.ubuntu.com/intrepid/i386/libavcodec51/download)

avformat-52.dll
[http://packages.ubuntu.com/intrepid/libavformat52](http://packages.ubuntu.com/intrepid/libavformat52)

avutil-49.dll
[http://packages.ubuntu.com/intrepid/libavutil49](http://packages.ubuntu.com/intrepid/libavutil49)

cooliris19.dll
Will need reverse engineering (decompile, recompile???)

freetype.dll
Presumably replaceable with libfreetype6?
[http://packages.ubuntu.com/feisty/libfreetype6-dev](http://packages.ubuntu.com/feisty/libfreetype6-dev)

pixomatic.dll
Its not the same 3d rasterizer made by radgametools is it?
[http://www.radgametools.com/pixomain.htm](http://www.radgametools.com/pixomain.htm)
If so, pixomatic2 is apparently linux compatible and has an SDK somewhere...
So anyways...  It seems all but 2 of the DLL's are available in native linux versions.  Only pixomatic and cooliris would need reversing.

That's where I am a bit stuck.  Is it possible to reverse engineer the DLL into x86 assembly, then use a compiler to produce an SO library?

If we can replace these libs, then it should be possible to browse through all the source files and fix the necessary function calls and includes to get a working version.

However there is also the matter of:

cooliris.xpt

Is it possible to reverse engineer a windows XPCOM object, or are there any tools available?  Or is it even necessary?  XPCOM stands for Cross Platform Component Object Model ([http://en.wikipedia.org/wiki/XPCOM](http://en.wikipedia.org/wiki/XPCOM)) does this mean it will work wherever there is a Mozilla framework to run it?  I would assume so...  but then, there may be certain differences I am not aware of.

Should, perhaps if and maybe, fudging this to work would be an interesting feat.

Like someone suggested, maybe it would be better if someone came up with a competing linux-native open source program, at least it wouldn't be a hack...  But is there a short term solution to be found in hacking cooliris to work?  I don't know.

Anyway...  I hope this helps out in some way. :D

Cheers

(p.s. I just posted a related topic on the general issue of FF windows extension incompatibility if anyone is interested: [http://ubuntuforums.org/showthread.php?p=5787704#post5787704](http://ubuntuforums.org/showthread.php?p=5787704#post5787704))

---

### Post by davidw89 on 2008-09-14
Yeah i am missing this in Linux i wonder if their developers are doing anything about it?

---

### Post by mihai.ile on 2008-09-16
well did you already sent them an e-mail asking about linux? remember it's us that can make them release a linux version. More the requests, more the probability that te'll seriously consider a linux version.

---

### Post by Bakon Jarser on 2008-09-19
Good work zynaps.  I wish I knew enough to help out.

---

### Post by mihai.ile on 2008-09-24
Just thinked about it a little...
I just remembered that they have a Mac version of the plugin. Now wouldn't it be easier to try the Mac -> Linux instead of Windows -> Linux?
Right now i'm at work, but if I have time this week i'll have a look into the package to see if I find something relevant, you could try the same and see what we get.

Keep in touch...

---

### Post by bijeeshvs on 2008-09-24
> **mihai007 said:**
> Just thinked about it a little...
I just remembered that they have a Mac version of the plugin. Now wouldn't it be easier to try the Mac -> Linux instead of Windows -> Linux?
Right now i'm at work, but if I have time this week i'll have a look into the package to see if I find something relevant, you could try the same and see what we get.

Keep in touch...

great Dude, all the best for your effort,,,,,,,,,,,,,

---

### Post by mgc8 on 2008-09-27
Hello,

I am very interested in a Linux CoolIris port, that's how I found this thread. However, I'm afraid it won't be as easy as you think :-/

First of all, even though some of the libraries are actually open-source, the most important is the proprietary one -- cooliris19.* -- which unfortunately contains by far the largest ammount of code.

Interestingly enough, by comparing Mac vs. Win versions, it seems they only use ffmpeg libs and pixomatic under win -- perhaps MacOS provides better/native alternatives, I don't know as I've never programmed for it.

Anyway, pixomatic is as proprietary as they come (and it costs some 10.000$) so it's no chance of getting it open-sourced. Even then, it would leave the huge cooliris library which would be quite hard to reverse engineer, probably easier to re-write from scratch.

The rest of the XPI contains only glue, i.e. means of connecting the software to FireFox, it's nothing important or helpful in a porting endeavour.

All this considered, I think the only choice (short of cooliris releasing a Linux version or getting some sort of compiz plugin that does the same) would be to ask the WINE guys for help -- after all, getting windows dll's to run on Linux **is** their speciality. So I'd suggest asking them for a way to get the plugin working, maybe it's not even that hard, as many time more complex windows apps run great via Wine. If it uses pixomatic, it means it's not even hardware-3d, simplifying things even further.

So I guess the winehq boards will be my next stop :)

Best regards

LATER EDIT: Ok, it seems Wine **does** work with CoolIris (well, at least as far as version 1.6.2)... I haven't had time to test it yet, but here are the relevant links on winehq.org:
[Details about PicLens here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=11527")

Quote: "Four steps to get piclens working: 1) Install ie6 using ies4linux 2) Install Firefox (inside wine ofc) 3) Install piclens addon for Firefox 4) Using winetricks, install gdiplus Notes: - Without ie6, only grabs the first ~20 images - Crashes when using gecko rather than ie6 - Looks weird without gdiplus"

HTH, good luck!

---

### Post by Bakon Jarser on 2008-09-28
So then this only works for Firefox running in wine?  Too bad.  I'll wait for them to come out with a linux version.  I read somewhere in their FAQ that a linux version is planned but they want to get the windows and mac versions stable before they port.

---

### Post by mihai.ile on 2008-09-30
well yes, but they said that almost a year ago...
I also think that there is no way to dissasemble the extension to make it work, and a way better option would be to create from scratch something similar...

I think that someone could mount a project around this, I would structure it like this:

- core display engine independent from firefox extensions and reusable
- 3d accelerated with support for compiz but should work without it!
- support to plug in various end clients (firefox, nautilus, rhythmbox (covers), f-spot, etc.) - this way we could use it to browse fotos from hdd
- initially create the firefox plugin after core is working

Let's see if we can gather some info and then trying to start a project...
PS: Any other ideas are welcome.

---

### Post by bijeeshvs on 2008-09-30
Great dude, things are coming into shape. So it could be far and far better to start a new project, and lets find someone to do this...................( sorry i dont know to code )

---

### Post by mihai.ile on 2008-10-26
Well they just released a new version but still no Linux support. I started a project in python, but the development will be quite slow as I am learning python myself. I have way more experience in Java but I would like to do it in python.
To begin with I'll try to make it read images from a folder, and after that think about using web services from flickr for example.

I am not sure how this will integrate with Firefox, but for now I am concentrating for a standalone version.

I hope I will have an alpha version in the following weeks...

---

### Post by Bakon Jarser on 2008-10-27
Cool.  I'm just learning python myself.  I've got another project going on right now but maybe I'll have it done by the time you get done with the alpha.  If you put it up on sourceforge and post a link and I will try and help out.

---

### Post by Arabiest on 2008-10-27
thanks...I agree with you...its not the same one used for windows IE.

---

### Post by bijeeshvs on 2008-10-29
hi guys suddenly it got very interesting, and i am waiting for the first release, collaborate and make it faster and amazing than piclens................ 


best of luck..................

---

### Post by mihai.ile on 2008-12-12
I know the thread is old, meanwhile another release of piclens (cooliris now) and still no linux support. Even so it is possible that they do the port before i'm finishing my simple application, as I have very little time available for this.

Anyway I just wanted to say that at least I can create a wall with images from a folder, yet no navigation, nothing.

Here is a Screenshot:

---

### Post by mihai.ile on 2009-03-05
Don't know if anyone is still interested in this plugin but cooliris just released beta for linux and you could support just by downloading and sending feedback to them.
release infos: [http://docs.google.com/Doc?id=dhj9wm6j_4gq4mfmhj](http://docs.google.com/Doc?id=dhj9wm6j_4gq4mfmhj)
download page: [http://www.cooliris.com/beta/?s=linux](http://www.cooliris.com/beta/?s=linux)

---

### Post by aLiEnTxC on 2009-03-05
hey, nice! Thank your for this Information :))

I will test it asap ^^ :popcorn:

---

### Post by mihai.ile on 2009-03-05
Don't forget, you can give the feedback over here: [http://spreadsheets.google.com/viewform?hl=en&formkey=cFlzUHpZZFB3dE1SNjlmZXZvcWswUFE6MA](http://spreadsheets.google.com/viewform?hl=en&formkey=cFlzUHpZZFB3dE1SNjlmZXZvcWswUFE6MA)

---

### Post by Keen101 on 2009-03-08
Looks like someone already beat me to it. oh, well. This Linux version will certainly have to be evaluated asap. Way to go Cooliris people! Thank you for listening to us vocal linux users.

> Fearless Cooliris User,

We're excited to tell you that we've got a Linux beta version
 
of Cooliris for you!

Simply head to [http://www.cooliris.com/beta/?s=linux](http://www.cooliris.com/beta/?s=linux)
 
to download it.

We hope you absolutely love it. And please, give your feedback on this form!

[http://spreadsheets.google.com/viewform?hl=en&formkey=cFlzUHpZZFB3dE1SNjlmZXZvcWswUFE6MA](http://spreadsheets.google.com/viewform?hl=en&formkey=cFlzUHpZZFB3dE1SNjlmZXZvcWswUFE6MA)

Kindest Regards,

Preston & the Cooliris Team


---

