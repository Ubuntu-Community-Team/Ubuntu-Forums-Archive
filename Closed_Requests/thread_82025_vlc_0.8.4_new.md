---
title: "vlc 0.8.4 new"
date: 2005-10-25
forum: Closed Requests
---

### Post by duffman25 on 2005-10-25
Breezy's vlc 0.8.4 was compiled to work with libwxgtk2.4-dev because of Unicode issues. According to this:
[http://lists.ubuntu.com/archives/dapper-changes/2005-October/000244.html](http://lists.ubuntu.com/archives/dapper-changes/2005-October/000244.html)
this issues have been fixed, so can we have a backport once breezy backports are opened?

Thanxs

---

### Post by stoffe on 2005-10-25
Yes please. :)

---

### Post by Kyral on 2005-10-25
I could build a package, but I forgot how to change debian/changelog for Backports... (Hey! Its been a couple months since I did this kinda thing! ;P)

Backports Admins, you guys want any help? :D

---

### Post by JuanC on 2005-10-26
Also an AMD64 package of VLC will be good.

---

### Post by vassie on 2005-10-26
I'd love to see this too, VLC plays anything you throw at it!

I have MPlayer installed, but that does not support DVD menu's (I only use it for mozilla-mplayer)

I hope to see a new VLC package soon

Ben

---

### Post by Kyral on 2005-10-26
[QUOTE=vassie]I'd love to see this too, VLC plays anything you throw at it!

I have MPlayer installed, but that does not support DVD menu's (I only use it for mozilla-mplayer)

I hope to see a new VLC package soon

Ben[/QUOTE]
I built them (Yanno, a LOT of packages come out of that one source...) and will upload them...somewhere tonight. Keep in mind these are *NOT OFFICIAL BACKPORTS!!* ;P

They should work, but Your Milage May Very ;P

Oh, they all have the custom version string "~cp1" to further set them apart from Backports :P

(Just have to make sure no one freaks and bothers JDong and Co if these don't work, don't want to get in trouble ;P)

---

### Post by vassie on 2005-10-26
[quote=Kyral]I built them (Yanno, a LOT of packages come out of that one source...) and will upload them...somewhere tonight. Keep in mind these are *NOT OFFICIAL BACKPORTS!!* ;P

They should work, but Your Milage May Very ;P

Oh, they all have the custom version string "~cp1" to further set them apart from Backports :P

(Just have to make sure no one freaks and bothers JDong and Co if these don't work, don't want to get in trouble ;P)[/quote]

Cool, thanks

I'll keep an eye out for them

Ben

---

### Post by Kyral on 2005-10-26
They are all in here, built for x86

[http://people.clarkson.edu/~petermcv/vlc/]("http://people.clarkson.edu/%7Epetermcv/vlc/")

I'd love it if someone were to put them on some other webspace, they are quite big for a 50 MB space...and I'm almost out

---

### Post by vassie on 2005-10-26
[quote=Kyral]They are all in here, built for x86

[http://people.clarkson.edu/~petermcv/vlc/]("http://people.clarkson.edu/%7Epetermcv/vlc/")

I'd love it if someone were to put them on some other webspace, they are quite big for a 50 MB space...and I'm almost out[/quote] 
Thanks :)

I will try and mirror them tomorrow, I have a server at work I can use, but it's a bit unstable at the moment (hardware issue)

Ben

*EDIT God damn it! I have just FTP'd onto my box at work, and it has just knocked it over, will have to wait 'till tomorrow, sorry

PS Your packages work a treat, thank you so much, I so nice to have nice looking VLC back :)

---

### Post by angrykeyboarder on 2005-10-26
[quote=Kyral]They are all in here, built for x86

