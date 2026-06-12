---
title: "Request: GnomeBaker 0.4"
date: 2005-07-16
forum: Deferred/Invalid Requests
---

### Post by plutoprime on 2005-07-16
Hi, gnomebaker .4 came out with lots of bugfixes/features ... If you have the time it would be nice!

---

### Post by UbuWu on 2005-07-16
Really want this too!!!  \\:D/

---

### Post by TheSavage on 2005-07-16
+1 over here too :razz:

---

### Post by duffman25 on 2005-07-16
[QUOTE=plutoprime]Hi, gnomebaker .4 came out with lots of bugfixes/features ... If you have the time it would be nice![/QUOTE]

+1

Looking at the changelog it seems that they are doing a pretty good job:) Maybe it could be the default cd/dvd burning sw in breezy ;)

---

### Post by UbuWu on 2005-07-16
[QUOTE=duffman25]Maybe it could be the default cd/dvd burning sw in breezy ;)[/QUOTE]

A combination of nautilus (for data)/serpentine (for audio) is planned to be the default for burning on breezy. The reason for not using gnomebaker was that it had a lot of dependencies in universe. With this update that problem is solved! I sent a mail to the development mailing list asking to reconsider the decision on which burning program to use, so who knows what happens...  ;-)

---

### Post by plutoprime on 2005-07-16
What's sad is that your suggestion to the mailing list doesn't seem to get much attention ... it seems some of the apps have to have bare minimum functionality to be approved. Have you looked under multimedia options in gnome? There is a separate app for "Monitoring Volume" and "Monitoring Recording Volume". This my friends is absolutely retarded.

I would really hate it if the goal is to have a separate app for Burning folders, a separate app for burning files, a separate app for audio, another for video, another for blah ...

---

### Post by UbuWu on 2005-07-16
[QUOTE=plutoprime]What's sad is that your suggestion to the mailing list doesn't seem to get much attention ... it seems some of the apps have to have bare minimum functionality to be approved. Have you looked under multimedia options in gnome? There is a separate app for "Monitoring Volume" and "Monitoring Recording Volume". This my friends is absolutely retarded.

I would really hate it if the goal is to have a separate app for Burning folders, a separate app for burning files, a separate app for audio, another for video, another for blah ...[/QUOTE]

According to your comments you must be Farhad Shakiba?? I really hope there are more people that agree with me that gnomebaker is much more powerful... And maybe some people can give their comments on the mailing list as well. Those separate volume apps is just crazy! But please bear in mind that audiocdburning was a goal for breezy that was considered already completed with the inclusion of serpentine, so I wouldn't be surprised if for that reason gnomebaker will not be considered for breezy... but you never know...

---

### Post by duffman25 on 2005-07-17
[QUOTE=UbuWu]According to your comments you must be Farhad Shakiba?? I really hope there are more people that agree with me that gnomebaker is much more powerful... And maybe some people can give their comments on the mailing list as well. Those separate volume apps is just crazy! But please bear in mind that audiocdburning was a goal for breezy that was considered already completed with the inclusion of serpentine, so I wouldn't be surprised if for that reason gnomebaker will not be considered for breezy... but you never know...[/QUOTE]

I also think gnomebaker is a better solution to audio cd/cd/dvd burning, kde has k3b, gnome has gnomebaker. Even if it doesn't get in breezy main component, I'am going to apt-get it as soon as it comes out. :D

---

### Post by UbuWu on 2005-07-17
It is not going to happen... but of course it is in universe, so apt-get here I come!  :grin: (see mailing list for details)

---

### Post by vassie on 2005-07-18
Is there any news on this?, the changelog looks good

Ben

---

### Post by Burgundavia on 2005-07-18
Not in Breezy yet.

Corey

---

### Post by ubuntp on 2005-07-20
This is no backport since it's not in breezy yet, it's build from source. It still identifies itself as a 0.3 deb.

You must install libgstreamer0.8-0 and gstreamer0.8-plugins before installing gnomebaker.

