---
title: "MP3 failure (after dapper upgrade)"
date: 2006-06-10
forum: Desktop Environments
---

### Post by brianj774 on 2006-06-10
Hi all,

Under Breezy, I had mp3 files working just fine.

After I upgraded to Dapper, I've noticed that although my sound system as a whole seems to work just fine, I am unable to play mp3 files again.

I tried EasyUbuntu and Automatix both, using them to install mp3 support, and they appear to have completed successfully, but I still get nothing.

When I run an mp3 file with Amarok nothing happens, no error message, nothing.

How can I debug this further, and get mp3's to play once again?

Thanks,

Brian

---

### Post by aysiu on 2006-06-10
Maybe try this? ```
sudo aptitude update
sudo aptitude install libxine-extracodecs gstreamer0.10-plugins-ugly
```

---

### Post by TOPPEL on 2006-06-10
actually i suffered the same problem with him when i was using Muine.  i solved it with some gstreamer8 revision plugins and a fluendo_mp3 gstreamer plugin.  something else i did but i can't remember.  i hate doing it but i installed as many gstreamer8's i could just to get Muine working.  i dont think i broke anything :)

forgive my lack of knowing what things are called.  my medication wiped my brain.

---

### Post by brianj774 on 2006-06-11
no luck there.  I already have all the gstreamer and xine items installed.

Before, when I was trying to get everything working with Breezy, I had found that the gstreamer apps wouldn't play, but xine based ones would.  I guess I'll try uninstalling all the gstreamer stuff, leaving only the xine engine.  see how that works.

---

### Post by brianj774 on 2006-06-11
Okay, its fixed, sort of...

I uninstalled all gstreamer* and *xine* related items.

Now mp3's play in xmms...

So, I want amarok, I guess I'll just try installing the basic Amarok package, and hope everything just works....

*lost*

Brian

---

### Post by brianj774 on 2006-06-11
```
brianj@tinas-ubuntu:~$ sudo apt-get install amarok
Reading package lists... Done
Building dependency tree... Done
Package amarok is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package amarok has no installation candidate
```

so much for that idea....

Any others?

Thanks,

Brian

---

### Post by tronica on 2006-06-11
try adding this repo

[http://kubuntu.org/announcements/amarok-1.4.php](http://kubuntu.org/announcements/amarok-1.4.php)

or add this to your sources.list for the stable release

deb [http://people.debian.org/~adeodato/packages](http://people.debian.org/~adeodato/packages) amarok-sarge/

---

### Post by TOPPEL on 2006-06-11
You could try:

sudo apt-get install gstreamer0.10-plugins-*

It'll install every gstreamer plugin package. If that doesn't work, then the Muine doesn't use gstreamer for audio playback.

btw i did the same for the 8* plugins which also installed all of them and it failed to work as well.  i was told Muine uses gstreamer rev 8.

---

### Post by brianj774 on 2006-06-11
[QUOTE=tronica]try adding this repo

[http://kubuntu.org/announcements/amarok-1.4.php](http://kubuntu.org/announcements/amarok-1.4.php)

[/QUOTE]

I tried that, and amarok 1.4 installs nicely.  However, the first time I ran an mp3 with it, some error notices flashed by quicker than I could notice.  All I saw was that there were 2 of them, and one said something about 'arts'.

I then tried to install 'amarok-arts' but its for 1.3.9, and Adept won't commit it.  Apt get says:```
brianj@tinas-ubuntu:~$ sudo apt-get install amarok-arts
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  amarok-arts: Depends: amarok (= 2:1.3.9-0ubuntu4) but 2:1.4.0a-0ubuntu1 is to be installed
E: Broken packages
```

So, how do I find the 1.4.0 amarok-arts?  I'll investigate.

Brian

---

### Post by shelbydz on 2006-06-13
the arts engine is only for Kubuntu. Is that what you're using? If so, it should be installed automatically.

---

### Post by brianj774 on 2006-06-19
[QUOTE=shelbydz]the arts engine is only for Kubuntu. Is that what you're using? If so, it should be installed automatically.[/QUOTE]

Yeah, this is all Kubuntu.

The problem is that Adept only carries 1.3.9 arts files, but according to the suggestion of someone, I am getting adept from some other source.  But I can't locate anything anywhere on how to get the 1.4.0 arts deb in my sources.list ....

It must be simple, or there'd be other posts about it...

I just can't find anything on it.

Thanks,

Brian

---

### Post by jackow on 2006-06-20
Hi Brian,

I'm using amarok 1.4 on dapper and too had this problem.

[QUOTE=brianj774]Yeah, this is all Kubuntu.

The problem is that Adept only carries 1.3.9 arts files, but according to the suggestion of someone, I am getting adept from some other source.  But I can't locate anything anywhere on how to get the 1.4.0 arts deb in my sources.list ....

It must be simple, or there'd be other posts about it...

I just can't find anything on it.

Thanks,

Brian[/QUOTE]

But somewhere on the homepage of amarok stood that amarok 1.4 does not support arts anymore because of its lacks of stability. The main engine is now xine. You can simply switch in the configuration menu to xine allthough you're using arts for other applications.:D 

Two days ago my xine-engine allready played mp3-files. But after the last update of my kubuntu 6.06 it didn't work anymore and there was the message:

"xine-engine can't play MP3 files ..."

libxine-extracodecs is installed, but there is no MP3 demuxer anymore.
What happened? :confused:

Thanx for all replies!
jackow

---

### Post by N8K99 on 2006-06-21
Yes, I too am having this problem on my ppc running kubuntu. Two days ago, amarok was playing mp3s and then on an update, no longer.

---

### Post by brianj774 on 2006-06-21
Thats the same thing that just happened to me in the last few days....

---

### Post by jackow on 2006-06-23
Ok, after some tries I finaly did it:

You should have libxine-main1 and libxine-extracodecs installed.

Install gxine and gxine-plugin.
Remove your ~/.xine directory
Start gxine to reconfigure the xine-engine.

I did many other things, but the last steps let my amarok play mp3s again.

good luck,
jackow

---

### Post by No_sanctuary on 2006-06-23
hey thanks jack that worked for me.  It's strange that you'd need to install gxine but hey if it works. I wonder what the real problem is...

---

### Post by N8K99 on 2006-06-24
I was able to install libxine-extracodecs from a page in the Ubuntu wiki.

[INDENT][http://packages.ubuntu.com/dapper/libs/libxine-extracodecs](http://packages.ubuntu.com/dapper/libs/libxine-extracodecs)[/INDENT]

You can right click on the link in kubuntu and use the Actions menu to download with Kget, and then right clicking again you can install it. 

I also found out that if you turn off the sound in the System Settings menu, you no longer get that annoying clicking/skipping noise when you play music with amarok.:cool:

---

### Post by pstep9407 on 2006-10-06
thanks guys. I fixed mine with :
 ```
sudo apt-get install gstreamer0.10-fluendo-mp3
```

---