[http://people.clarkson.edu/~petermcv/vlc/]("http://people.clarkson.edu/%7Epetermcv/vlc/")

I'd love it if someone were to put them on some other webspace, they are quite big for a 50 MB space...and I'm almost out[/quote]

I'd be more than happy to host/mirror them. I've got plenty of unused space.

---

### Post by Kyral on 2005-10-26
I'm glad that they work :D

Now the Backports Team doesn't have to do it (its a simple matter to change the tagline to ~ubp1)

And if anyone wants to mirror them just throw the link here

---

### Post by Kyral on 2005-10-28
I had to remove them from my webspace because I needed it for academic reasons. Private Msg me if you want them ;P

---

### Post by ember on 2005-10-28
I guess, I can come up with some space for packages in one or two weeks - how much traffic did you have from that package?

---

### Post by Kyral on 2005-10-28
No idea. I think I may be able to convince my computer lab people to let me have an old machine as a server for this

---

### Post by hav0x on 2005-10-28
I could use those packages :|
You got pm! :D



edit: They worked like a charm thanks again and i hope you find a mirror for them.

---

### Post by angrykeyboarder on 2005-10-31
[quote=Kyral]I'm glad that they work :D

Now the Backports Team doesn't have to do it (its a simple matter to change the tagline to ~ubp1)

And if anyone wants to mirror them just throw the link here[/quote] 
I was all ready to upload them to my webspace when I realized you didn't include the source packages.

Distributing them without the source packages is in violation of the [GPL]("http://www.gnu.org/licenses/gpl.html").  I don't want any [big hairy guys]("http://images.google.com/images?svnum=50&hl=en&lr=lang_en&safe=off&q=richard+stallman&btnG=Search") knocking at my door.

If you have the sources as well, I'll upload all.

---

### Post by Kyral on 2005-10-31
Actually I didn't touch the source. All I did is made sure it built with the libs and whatnot in Breezy (in my Breezy PBuilder) and made a note in the debian/changelog that it was backported to breezy and appended the version string so that it would be overwritten when an official package with a higher version number came out (like when Dapper goes stable in 6 months). Streight Dapper sources

---

### Post by 23meg on 2005-10-31
Why don't you just post them to [rapidshare]("http://www.rapidshare.de")?

---

### Post by Kyral on 2005-10-31
Because I've never heard of it ;P

---

### Post by 23meg on 2005-10-31
So, when shall we see the packages?

---

### Post by Kyral on 2005-11-01
uhhh.....when I get free time (School is a ***** this week)

---

### Post by siml on 2005-11-02
i have found vlc with a good "style" again and the new wma codecs.. (and i think other codes are included too)
[http://people.uleth.ca/~dave.brady/vlc-with-vc1.deb](http://people.uleth.ca/~dave.brady/vlc-with-vc1.deb)

maybe you are looking for that... ;-)

lg

---

### Post by vassie on 2005-11-03
Mirror

[http://195.153.177.76/upload/ben/ubuntu/vlc084/]("http://195.153.177.76/upload/ben/ubuntu/vlc084/")

Ben

---

### Post by vassie on 2005-11-03
Please note that my mirror might be down for a few hours soon, for some reason Hoary work better than Breezy on my server, so I might reload it

Ben

(PS If anyone want's any Ubuntu releated stuff uploaded, PM me)

---

### Post by sparkster83 on 2005-11-05
[QUOTE=vassie]Mirror

[http://195.153.177.76/upload/ben/ubuntu/vlc084/]("http://195.153.177.76/upload/ben/ubuntu/vlc084/")

Ben[/QUOTE]

Thanks! Working like a charm!

Sparkster

---

### Post by jdong on 2005-11-11
Sent to James.

---

### Post by cypher35 on 2005-11-13
the original link and the mirror both appear to be down...  any chance someone could put up a new one?

---

### Post by vassie on 2005-11-13
Sorry, I moved them...

[http://195.153.177.76/upload/files/1/ubuntu/vlc084/](http://195.153.177.76/upload/files/1/ubuntu/vlc084/)

Ben

---

### Post by Hairy_Palms on 2005-11-14
thanks for this :) i downgraded to 0.8.2 and the notification icon was pissin me off tellin me to get 0.8.4 :)

---

### Post by nKov on 2005-12-02
All mirrors seem to be down? :(

EDIT:

Should have looked harder.
[http://www.ubuntuforums.org/showpost.php?p=417378&postcount=7](http://www.ubuntuforums.org/showpost.php?p=417378&postcount=7) for anyone like me who's looking.

EDIT 2:

Oops. Not quite. :x

---

### Post by hav0x on 2005-12-03
Kyral made some sweet packages for it.
PM him, or me and someone will mail them to ya.

---

### Post by angrykeyboarder on 2005-12-07
[quote=Kyral]Actually I didn't touch the source. All I did is made sure it built with the libs and whatnot in Breezy (in my Breezy PBuilder) and made a note in the debian/changelog that it was backported to breezy and appended the version string so that it would be overwritten when an official package with a higher version number came out (like when Dapper goes stable in 6 months). Streight Dapper sources[/quote] 

Whether you touched the source or not is not the issue, VLC is licensed under the GPL.

See [http://www.gnu.org/licenses/gpl-faq.html#SourceAndBinaryOnDifferentSites]("http://www.gnu.org/licenses/gpl-faq.html#SourceAndBinaryOnDifferentSites")

& [http://www.gnu.org/licenses/gpl-faq.html#TOCAnonFTPAndSendSource]("http://www.gnu.org/licenses/gpl-faq.html#TOCAnonFTPAndSendSource")
[ ]("http://www.gnu.org/licenses/gpl-faq.html#SourceAndBinaryOnDifferentSites")

---

### Post by jdong on 2005-12-07
Yes; I was pretty burned on the GPL violation thing with Mirromax, too.... Make sure you know the terms... Regardless of modification of sources, you need to either host the source or have a contract with those who hosts the source to keep it for a predetermined amount of time (IIRC 6 months?)

---

### Post by angrykeyboarder on 2005-12-08
[quote=jdong]Yes; I was pretty burned on the GPL violation thing with Mirromax, too.... Make sure you know the terms... Regardless of modification of sources, you need to either host the source or have a contract with those who hosts the source to keep it for a predetermined amount of time (IIRC 6 months?)[/quote] 
[B][SIZE=4]Thank you! :-)

[/SIZE][/B]And like I also said originally. I don't want any [big hairy guys]("http://jimmysweblog.net/2004/10/richard-stallman.jpg") knocking at my door. ;-)

---

### Post by Humanoid on 2005-12-25
I've my own gtk2-version but what's that fuzz upper? It's forbidden to release your own deb publically?

---

### Post by jdong on 2005-12-31
[QUOTE=Humanoid]I've my own gtk2-version but what's that fuzz upper? It's forbidden to release your own deb publically?[/QUOTE]

No; it's not. There are three issues with regards to third party package:

(1) Packaging method/quality: How was the package made? Debian approved tools, standard Backports procedures? A dirty checkinstall or alien job? That can greatly affect package quality for users.

(2) Authenticity/trust: Can these binary packages be trusted? Is the packager a reliable person with a good track record? Is the package cryptographically signed to deter tampering?

(3) Licensing: Have the license terms been met? GPL violation is very common here when people distribute their packages. Often no source packages can be located -- which is not permitted under the GPL. Most of us omit them out of laziness (uploading a huge "pointless" tarball) or think that just because there are no source modifications in a backport that sources are unnecessary (untrue).

---

### Post by infinito on 2006-01-15
[QUOTE=jdong]Sent to James.[/QUOTE]
This backport (vlc0.84) has just been built for AMD64 and powerpc (since 22 november), but not for i386. Any idea on this??

---

### Post by decaf on 2006-01-19
Add this line for my x86 backport (just a recompile without .mkv support):

deb [http://dot.name.tr/ubuntu-decaf/](http://dot.name.tr/ubuntu-decaf/) debs/

---

### Post by vassie on 2006-01-19
I moved them again, sorry

[http://195.153.177.76/uploads/ben/linux/ubuntu/vlc084/](http://195.153.177.76/uploads/ben/linux/ubuntu/vlc084/)

Ben

---

### Post by engla on 2006-01-19
Thank you for this backport, it solved a lot on my install-- previously skins/wxwid wasn't working and vlc looked ugly (gtk1)
Now it looks gorgeous!

---

### Post by Noah0504 on 2006-01-21
Is there a reason why a lot of the functionality isn't working?  I cannot access the preferences, add new items to the playlist, or a few other things.

---