[http://www-public.rz.uni-duesseldorf.de/~thpod001/gnomebaker_0.4-1_i386.deb](http://www-public.rz.uni-duesseldorf.de/~thpod001/gnomebaker_0.4-1_i386.deb)

---

### Post by jdong on 2005-07-20
DEFERRED for now, as it's not in Breezy. It would be an acceptable backport as soon as it reaches Breezy.

---

### Post by MetalMusicAddict on 2005-07-20
[QUOTE=ubuntp]This is no backport since it's not in breezy yet, it's build from source. It still identifies itself as a 0.3 deb, also the new dependencies are not checked, i was too lazy for all of that. It's experimental, it will not break your system, but sth. might not work because of a missed dependency.

You must install libgstreamer0.8-0 and gstreamer0.8-plugins before installing gnomebaker.

[http://www-public.rz.uni-duesseldorf.de/~thpod001/gnomebaker_0.4-1_i386.deb](http://www-public.rz.uni-duesseldorf.de/~thpod001/gnomebaker_0.4-1_i386.deb)[/QUOTE]
Installed fine man. Thanx. Do you **know** you missed a dependency or you think you might have? Thanx still. ;)

---

### Post by ubuntp on 2005-07-21
I don't think there is any new dependency except for gstreamer, it's just a warning to be on the safe side. I've burned a few CDs and a DVD now and so far all is well.

---

### Post by AgenT on 2005-07-22
Not inlcuding Gnomebaker in Breezy is not a good idea.  It is true that Breezy will have nice intergration, but there are things that a regular burning program provides that none of the intergrated programs will. For example, Gnomebaker provides the ability to burn cue and bin files, something that the Breezy burning intergration does not (so far as I know). And of course, as Gnomebaker matures more and more features will be added. It should be available, although maybe not installed by default.

---

### Post by RaymondQE on 2005-07-23
Will Gnomebaker 0.4 make it into breezy since IIRC there is an upstream version freeze ?

---

### Post by Confuse on 2005-07-24
I've been able to compile gnomebaker and run it sucessfully (as far as I know). Do all packages from the bp project have to be backported? I'm looking for some instructions on how to create a deb of this compile and have it be tested out. If anyone has any resources they'd like to share with me it'd be highly appreciated. Thanks.

Damian

---

### Post by AgenT on 2005-07-24
[QUOTE=Confuse]I've been able to compile gnomebaker and run it sucessfully (as far as I know). Do all packages from the bp project have to be backported? I'm looking for some instructions on how to create a deb of this compile and have it be tested out. If anyone has any resources they'd like to share with me it'd be highly appreciated. Thanks.

Damian[/QUOTE]

One word: [b]checkinstall
[/b]Get it, love it, make your source files into debs with ease! Search this forum as I have posted about this program (what it does and how to use it) multiple times.

---

### Post by SlugO on 2005-07-26
I think that cd burning deserves it own specialized program.
It's not such a trivial task as moving files to a disk or usb.
Each failed cd costs money and the only kind of cd that I
dare to use with an integrated burner is rw.

---

### Post by UbuWu on 2005-07-28
[QUOTE=SlugO]I think that cd burning deserves it own specialized program.
It's not such a trivial task as moving files to a disk or usb.
Each failed cd costs money and the only kind of cd that I
dare to use with an integrated burner is rw.[/QUOTE]

Me too, but the current idea (at least for breezy it is) of the developers is to have different ways for different kinds of cd-burning tasks, not one central cd-burning app. I even proposed on the development mailing list to replace serpentine with gnomebaker, but this request was quickly deferred. I hope the next version after breezy will have a cd burning app.

There were good reasons, by the way, earlier not to use gnomebaker. It needed a lot more new dependencies to be in main. But since the latest version of gnomebaker (0.4) uses gstreamer, this is not the case anymore.

---

### Post by AgenT on 2005-07-28
Gnomebaker can do things that the current Breezy way of burning cannot. Gnomebaker does not have to be intalled by default since the major burning tasks can already be done with the proposed applications in Breezy. But **Gnomebaker needs to be included in the official repositories**.

---

### Post by brian g on 2005-08-02
so what is the best way for me to use 0.4 today?
Installing it from the Gnomebaker page?
I'd like to get rid of K3b and would love to have the FLAC support that 0.4 offers.

---

### Post by Confuse on 2005-08-02
[QUOTE=brian g]so what is the best way for me to use 0.4 today?
Installing it from the Gnomebaker page?
I'd like to get rid of K3b and would love to have the FLAC support that 0.4 offers.[/QUOTE]

I'd say try to compile it; it compiled fine for me but I didn't try all the features.

---

### Post by brian g on 2005-08-03
i tried to compile it and found out i am missing a bunch of libraries that are required.  ](*,)

