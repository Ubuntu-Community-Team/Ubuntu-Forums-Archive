---
title: "[SOLVED] FluxBox - the toolbar icons are strange !"
date: 2008-03-12
forum: Desktop Environments
---

### Post by LinuX-M@n1@k on 2008-03-12
Look at the [screenshot...]("http://i.data.bg/08/03/12/851404_orig.jpg") I don't know how to explain it. lol
How do I fix that ? :confused:

---

### Post by kerry_s on 2008-03-12
dang, that screen shot took forever to load, you should have just used the forums attachments, but the girl was entertaining :) 

have no idea on the problem, it looks like the background transparency is screwed up.

---

### Post by LinuX-M@n1@k on 2008-03-12
the image is too big to upload it here - 2.3MB
i'll upload it somewhere else

---

### Post by markjensen on 2008-03-12
I can't view your image.  Is it anything like what I posted about here: [http://ubuntuforums.org/showthread.php?t=721886](http://ubuntuforums.org/showthread.php?t=721886)

The icon images are getting almost random-looking pixels scattered in there, sometimes enough to hardly tell what icon it is supposed to be.

---

### Post by LinuX-M@n1@k on 2008-03-12
yes ! thats exactly how my icons look like

---

### Post by markjensen on 2008-03-12
I am not sure what is causing that.   It did it from my very first run of Fluxbox on *buntu, and I had been using flux under Fedora for many years without seeing this.

