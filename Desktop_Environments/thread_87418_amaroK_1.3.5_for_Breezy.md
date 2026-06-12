---
title: "amaroK 1.3.5 for Breezy"
date: 2005-11-08
forum: Desktop Environments
---

### Post by webhead on 2005-11-08
Hey all,

So I've been researching, and communicating with amaroK developers about why amaroK doesn't work well with iPods.  Well, they tell me that it's because they had originally written their own native iPod linking code, and it's faulty.  The amaroK that is available through Synaptic is unfortunately one of the older builds, 1.3.1, that has this faulty link.  They do tell me now that version 1.3.5 uses libgpod which should fix these errors.

Now I've tried everything to get the blasted thing to work, but when I download the tarball and try the ./configure (in sudo) I get errors of missing dependencies, which is a pain to say the least.  

The long and the short of it, is there anyone who has successfully upgraded to the 1.3.5 version, and that could give me a HOWTO... PLEASE?!

Thanks in advance,

Dan

---

### Post by ossi on 2005-11-08
Hi!

Have a look at the Amarok Wiki. There is a Kubuntu Package which also works fine under Gnome. Uninstall Amarok first and download the two packages. Then go to te directory with the terminal and type:

dpkg -i "amarok_1.3.5 package" "amarok gstreamer package" - that should do the trick. You can find the packages here:

[http://kubuntu.org/announcements/amarok-1.3.5.php]("http://kubuntu.org/announcements/amarok-1.3.5.php")

---

### Post by webhead on 2005-11-08
Well, I'm getting there.

Now, it claims to have successfully transferred the files, but I sure don't see them on the iPod after I disconnect it.  :(  Hmm.  Any ideas?

Along the same lines, is that I'd love it if amaroK out the album art along with the songs, does it do that?  I've been told yes.  Anyone have experience with this?  Also, does it put podcasts IN the podcasts directory on the iPod?

Thanks,

Dan

---

### Post by linbetwin on 2005-11-08
amaroK 1.3.6 released. Says it has some bugs fixed.
 
[http://amarok.kde.org/]("http://amarok.kde.org/")

---

### Post by ossi on 2005-11-08
For transferring songs use gtkpod. They are working on Artsupport currently, but transferring songs should work. I tried mysef a lot to work with Amarok - but somehow I doubt, that its ipod integration is as good as gtkpod - just from my experiences.

---

### Post by webhead on 2005-11-08
Damn, that's too bad.  I really like the interface of amaroK, plus the fact that it can download podcast for me.

So, is there any ONE application that anyone has experience with that can:
-put podcasts IN the podcast dir on an iPod
-download podcasts
-put album art with associated albums
-transfer stuff successfully to an iPod

Thanks!

Dan

---

### Post by webhead on 2005-11-08
Anyone still reading this?

Dan

---

### Post by souled on 2005-11-08
There's a HOWTO that tells you how to install the svn version. It's always updated. Try that.

---

### Post by ltmon on 2005-11-08
Or you could try "klik" to get the latest, bleeding-edge svn 

[http://www.kdedevelopers.org/node/1592](http://www.kdedevelopers.org/node/1592)

L.

---

### Post by webhead on 2005-11-08
Where is this HOWTO?

---

### Post by souled on 2005-11-08
Right here. [http://www.ubuntuforums.org/showthread.php?t=80492](http://www.ubuntuforums.org/showthread.php?t=80492)

---

### Post by Dr. Nick on 2005-11-08
That howto got amarok for me, but I cant test Ipod support since I dont have one. Amarok wont add cover art to each song, It builds a database and puts the art in that. Their is a way to put images in the id3 tag but I forgot how, When I did it you had to do every mp3 seperately which wasnt worth it. Maybe someone knows a better way

---

### Post by webhead on 2005-11-09
Dammit........ so close!  Followed the HOWTO and was nearing the end, when this happened
> 
collect2: ld returned 1 exit status
Error creating ./amarok/src/collectionscanner/amarokcollectionscanner. Exit stat us 1.

ERROR: Compilation wasn't successful. amaroK was NOT installed/upgraded. Ask the  friendly people in #amarok on freenode for help.


I completed every step upto, *sudo ./get-amarok-svn.sh* and it was upon attempting that step, that the above error occured.  Any ideas?

Thanks for all your help so far guys,

Dan

---

### Post by ljamie82 on 2005-11-09
i'm totally trying to spread the awesomeness of synaptic.

why you try to install something from source and it has dependencies that can't be met open up synaptic.  it says you have a broken package.  fix the broken package.  that fixing it's doing is installing those dependencies it couldn't find on the command line in the terminal.  then go to the terminal and install your program.  i don't know why it works, but it always has for me.

---

### Post by webhead on 2005-11-09
I agree.  I totally love Synaptic.  I prefer using it to install apps.  But in order to get the new functionality of some apps that have newer releases available than what are available through Synaptic, such as amaroK, you need to do it the old fashioned way.  Which is a pain, and I hate it, but I can follow instructions pretty well.  Except when there are errors.  :(

Wouldn't it be nice if Synaptic had access to all the bleeding edge stuff too?  Maybe there's a repository that one could add for that, at one's own risk?

Dan

---

### Post by Prolyprole on 2005-11-15
There are breezy debs for the latest (as of the 11th of Nov.) CVS version of gtkpod.

 [http://www.badcow.homelinux.net/](http://www.badcow.homelinux.net/)

I haven't used podcasts yet so I'm not completely sure but I think they are supported in this version. There is also a deb of the latest libgpod. With this I am using amarok 1.4svn with full ipod support. There is a section in the media device tab of amarok for podcasts so I would guess they are supported.

---

### Post by webhead on 2005-11-15
Hmm.........trying the latest gtkpod now.  Successfully DL my Podcasts.  Puts them in correct location on the iPod (a Nano) too.  However, it did put them as well as "Music"; any ideas?  Settings or something?

No artwork yet though?  I thought I had read/heard rumors that the latest gtkpod was going to have it, and did in fact now?

Do you have success with amaroK and artwork?

---

