---
title: "Replacement for buggy Kaffeine package here"
date: 2005-04-17
forum: Desktop Environments
---

### Post by Zakalwe on 2005-04-17
Hi all, I'm a long time Linux user (nearly 10 years now!) and recently decided to give Kubuntu a go on my laptop. So far I'm pretty happy with it, but was disapointed with the state of kaffeine. It crashes left right and center and is pretty much unusable. It's a shame as it's a great media player. There's already a bug filed so rather than duplicate it, I decided to help out.

[http://homepage.ntlworld.com/fowlerc/](http://homepage.ntlworld.com/fowlerc/)

Downloaded the deb off of that page and run dpkg -i on it to install it. It should cleanly replace your existing kaffeine package. 

Of course, you should ALWAYS be wary of downloading random packages from strangers, but I assure you I'm a nice guy :)

---

### Post by kal_zakath on 2005-04-17
Thanks a lot dude, I'm going to install it right now.

(You're sure the is no backdoor or something hmm ?? :p )

---

### Post by kal_zakath on 2005-04-17
Installed, tested, and approved :)

---

### Post by getaceres on 2005-04-17
I haven't teted it deeply but the 100% CPU utilization bug seems to been gone.

---

### Post by Jonathan2007 on 2005-04-17
Oh thank you thank you sooo much. I was having lots of problems with Kaffeine that were making me want to go back to Xandros or even Windows. But thanks to you and your patch it has solved all my Kaffeine problems. I posted about my problems in [this](http://http://ubuntuforums.org/showpost.php?p=129204&postcount=13) post. As you can see it would be very annoying. 

Again thanks a ton and to all those skeptical about this it works 100% and got rid of all my problems.

---

### Post by epb613 on 2005-04-17
Hey thanks so much! I have only been using Kubuntu for a week and have been amazed with Kaffeine (I think it's the best media player to date) except for the 2 or 3 bugs I found. This fixed them all as far as I can tell; Thanks so much!

---

### Post by Ironi on 2005-04-17
Would you please post a unified diff so that those so inclined can build it from source? TIA. :)

---

### Post by ykpaiha on 2005-04-17
Great it works and +++ it's in my language !!!At last

---

### Post by kal_zakath on 2005-04-17
[QUOTE=ykpaiha]Great it works and +++ it's in my language !!!At last[/QUOTE]
 Yeah,I didn't even noticed that now the right language is used, really cool work

---

### Post by Zakalwe on 2005-04-17
[QUOTE=Ironi]Would you please post a unified diff so that those so inclined can build it from source? TIA. :)[/QUOTE]


All I did was dpkg-buildpackage the latest sarge source package on kubuntu :) Zack Cerza ( The debian package maintainer) is the one who did the real work here so thanks are due to him.

---

### Post by Ironi on 2005-04-17
[QUOTE=Zakalwe]All I did was dpkg-buildpackage the latest sarge source package on kubuntu :) Zack Cerza ( The debian package maintainer) is the one who did the real work here so thanks are due to him.[/QUOTE]
Interesting; I installed 0.6-1 from Debian unstable's repos and it still had the 100% CPU utilization on quit problem. Built it from source and the problem seems to be gone. Thanks for the info.

---

### Post by !nkubus on 2005-04-18
Wow that's awesome it works like a charm :) no more cpu trouble :)

---

### Post by ludi on 2005-04-18
Hi.
Good work! Thanks for your support :)
By the way, somebody knows were can I found a Kmplayer.deb package?
I have dial up connection and it take me a lonnnng time to compile from source (deps.).
Regards.

---

### Post by brk3 on 2005-04-19
I dont find any trouble with kaffiene on my kubuntu.. Thanks anyway though  :)

---

### Post by Zakalwe on 2005-04-19
[QUOTE=brk3]I dont find any trouble with kaffiene on my kubuntu.. Thanks anyway though  :)[/QUOTE]

While playing a video file, try to open another and see what happens. For most people it will crash. For a lot of people the kaffeine process will also still run in the background eating up CPU.

---

### Post by ceti on 2005-04-19
Why not give VLC a shot?
VLC is prettier, lighter and bug-free.
And it's in Synaptic.

Chees
ceti

---

### Post by jubei on 2005-04-28
[QUOTE=Zakalwe]While playing a video file, try to open another and see what happens. For most people it will crash. For a lot of people the kaffeine process will also still run in the background eating up CPU.[/QUOTE]

Yep, I had this problem. Its resolved now though with this update.

I still have one problem with kaffeine though. When I come back from fullscreen mode I have to hit maximize to get my controls down the bottom back. Anyone else had this trouble?

---

### Post by neilius on 2005-04-29
Excellent!!! Thanks a million for this, no more crashes or that process left running in the background eating cpu. Awesome!

Regards,

Neil.   :)

---