It happens with the "nvidia" driver, and with the "nv" one.  I haven't tried plain "vesa" yet, but I don't expect that to make a difference.  Maybe you can give that a try real quick (I am at work on lunch and don't have access to my Linux box until I get home this evening).

I also tried installing openbox (**sudo apt-get install openbox**) but my openbox session, for whatever reason, doesn't have a taskbar.   It was a mystery I did not dwell on this morning, since I had to head to work.

Ahhh.. work.   Interfering with my life. :P

---

### Post by RedSquirrel on 2008-03-12
> **markjensen said:**
> I am not sure what is causing that.   It did it from my very first run of Fluxbox on *buntu, and I had been using flux under Fedora for many years without seeing this.

It happens with the "nvidia" driver, and with the "nv" one.  I haven't tried plain "vesa" yet, but I don't expect that to make a difference.  Maybe you can give that a try real quick (I am at work on lunch and don't have access to my Linux box until I get home this evening).

I also tried installing openbox (**sudo apt-get install openbox**) but my openbox session, for whatever reason, doesn't have a taskbar.   It was a mystery I did not dwell on this morning, since I had to head to work.

Ahhh.. work.   Interfering with my life. :P

I would recommend compiling your own fluxbox. I recall that I had the same issue with the fluxbox from the gutsy repositories, but it was not present when I compiled my own (for example, from the stable source tarball). 

In the menu tutorial link in my signature, there are instructions for compiling fluxbox.

Openbox doesn't come with a taskbar/panel. You have to add one (I use fbpanel).

---

### Post by markjensen on 2008-03-12
Oh god....  I really don't want to start the "compile your own" thing.

I mean, I like Open Source, but as a practical person, I just like to run my darn computer, and not work for it to get it to run.

I will live with the crappy rendering of icons until whomever is maintaining the Ubuntu repos gets this fixed. :(

The attached is barely recognizable as the Yahoo symbol due to the funky black with multi-color pixels.   But I will tolerate this problem.

---

### Post by spupy on 2008-03-12
Right click on the desktop and go to the submenu with the configuration options. Check the option "Image Dithering". I have no idea what it means, just a wild guess (but it does have to do something with images)!

---

### Post by RedSquirrel on 2008-03-12
> **markjensen said:**
> Oh god....  I really don't want to start the "compile your own" thing.

I mean, I like Open Source, but as a practical person, I just like to run my darn computer, and not work for it to get it to run.

I hear ya.

Besides, Hardy will be out next month and maybe the fluxbox package will be better next time. 

If you ever change your mind about tolerating the issue, I will tell you that compiling fluxbox isn't that hard and it's a fairly small package (only takes a few minutes to build). Just FYI. ;)



> **markjensen said:**
> I will live with the crappy rendering of icons until whomever is maintaining the Ubuntu repos gets this fixed. :(

Somehow, when I read that the first time I thought you wrote "until whomever is maintaining the Ubuntu repos gets _fired_". :twisted:

It's been a long day... maybe I should watch a movie tonight. :lol:

---

### Post by LinuX-M@n1@k on 2008-03-12
> **spupy said:**
> Right click on the desktop and go to the submenu with the configuration options. Check the option "Image Dithering". I have no idea what it means, just a wild guess (but it does have to do something with images)!

not working :/ btw, it was already checked... i unchecked it and checked it again... nope
maybe i'll compile it myself, but i dunno

---

### Post by markjensen on 2008-03-12
Hmmm...  Since it's been since about 2002 since I had ever compiled anything, I thought I would give it a try.   The build-dep step ended up asking for the CD an awful lot, but let me skip it - up to the end.   I didn't have the CD handy, and didn't think it necessary with the big wide internet out there available to grab whatever it needed.

It didn't work, but now I have compiling in the back of my head as an option...  Probably will mean that it will eventually bother me enough to give it a try.

Also, can't someone take the correctly (perhaps "more commonly desired" is a better term) compiled version of fluxbox and feed it back up to the Ubuntu dev team for approval/inclusion in the repos? :confused:

---

### Post by LinuX-M@n1@k on 2008-03-12
you can just disable the pictures if you want..
right click on the toolbar > iconbar mode > show pictures

---

### Post by RedSquirrel on 2008-03-12
> **markjensen said:**
> Hmmm...  Since it's been since about 2002 since I had ever compiled anything, I thought I would give it a try.   The build-dep step ended up asking for the CD an awful lot, but let me skip it - up to the end.   I didn't have the CD handy, and didn't think it necessary with the big wide internet out there available to grab whatever it needed.

It didn't work, but now I have compiling in the back of my head as an option...  Probably will mean that it will eventually bother me enough to give it a try.

If you're being asked for the CD, your /etc/apt/sources.lst file likely still has the CD as a source. You can comment that (put a '#' in front of the line with cdrom in it).



> **markjensen said:**
>  Also, can't someone take the correctly (perhaps "more commonly desired" is a better term) compiled version of fluxbox and feed it back up to the Ubuntu dev team for approval/inclusion in the repos? :confused:

I don't think it works like that. You can report a bug and then it is up to the devs to handle it. I have a strong feeling that the source of the icon problem is that the XShape extension support was left out of gutsy's fluxbox package. That by itself has already been reported and confirmed as a bug. I supposed you could report a bug mentioning the icon issues in the toolbar and see what happens. :neutral:

---

### Post by markjensen on 2008-03-12
> **RedSquirrel said:**
> If you're being asked for the CD, your /etc/apt/sources.lst file likely still has the CD as a source. You can comment that (put a '#' in front of the line with cdrom in it).
That was it.

It wasn't painful to cut and paste the commands you have to compile, and it did the trick wonderfully!   Nice clean icons and I even have rounded corners back, too.  Thanks!

---

### Post by markjensen on 2008-03-13
Quick question, directed primarily toward RedSquirrel, but it is a general question that can be answered by anyone knowledgeable in this area...

Can we (or someone with familiarity in this area) not set up a [Ubuntu Personal Package Archive](https://launchpad.net/ubuntu/+ppas) to create a repository for this fluxbox correction, since the Gutsy have not done so?

If I understand this right, it is space that can be added to the apt sources.list file and anyone (in this case flusbox users) can update from that instead of the official standard repos to get the corrected version.   Then the "maintainer" of this PPA repo would just need to keep up with the fluxbox page and just recompile any new releases and put it into the PPA.

Am I thinking of this correctly?

---

### Post by LinuX-M@n1@k on 2008-03-13
cool :D i compiled it from source and now it works like a charm, except for the skype icon. it's still awful, but who cares! :lolflag:
THANKS !

---

### Post by RedSquirrel on 2008-03-14
I'm glad you both have a nice-looking toolbar now. :)


> **markjensen said:**
> Quick question, directed primarily toward RedSquirrel, but it is a general question that can be answered by anyone knowledgeable in this area...

Can we (or someone with familiarity in this area) not set up a [Ubuntu Personal Package Archive]("https://launchpad.net/ubuntu/+ppas") to create a repository for this fluxbox correction, since the Gutsy have not done so?

If I understand this right, it is space that can be added to the apt sources.list file and anyone (in this case flusbox users) can update from that instead of the official standard repos to get the corrected version.   Then the "maintainer" of this PPA repo would just need to keep up with the fluxbox page and just recompile any new releases and put it into the PPA.

Am I thinking of this correctly?

Yes, I think so. I cannot personally take this on at this juncture, but it's an interesting idea. My only other comment is that Hardy will be out fairly soon. It is to be hoped that the fluxbox package in Hardy will be in better shape. ;)

---

### Post by ptero on 2008-03-26
am i the only one who doesn't manage to compile it? :confused: ;)
i "guess", fluxbuntu-devs didn't include all the necessary stuff to compile things.
i'll attach the config.log...

ps. why, for gods' sake can't one attach .log files? :///

---

### Post by markjensen on 2008-03-26
I just followed the steps in RedSquirrel's thread, and it worked fine for me.   

To make it easy, I can upload the .deb file and post a link to it when I get back home this afternoon.   That way you don't have to compile.

---

### Post by ptero on 2008-03-26
> **markjensen said:**
> I just followed the steps in RedSquirrel's thread, and it worked fine for me.   

To make it easy, I can upload the .deb file and post a link to it when I get back home this afternoon.   That way you don't have to compile.

yeah, it would be nice.
however, i still want to be able to compile stuff. i had the same problem wuth wicd (but found a .deb later).

do you also have fluxbuntu, too or did you just install fluxbox on "normal" ubuntu? fluxbuntu seems to have some problems, which "normal" ubuntu doesn't have...

---

### Post by markjensen on 2008-03-26
I used xubuntu as a start, since I had it already lying around.   I installed flux onto that.   I have a kid account set (reduced priveleges so the kids can use my computer without affecting my settings) that they "switch user" into, but they use XFCE with some desktop icons I set for them, and a more "windows like" start area to select other apps/tasks.

---

### Post by ptero on 2008-03-26
well, i thought, it would be better to create a new thread, for it isn't really a fluxbox problem.
[http://ubuntuforums.org/showthread.php?p=4590523#post4590523](http://ubuntuforums.org/showthread.php?p=4590523#post4590523)

---

### Post by ptero on 2008-03-26
well, i built it from source, noticed that it doesn't know when to look in /usr/share (well, actually, it should never look there, should it?) and when in /usr/local/share) for styles etc... set everything up...
and guess what - the icons stayed the same way! even worse, it refused to show stuff in toolbar and window title in my language (yes, i configured it with --enable-nls).

---

### Post by markjensen on 2008-03-26
Dang.  I just got home and uploaded the .deb file to googlepages.
[http://neowin.files.googlepages.com/fluxbox_1.0.999-1_i386.deb](http://neowin.files.googlepages.com/fluxbox_1.0.999-1_i386.deb) <-- if you still want to try it (and you think I am a "trusted" source)

For the icons, can you post a little tiny screenshot of the icon example?

And did you log out and back in to restart your session?

---

### Post by ptero on 2008-03-26
thanks for your .deb! the icons look fine now and i've got no problems with cyrillics in toolbar.

as for the icons: [here]("http://ubuntuforums.org/showthread.php?t=734835") is my thread on that topic, i attached a screenshot there.

---

### Post by markjensen on 2008-03-26
Hey, glad it worked for you.

I just followed the same steps from the link in RedSquirrel's sig.  Not sure why it gave you such problems, but at least you have a working fluxbox.

I hope that Hardy has this little issue resolved.

---

### Post by ptero on 2008-04-23
> **markjensen said:**
> Hey, glad it worked for you.

I just followed the same steps from the link in RedSquirrel's sig.  Not sure why it gave you such problems, but at least you have a working fluxbox.

I hope that Hardy has this little issue resolved.

hmmh, that's strange.
while your package absolutely worked on my laptop, it doesn't on my pc (i recently changed from gentoo ;) ).
well, i'll try to rebuild it here myself again...

EDIT: oops, my bad. i forgot to change ~/.fluxbox/startup

---