---

### Post by Confuse on 2005-08-03
[QUOTE=brian g]i tried to compile it and found out i am missing a bunch of libraries that are required.  ](*,)[/QUOTE]

Install the dev packages as needed from Synaptic...

---

### Post by AgenT on 2005-08-04
Or just use the [Debian package]("http://packages.debian.org/unstable/gnome/gnomebaker") or alien an rpm. Also, maybe you did not see it, but someone already made a deb for Ubuntu above.

---

### Post by brian g on 2005-08-05
[QUOTE=Confuse]Install the dev packages as needed from Synaptic...[/QUOTE]the versions i need are not avalible in Synaptic

```
dpkg: dependency problems prevent configuration of gnomebaker:
 gnomebaker depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu13.
 gnomebaker depends on libvorbis0a (>= 1.1.0); however:
  Version of libvorbis0a on system is 1.0.1-1.
 gnomebaker depends on libvorbisfile3 (>= 1.1.0); however:
  Version of libvorbisfile3 on system is 1.0.1-1.
dpkg: error processing gnomebaker (--install):
 dependency problems - leaving unconfigured

```

---

### Post by cowlip on 2005-08-08
[QUOTE=AgenT]Gnomebaker can do things that the current Breezy way of burning cannot. Gnomebaker does not have to be intalled by default since the major burning tasks can already be done with the proposed applications in Breezy. But **Gnomebaker needs to be included in the official repositories**.[/QUOTE]

Yes it's too bad :(  Gnomebaker is defintely the best cd burner i've used on any platform, ESPECIALLY windows (horibble nero!)

---

### Post by Knome_fan on 2005-08-08
It's in breezy now.
[click me](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gnomebaker&searchon=names&subword=1&version=breezy&release=all) 

Backporting it should be no problem now and if you want to build it yourself:
Adding the breezy deb-src entries to sources.list, getting the sources with apt-get source gnomebaker and than compiling it with dpkg-buildpkg worked like a charm for me.

---

### Post by ScoobyDan on 2005-08-28
[QUOTE=Knome_fan]It's in breezy now.
[click me](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gnomebaker&searchon=names&subword=1&version=breezy&release=all) 

Backporting it should be no problem now and if you want to build it yourself:
Adding the breezy deb-src entries to sources.list, getting the sources with apt-get source gnomebaker and than compiling it with dpkg-buildpkg worked like a charm for me.[/QUOTE]

Can we have this in "Newbie-English" please? :confused:

What is the correct entry in the sources list for this repository?

I tried the deb package, but got the same error as brian.

Many thanks!

Daniel

---

### Post by SilvioTO on 2005-09-06
I don't know if this work (on my pc is ok), but I compiled the latest gnomebacker (0.4.2) with checkinstall, and automatically have a .deb package. Try it, download from   [here](http://digilander.libero.it/silvio2001/gnomebaker-0.4.2_0.4.2-1_i386.deb)    

I hope this help for you!!   :) 

Silvio.

---

### Post by SilvioTO on 2005-09-06
correction... gnomebaker 0.4.2 installed correctly on my pc but don't burn dvd: the error is: Xlib: unexpected async reply (sequence 0x22862)! in console. After this application freeze. Sorry. I hope work for you.  :?

---