### Post by firas on 2005-05-01
Thanks a lot Zakalwe !! It was driving me nuts.

---

### Post by philipacamaniac on 2005-05-10
This is a great quickfix package. Hopefully the Kubuntu packagers will put this in to the main repo. (Do they do bugfixes between releases?)

Anyway, you should add one more thing. Kaffeine likes to add a service menu to every single file, but the latest CVS finally corrected that. It is a very simple fix:

Edit /usr/share/apps/konqueror/servicemenus/kaffeine_append_file.desktop
and change the ServiceTypes line to:

```
ServiceTypes=application/x-ogg,audio/basic,audio/vnd.rn-realaudio,audio/x-aiff,audio/x-mp3,audio/x-mpeg,audio/x-mpegurl,audio/x-ms-wma,audio/x-ogg,audio/x-pn-realaudio,audio/x-pn-realaudio-plugin,audio/x-scpls,audio/x-wav,audio/x-flac,video/x-matroska,audio/x-matroska,video/mpeg,video/msvideo,video/quicktime,video/vnd.rn-realvideo,video/x-avi,video/x-fli,video/x-flic,video/x-ms-asf,video/x-ms-wmv,video/x-msvideo,application/x-mplayer2,application/smil,application/x-kaffeine,audio/x-musepack
```

EDIT: Nevermind, I see that this package takes care of that already. Sweet!

---

### Post by Ironi on 2005-05-11
0.6-0ubuntu4 for breezy fixed the major problem discussed in this thread. I don't know why it didn't go to hoary as well, although there could be a reason for that. In the meantime, you can download it directly from the repository:

[http://archive.ubuntu.com/ubuntu/pool/main/k/kaffeine/](http://archive.ubuntu.com/ubuntu/pool/main/k/kaffeine/)

Don't blame me if it doesn't work on hoary, though. :)

---

### Post by palsyboy on 2005-06-08
Thanks, Zakalwe!

---

### Post by caspar_wrede on 2005-06-08
What I want to know is why haven't the kubuntu developers got round to fixing this and then letting it get automatically upgraded by apt?

kaffeine is arguably one of the most important apps for KDE yet it was realeased broken and hasn't been fixed. It doesn't reflect too well on Kubuntu (even though I love it). Or are they concentrating on more important stuff for the next release?

---

### Post by philipacamaniac on 2005-06-08
[QUOTE=caspar_wrede]What I want to know is why haven't the kubuntu developers got round to fixing this and then letting it get automatically upgraded by apt?

kaffeine is arguably one of the most important apps for KDE yet it was realeased broken and hasn't been fixed. It doesn't reflect too well on Kubuntu (even though I love it). Or are they concentrating on more important stuff for the next release?[/QUOTE]

Er, hmm... they have! Ubuntu.com repositories don't allow updates once a release has gone final, so they can't upload Hoary updates to ubuntu.com (or mirrors).

So, they added the fix to their own Kubuntu.org archive.
Browse here [http://kubuntu.org/pool/kaffeine/](http://kubuntu.org/pool/kaffeine/) and you'll see an update.
Add "deb [http://kubuntu.org/](http://kubuntu.org/) hoary-updates main" and you get an update.

Yes, they are actively working on Breezy, but it isn't like they are ignoring Hoary. They even released KDE 3.4.1 for Hoary the very day it was announced at KDE!

---

### Post by dolny on 2005-06-08
Thanks!

---

### Post by Mgcross on 2005-07-12
This is why I love this OS AND the people on this forum, and the forum itself...I was tired of Totem not working as I wanted and went for kaffeine, even though I use Gnome. Did what I wanted, but had Firefox crashing left and right, and also would not shut down until killed. I had to look in ONE thread to find this post and it fixed my problems completely. Hats Off to ALL the helpful people here!

G

---

### Post by coaxx on 2005-09-22
dito :-)

---

### Post by helwitch on 2005-10-06
Thanks tons, both to the person who posted the upgraded package, and the person who provided the deb link for upgrades!

---

### Post by coaxx on 2005-11-02
[QUOTE=philipacamaniac]Er, hmm... they have! Ubuntu.com repositories don't allow updates once a release has gone final, so they can't upload Hoary updates to ubuntu.com (or mirrors).

So, they added the fix to their own Kubuntu.org archive.
Browse here [http://kubuntu.org/pool/kaffeine/](http://kubuntu.org/pool/kaffeine/) and you'll see an update.
Add "deb [http://kubuntu.org/](http://kubuntu.org/) hoary-updates main" and you get an update.

Yes, they are actively working on Breezy, but it isn't like they are ignoring Hoary. They even released KDE 3.4.1 for Hoary the very day it was announced at KDE![/QUOTE]

This worked for me with Hoary. But now I have upgraded to Breezy and my Kaffeine seems to be removed. Is there a breezy deb anywhere?

---

