---
title: "[Discuss] Ipod Management"
date: 2006-05-24
forum: Desktop Environments
---

### Post by jhorner on 2006-05-24
What does everyone use to manage their iPod in Dapper?  I tried Rythmbox and aMarok, really lik aMarok but its just been sketchy recently.  So I am looking for suggestions.

---

### Post by ketsugi on 2006-05-24
I'm just using gtkpod until I buy a sexy new MacBook :)

---

### Post by jhorner on 2006-05-24
I tried that using Breezy and had some issues with mounting / unmounting...  Maybe I will give it another try.

---

### Post by PsyberOneZero on 2006-05-24
Right now I use banshee to manage my iPod, the only problem is banshee cant read/open (C# bug) almost 2000 of my songs. It's better than nothing but I'm waiting until rhythmbox beef's its iPod support or banshee fixes the read errors.

As for gtkpod, I've had nothing but problems. You have to load the library everytime (which takes a LONG time) then try and figure out which combination of buttons to press to transfer. It's also just layed out poorly IMHO.

---

### Post by soze on 2006-05-24
[QUOTE=jhorner]What does everyone use to manage their iPod in Dapper?  I tried Rythmbox and aMarok, really lik aMarok but its just been sketchy recently.  So I am looking for suggestions.[/QUOTE]

I've been using Banshee. It works well but there are two missing feature:
1. Playlists (Banshee has playlists, but they don't propagate to the ipod)
2. Podcast support (I've been using Ipodder as a podcatcher and then importing the files into Banshee. I'd just as soon skip this step).

Other than that, it pretty much does the job.

---

### Post by jdusablon on 2006-05-24
Not to mention...

Do ANY of these support Album art to *correctly* display it on the iPod itself? I've tried Banshee, Listen, gtkpod, amarok, etc.

**NONE** of these have iPod album art support.

At least gtkpod is relatively predictable in behavior, but its UI is awful and the program is half-broken.

---

### Post by jhorner on 2006-05-24
maybe one day apple will answer our cry and port itunes.  does anyone know if this works in wine or cross over office?  I tried it in vmware, but couldnt get the ipod recognized.

---

### Post by malte on 2006-05-24
You can try GPixPod for album art support
[http://www.gpixpod.org/wordpress/](http://www.gpixpod.org/wordpress/)
[http://www.gnomefiles.org/app.php?soft_id=1262](http://www.gnomefiles.org/app.php?soft_id=1262)
[http://sourceforge.net/project/showfiles.php?group_id=157492&release_id=391207](http://sourceforge.net/project/showfiles.php?group_id=157492&release_id=391207)

---

### Post by chronusdark on 2006-05-24
amarok is an excellent ipod managment program except for the fact that they removed ipod video support (i.e. wont transfer m4v files) and the only thing people tell me is to buy the developers an ipod and they will get it working....not very professional in my opinion but if your looking for just music management amarok is the best plus it will search for your album art automatically

---

### Post by jhorner on 2006-05-24
my only beef with amarok is that recentley it says that it has transferred my music to the ipod, but then I go and try to listen and it either didn't transfer or in one instance it only transferred 4 of the 12 songs...  and yes, there was plenty of free space.  I think that it is probably the best music prog for linux (and I use gnome) , but I just wish I could find something that played well with the nano.

---

### Post by joncheyne on 2006-05-24
[QUOTE=jhorner]What does everyone use to manage their iPod in Dapper?  I tried Rythmbox and aMarok, really lik aMarok but its just been sketchy recently.  So I am looking for suggestions.[/QUOTE]

GTKpod works for me - load from ipod, remove songs, add new from folder, sync, done.

It take a while to sync but that's my only complaint.

---

### Post by dentaku65 on 2006-05-24
give a try to YamiPod
[www.yamipod.com](www.yamipod.com)

;)

---

### Post by jhorner on 2006-05-24
[QUOTE=dentaku65]give a try to YamiPod
[www.yamipod.com](www.yamipod.com)

;)[/QUOTE]

tried it in breezy and had little luck with the program.  I will give it another go around with the dapper though.  thanks for the suggestion.

---

### Post by denjin on 2006-05-24
Banshee seems pretty nice!  How do you get it to play aac files though?  I have a few CDs I ripped to aac and it can't play them.  I do have the gstreamer bad multiverse package installed along with everything that came up with aac in synaptic...

---

### Post by chronusdark on 2006-05-24
[QUOTE=jhorner]my only beef with amarok is that recentley it says that it has transferred my music to the ipod, but then I go and try to listen and it either didn't transfer or in one instance it only transferred 4 of the 12 songs...  and yes, there was plenty of free space.  I think that it is probably the best music prog for linux (and I use gnome) , but I just wish I could find something that played well with the nano.[/QUOTE]

have you been using the 1.4 release they have vastly improved ipod support also weird characters in the filename would cause amarok to not transfer the files

---

### Post by Piggah on 2006-05-24
I've been using amarok lately, and it's been the only thing I've had success with lately. I could never get gtkpod working, but amarok worked the first time and I've had no trouble with it really. 

I would like the video support however, since I'm going to be purchasing a video iPod very soon. Shuffle is getting boring. (Even though it makes life so random) :P 

I havn't tried yamipod, but I will soon enough.

---

### Post by jhorner on 2006-05-24
[QUOTE=chronusdark]have you been using the 1.4 release they have vastly improved ipod support also weird characters in the filename would cause amarok to not transfer the files[/QUOTE]

that is a good question.  It may be a 1.3 version.  I think when I installed it, I used apt-get and still had breezy repo's so it is possible that I have an older version.  I will check this out ASAP.  also, does anyone think that the issue could be that I am using it in Gnome, considering its a KDE app and all.  again, thanks for the suggestions.

---

### Post by veratyr on 2006-05-24
gtkpod...still waiting for it to sync artwork in id3tags :-?.

---

### Post by jdusablon on 2006-05-25
> gtkpod...still waiting for it to sync artwork in id3tags
Yes, exactly.

**Malte**, GPixPod is nice and all, but it doesn't support album (cover) art embedded in idv3 tags. It only does photos and photo albums.

---

### Post by kalbir on 2006-05-26
I started off using Gtkpod but my laptop is quite old and I occasionaly had some problems (only 32Mb RAM) so I switched to KDE and used amarok (1.4). The first time that I did so I somehow managed to delete 80% of the songs on my Ipod:confused: ! I went from 1000 to 200. Luckily they were just songs that I owned the albums for already but it is a hassle reloading all that music! ](*,)

---

### Post by mlind on 2006-05-26
I use Rhythmbox to play songs from my iPod.

I tried amaroK few moths back, but I turned out to be evil and corrupted my ipod's
song database somehow. I had 900 songs in it, and suddenly there were 255..
I got db back without too much hassle by opening iTunes once, which seemed  to
fix the database and all songs were visible again.

amaroK also wrote its own metadata for songs that had no album or artist defined,
there were alot of songs from_no_artist_ and my Ipod name had chaged to amaroK.
After that incident I ditched the player.

gtkIpod seems to do the job for me.

---

### Post by CuCullin on 2006-05-26
amaroK for me...

And if you want the best support, get something other than an iPod, one that uses more standards oriented connections - like as a usb mass storage device, a la Cowon X5, A2, etc.

---

### Post by Bazon on 2006-05-26
So far I tried gtktPod, amaroK and banshee.

I prefer gtkPod.
If only it would be a bit faster displaying tracks!
I disabled displaying tracks at start according to the [readme](http://www.gtkpod.org/README) and now it's alright...:
> - Display of large number of tracks is awfully slow (mainly because of
  the use of the standard GTK2 tree views) -> deactivate "Automatically
  select "All" in first filter tab" and/or deactivate "Automatically
  select master playlist". You could also "block the display" to speed
  up the display update. Further, decreasing the window size
  considerably speeds up the display.

  I also want to point out that updating the info window takes up a
  considerable amount of time. Update may become more intelligent in
  the future -- until then close the info window for more speed.

However, gtkPod has the best features (including working album artwork...!) and best usability.

I struggled a bit in AmaroK to add an folder to my iPod. As I manged it, it also deleted 80% - 90% of my DB :x (As reported by some others before...)

Forunately, I was able to rebuild my DB with gtkPod, but anyway, my playlists were gone thanks to amaroK...

In Banshee, I didn't understand how to add things to the iPod at all.....




What I'd like to have, would be a iPod manager
[list][*]which is fast (unlike gtkPod)
[*]has a good "add folder" option (like gtkPod)
[*]Doesn't depend on a Database of my local tracks. (I don't like DBs. Too slow for me.)
[*]maybe supports tagging.[/list]

Any Tips? :)

---

### Post by almostlinux on 2006-05-26
[QUOTE=malte]You can try GPixPod for album art support
[http://www.gpixpod.org/wordpress/](http://www.gpixpod.org/wordpress/)
[http://www.gnomefiles.org/app.php?soft_id=1262](http://www.gnomefiles.org/app.php?soft_id=1262)
[http://sourceforge.net/project/showfiles.php?group_id=157492&release_id=391207](http://sourceforge.net/project/showfiles.php?group_id=157492&release_id=391207)[/QUOTE]

this is just for adding photos right ...  not album art[-(

---

### Post by veratyr on 2006-05-27
I don't want to have to add album art to my ipod when I've already added art to songs in the id3 tags. I'm looking for it to sync the way it does in itunes but in linux.

---

### Post by doclivingston on 2006-05-28
[QUOTE=chronusdark (snipped a bit)]they removed ipod video support (i.e. wont transfer m4v files) and the only thing people tell me is to buy the developers an ipod and they will get it working....not very professional in my opinion[/QUOTE]

Not very professional? I think saying that is fair. It's not that easy for developers to add support for hardware they don't have.


Of course I'm probably a bit biased here, as I've been saying the same thing in relation to Rhythmbox's iPod support for ~9 months. "None of the active developers have an iPod, so improving support will be hard. The best bet is for someone with an iPod to offer to do some development work, or buy/lend a developer an iPod".

That said the guy that did most of Rhythmbox's current iPod support and another person have been doing some work on it. Hopefully full iPod support should land in cvs soon after 0.9.5 gets out the door.

---

### Post by /dev/clast on 2006-05-28
I am using Rhythmbox for playing songs from my Ipod and gtkpod for syncing and adding songs to the Ipod. 
Both is working just fine with my Nano, including album art.
and as the doc said, full Ipod support will be in RB fairly soon. it's gonna be rocking as far as I am concerned.

:)

---

### Post by lizardking on 2006-05-28
I use [ListenGnome]("http://listengnome.free.fr/").
Just Wonderful!

---

### Post by teppic on 2006-05-28
Amarok 1.4.0's support is so much better than 1.3.x. You can download a semi-official version from a repostitory on the Kubuntu website. With 1.4 you can transfer music back and forth, including album covers, without the slightest problem.

---

### Post by gosh on 2006-05-28
I'm trying Amarok at the moment.
Anyone knows how to get podcasts on your ipod using amarok?

---

### Post by mlind on 2006-05-28
I'm too scared to use amaroK anymore. After reading this thread through at least
two other members share the same experience with me when amaroK suddenly
ate their playlists and corrupted songs database..

---

### Post by soze on 2006-05-28
[QUOTE=Bazon]
In Banshee, I didn't understand how to add things to the iPod at all.....

[/QUOTE]

1. Make sure your iPod is plugged in and mounted
2. Bring up Banshee
3. In the left-hand panel on Banshee click the iPod icon.
4. In the upper right click the "Synchronize iPod button"
5. Done!

---

### Post by virtuelvis on 2006-05-28
[QUOTE=jhorner]What does everyone use to manage their iPod in Dapper?  I tried Rythmbox and aMarok, really lik aMarok but its just been sketchy recently.  So I am looking for suggestions.[/QUOTE]

This might not be the answer you're looking for, but: I have totally given up on using anything that involves creating an iTunesDB at all.  Instead I installed [RockBox](http://www.rockbox.org/) on my iPod, and I just use nautilus or a shell to copy files to and from my iPod.  Much less error-prone, and way easier for daily use. :D

---

### Post by ketsugi on 2006-05-28
I just wanted to chime in with my AmaroK experience. After hearing a LOT of people recommending AmaroK for iPod management, I decided to try it out.

It seemed okay until I realised I couldn't manage playlists directly on the iPod. Too bad. I closed AmaroK and unmounted my iPod, and found to my horror that all my playlists were gone and I had only 255 (out of 5336) songs left on the iPod, although the song files were obviously still there since 24gb of space was in use.

I quickly loaded up gtkPod and restored my iTunesDB file. Thank God! I got back all my songs, although my playlists are still gone. Fortunately I rely almost entirely on Smart Playlists so I just have to recreate my dozen or so SPLs, and the one or two normal playlists I had.

No more AmaroK for me. >_<

```
$ sudo apt-get remove --purge amarok amarok-engines
```

---

### Post by ChrisNTR on 2006-05-29
[QUOTE=jdusablon]Not to mention...

Do ANY of these support Album art to *correctly* display it on the iPod itself? I've tried Banshee, Listen, gtkpod, amarok, etc.

**NONE** of these have iPod album art support.

At least gtkpod is relatively predictable in behavior, but its UI is awful and the program is half-broken.[/QUOTE]

I have used gtkpod to put album covers onto my iPod for various albums and it works perfectly. Which, to be honest, was a suprise to me!

---

### Post by nalmeth on 2006-05-29
GTKpod and amarok.

I've just learned you can replace the firmware on your ipod to be able to play anything. The project's are called ipodlinux and rockbox, I think.

---

### Post by ketsugi on 2006-05-29
Last I checked, iPodLinux doesn't support 5G iPods properly...

---

### Post by mlind on 2006-05-29
[QUOTE=nalmeth]GTKpod and amarok.

I've just learned you can replace the firmware on your ipod to be able to play anything. The project's are called ipodlinux and rockbox, I think.[/QUOTE]

I've tried out both in the past, and I must admit that **rockbox** is quality stuff!
It won't support iTunesDB, but has it's own replacement for that.

I suggest to try it out, installation is very easy using [wiki's instructions]("http://www.rockbox.org/twiki/bin/view/Main/IpodInstallation")

---

### Post by briguy on 2006-05-31
I've been using amaroK from SVN using the script from [amarok.kde.org]("http://amarok.kde.org").  I had to install glibpod from source as well to get the iPod support, but it has worked great so far.  Album artwork, podcasts (with artwork).  Video syncing hasn't worked, but I haven't tried lately so it may have been updated.

---

### Post by speedothebrief on 2006-10-06
UPDATE TIME!!!

I read through this thread and saw a lot of problems popping up with Amarok and the iPod. There were several posts about Amarok and the 1.4 version, and how much better the support is in that version.

It's true, support for the iPod in 1.4 (I'm using 1.4.3 KDE 3.5.2) is very smooth. And to lay the id3 album art to rest, YES it IS supported.

I am still trying to figure out how to sync Amarok with the iPod, but I did delete my entire iPod music database and reload it with my Amarok collection without any trouble whatsoever (minus the obvious lack of OGG support on the iPod).

So... I'd encourage those of you slighted by Amarok < 1.4 to give it another shot.

---

### Post by pgatrick on 2006-10-06
I use GtkPod, which works perfectly for me. With the exception of being able to add pictures, which it doesn't seem to do. And it won't load m4v, though mp4 video does fine, and album art works great as well.

---

### Post by Floola on 2006-10-07
Try floola. It supports artwork, videos (.mp4, .m4v) and much more.

[http://www.floola.com](http://www.floola.com)

---

### Post by Floola on 2006-10-13
Floola beta 6 released. Various bug fixed.

---

### Post by gummibaerchen on 2006-10-16
It should support Podcasts and get Open-Source.

Then I would be happy :)

---

### Post by Slace on 2006-10-17
I've receintly bought myself an iPod and am now looking at options of managing it through linux. I'm rather parshal to amaroK, having used it for a while with my music and not had any issues thus far. But I've found when its auto-mounted its owned by root, which means that I can't write to it.

Do I need to mount it with different arguments or something?

Also, what's around that's free and supports copying movies?

---

### Post by Floola on 2006-10-21
Floola b7 available. Video upload should work now. If anybody finds other m4v or mp4 that aren't uploaded correctly please let me know via email.

[http://www.floola.com](http://www.floola.com)

Thanks!

---

### Post by gummibaerchen on 2006-10-21
> **Floola said:**
> Floola b7 available. Video upload should work now. If anybody finds other m4v or mp4 that aren't uploaded correctly please let me know via email.

[http://www.floola.com](http://www.floola.com)

Thanks!

Will it ever be Open-Source?

---

### Post by IngSoc on 2006-10-21
So far I havnt seen any one complain about not being able to delete there songs using gtkpod but this seems to be my first problim. I try to select all and right click , delete but that dont work.

---

### Post by Lord Illidan on 2006-10-21
> **chronusdark said:**
> amarok is an excellent ipod managment program except for the fact that they removed ipod video support (i.e. wont transfer m4v files) and the only thing people tell me is to buy the developers an ipod and they will get it working....not very professional in my opinion but if your looking for just music management amarok is the best plus it will search for your album art automatically

Been using amarok from the start with ipod nano. Works very well.

---

### Post by gummibaerchen on 2006-10-21
> **chronusdark said:**
> amarok is an excellent ipod managment program except for the fact that they removed ipod video support (i.e. wont transfer m4v files) and the only thing people tell me is to buy the developers an ipod and they will get it working....

Are you serious? You can win an iPod Nano on their page, so if they want one for testing they should take this one.

[http://amaroK.kde.org](http://amaroK.kde.org)

---

### Post by maestrobwh1 on 2007-11-03
In amarok, if I drag something to a playlist, and that file is already on my ipod, it seems to add a duplicate file.  What am I doing wrong?

---

