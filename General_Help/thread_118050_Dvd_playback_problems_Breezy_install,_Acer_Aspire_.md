---
title: "Dvd playback problems: Breezy install, Acer Aspire 5000"
date: 2006-01-16
forum: General Help
---

### Post by kumakun on 2006-01-16
Okay, gang, here's the gig. I followed the Wiki directions for getting dvd playback, no joy. I dredged through the posts, tried everything I could to find a solution to my problem, and now I'm stumped. I have libdvdcss2 installed, totem-xine, on a Breezy install on an acer aspire 5000. I can't think of anything else and need help. The only error I get is "The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?" Which I do. I've uninstalled it and reinstalled it several times. Trying in Mplayer freezes it up. 

So...What next?

Thanks!

/K

---

### Post by kumakun on 2006-01-16
Just a bit of a bump. Any help with this is appreciated. If it's not in the right place, could an Mod move it?

---

### Post by LostBear on 2006-01-16
Hey man...search the forum for summit called "automatix" by arnieboy

got me up and running nicely watching dvds (even commercial ones)

its also neat for a fresh installed system since it takes the pain out of installing or the usual stuff (media players/codecs, bit torrent, java, browsers....stuff...list is long)

u can select what u want to install and it downloads it all and sets it up for u...u dont need to watch it just kick it off and go make a sandwich...

---

### Post by kumakun on 2006-01-17
Thanks for the thought, but that didn't help anymore than doing it myself from the wiki. Same results, same error. Any other thoughts? This is like..my last hurdle to a fully function laptop.

---

### Post by nanotube on 2006-01-17
the following from [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) got dvds working for me:

sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/examples/install-css.sh

apparently it wont work without running that shell script to get de-css... not sure if you have already tried it, but if not, try it.

---

### Post by kumakun on 2006-01-17
Yep, tried that too. Everything easy and some stuff arcane. I followed the wiki, scoured the forums...So far nothing...thanks, though...

---

### Post by johndavidthacker on 2006-01-17
I'm with you, man. I've tried everything on these forums and nothing has worked. I think there needs to be a Sub-Forum devoted exclusively to getting DVDs to play.

---

### Post by Sef on 2006-01-17
There is a newer encryption that there is no hack for on some DVDs.

---

### Post by kumakun on 2006-01-17
Not in this case. The same disk plays on ubuntu 5.10 on my desktop. Anything else?

/K

---

### Post by LostBear on 2006-01-17
OK its morning here now and my brain is working so i will give more advice. I tried for a couple of weeks to get this going, and tried all the stuff out there like you have. I even went to a local linux users group in person and asked them....fat lot of good that did me still didnt get it going.

Then i got fed up and stumbled across automatix. I formated my machine and reinstalled  brezzy, then set up my internet then installed automatix and loaded the dvd stuff in through that. then i had fully functioning dvd playing...strange.

Im guessing that by fiddling around we both messed up stuff. Automatix works fine on a fresh install, so if your up for it thats what u should do.

If u manage to find a disk that wont work (like one with the new encyption) try using DVD shrink to dump the disk to ur hard disk (assuming u have access to windows still or wine might work out for you or some soft like win4lin or vmware for linux). You will end up with an ISO file on your hard disk that u can mount and play..

---

### Post by kumakun on 2006-01-17
Okay, that's cool and all, but I'd really rather not reformat this thing and have at again. I've finally got wireless working on it and that's not something I'm inclined to mess with. I'm not trying to be difficult, I appreciate the suggestion, but I'm not that desperate yet. 

Also, I dunno if this helps, but every time I run totem from the command line and it starts accessing libreaddvd, it seems as though everything goes well in the prompt. it accesses libreaddvd and libdvdcss, but for whatever reason it kicks back an encryption error.

/K

---

### Post by LostBear on 2006-01-17
In that case i really dont know what else to suggest except this work around..

SLAX Popcorn Edition v 5.0.6 

Its a gorgeous tiny live distro (104mb takes 8 mins on 1mb dsl line) that will boot from a cd or a pen drive and its preconfigured to play dvds..and it wont damage ur breezy in any way. A quick look in the forums for it suggests it is possible to install this to ur hard drive so as a very last resort u could dual boot breezy and slax popcorn. Not very tidy i know but it will work.
 
[http://slax.linux-live.org/download.php](http://slax.linux-live.org/download.php)

As an as an aside..i installed the liddvdcss manually and totem claimed it was NOT installed. So i went back and tried to reinstall and this failed since it claimed it was already installed. go figure.

---

### Post by kumakun on 2006-01-17
So I stripped down the media players, codecs and libraries and reinstalled them and still nothing. I can get menus for most DVDs, but whenever it tries to actually play the content it gives me back the error: "Cannot play encrypted DVD, are you trying to play an encrypted dvd without libdvdcss?" Which I'm obvoiusly not, since I have it installed...

Anything else? 

/K

---

### Post by qferret on 2006-01-17
/me grasps at a straw

Has the DVD drive ever been used under Windows? If not, the region may not be set. (I ran into this with mine). If this is the case, it won't play a regioned DVD, as it doesn't know whether it's "kosher" or not.

Get Regionset and run it without any params. It will print out the players settings.

If the region slot is blank, set it to your region and try again.

---

### Post by kumakun on 2006-01-17
Well, the region wasn't set, but that didn't help anything. I know we're getting down to the nitty gritty....Anything, ANYTHING else? 

Thanks
/K

---

### Post by Sparkalo on 2006-01-17
Well, seeing as the software is set up nicely, how about checking out your hardware?  

Do you have access to an external DVD drive or a friend with a notebook dvd drive you could borrow?&#12288;

I honestly don't know where this is going, but it makes sense to confirm it isn't the actual dvd drive somehow I guess.

Good luck!

---

### Post by qferret on 2006-01-17
Run Totem from a command line and post any errors that show up in the terminal window when the DVD fails.....

---

### Post by kumakun on 2006-01-18
Hm...This gets curiouser and curiouser. I found a single disk so far that actually works with no hitch. The only difference I see is that it reports back as regions 1 2 3 4 5 6 7 8. All the other only report as region 1. The only error I see in the at all is:
```
libdvdnav: Unable to find map file '/home/justin/.dvdnav/<mymovie>.map'

```

And it shows that for the other one, too. replace my movie with any given title. It shows up on all of them.

I did run region set...

EDIT: Actually, every time I go to run region set the Current Region Code setting is blank. Should that be saving a value of some sort?

EDIT2: after digging a little deeper, this appears to be affecting some titles, but not all titles. Some of those titles unaffected are region 1..in fact most of them are. Here's the kicker. the titles that ARE affected on the drive in my laptop (which is a DVDRW) Are NOT affected in my desktop (which is a cdrw/dvdrom.) Go fig. Any thoughts?

---

### Post by qferret on 2006-01-18
[QUOTE=kumakun] I found a single disk so far that actually works with no hitch. The only difference I see is that it reports back as regions 1 2 3 4 5 6 7 8. 

EDIT: Actually, every time I go to run region set the Current Region Code setting is blank. Should that be saving a value of some sort?[/QUOTE]

Jackpot!

The one that works is regionfree.....

The region setting isn't taking for some reason...


Shamelessly ripped info to follow
---------------------------------------------------
On delivery, most DVD drives have no region code set. The drive firmware allows you to change the region code, but on nearly all drives you are limited to five (5) changes. After the fifth change, the DVD drive will stay fixed on that code -- on some drives you can upgrade the drive firmware and have then additional five changes, on other drives you won't be able to change the region code any more.

There are a couple of region code free DVDs on the market, but some drives will deny playing them without setting a region code for the drive first. After setting the region code, the drive will refuse playing any Video DVD (perhaps also Audio DVDs, I never had one to try out) with a different region code than its own.

If you set a DVD drive to region code 2 (RC2), you'll only be able to play region-code-2-DVDs from Europe, Middle East, South Africa and Japan -- the drive will definitively not play any US or Canadian DVD, nor Austrailian or Chinese. So if you cannot play a DVD because of the wrong region code, there is nothing the DVD player software can do about but changing the region code of the drive if you have any changes left.

So always be very very careful changing the region code, it could be your last try before you're forced to buy a new drive (or play foreign DVDs forever).
Installation

Just unpack the package then call "make". After compiling, you'll find the binary "regionset" in the directory which you should copy to /usr/sbin (as root, of course)
How to use the programm

You need write access to the DVD drive, either by group or by being root. The more, there absolutely definitively and in any case *must* be a readable Data CD or Data/Video DVD in the drive -- it does not matter if it's your favourite Windows CD, a video or a DVD with your last backup.

By default, regionset will use /dev/dvd to find your DVD drive. You can adjust this by entering the path to the DVD device as first command line parameter (please absolute path!).

If everything goes well, regionset will show you the current region code of the drive, how often it has been changed and how many changes are left. If there are any changes left, it asks for the new region code (see table above). After confirmation, the new region code will be set -- if you enter the same region code as the current one of the drive or just break the programm, regionset will just exit without setting the new code. On successful change of the region code, you'll get a confirmation.

---

### Post by qferret on 2006-01-18
[QUOTE=kumakun]Some of those titles unaffected are region 1..in fact most of them are. [/QUOTE]

You're in NA ..... they should ALL be region 1 (or region free)

Are we trying originals, copies or a mixture?

If a mixture, let's stick with originals until we get the process sorted. ;)

---

### Post by kumakun on 2006-01-18
[QUOTE=qferret]You're in NA ..... they should ALL be region 1 (or region free)

Are we trying originals, copies or a mixture?

If a mixture, let's stick with originals until we get the process sorted. ;)[/QUOTE]

The one copy I tried played fine, the rest were originals, some played well some didn't. I ran regionset as root, as in I did a sudo bash and then:
```
root@omoikane:~# regionset

```

The output tells me that it was set successfully, but when I run regionset again,  it's still without a code.

That's where I'm at now...some of my dvd's play (all except 1 are region 1) and others don't. There doesn't seem to be a common thread. Am I doing something wrong with region set? This is the exact output and path I follow when I run it.
```

root@omoikane:~# regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 1, mask=0xFE

Would you like to change the region setting of your drive? [y/n]:y
Enter the new region number for your drive [1..8]:1
New mask: 0xFFFFFFFE, correct? [y/n]:y
Region code set successfully!

```

So. What next?

---

### Post by LostBear on 2006-01-18
is it Possible that there is something inside libcss and libdvdread that stops it playing a region 1 dvd in america...there is a warning about this in automatix saying its illegal within the united states to play commercial titles, but i cant remember the exact conditions. I live in england so i wasnt paying attention.

Have u tried setting the drives region to 0 (meaning it will play any region)?

the drive in your desktop plays all your discs fine in breezy but id excpect the one in your laptop to be more compatable since its a dvdrw. If it was me id be inclined to buy and external encloser and try ur desktop dvd drive on the laptop, or borrow one if u can. then ud know the prob is the drive rather then the software.

---

### Post by LostBear on 2006-01-18
Just had another thought..

If u were to download slax popcorn and boot ur laptop off it and play dvd and it works...then the problem is defiantly the software rather then ur drive.

---

### Post by kumakun on 2006-01-18
I did try setting the drive to use all regions, but there's no real option for that.

---

### Post by kumakun on 2006-01-19
Just a brief thank you to those that have helped so far. The problem still isn't solved completely, I can play some DVDs, but not others. So far there doesn't seem to be a common thread between those that play and those that don't. Any help is still welcome.

Thanks!
/K

---

### Post by LostBear on 2006-01-19
No probs man. not sure i helped really.

---

### Post by qferret on 2006-01-26
Sorry....was out & about for awhile  ;-)


The regionset info you posted looks good...no clue why it doesn't stick.

This has to be at least part of the problem... 

I don't believe I had to run regionset with root access.
Since you did run it with root access, I'm just curious...do the DVD's play if you run the player as root? (grasping at straws here wondering if regionset throws something in the home directory, which would be root's home directory w/ the method you ran the proggy.

---

### Post by LostBear on 2006-01-31
Hi...someone from my local linux group has just mailed me witha possible soloution for me, but i thought id pass it on ...u never no it may be of help to you..

this is just direct cut from the mail he sent me..

> The first was DVD/CSS decoding under Ubuntu,



At least on Ubuntu 5.10 (Breezy) the information on this can be found in


the file:



 /usr/share/doc/libdvdread3/README.Debian



but basically what you need to do is run this script while connected to


the the Internet:



 /usr/share/doc/libdvdread3/examples/install-css.sh

youve probs done this already but wtf

Lostbear

---

### Post by hamil on 2006-02-01
Bumping this thread, since I do have the same trouble, and not finding any solutions..

---

### Post by Laxflip on 2006-02-08
uber bump i searched and dredge and nothign i cant play JACK

---

