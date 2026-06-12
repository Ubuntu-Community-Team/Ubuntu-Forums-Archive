---
title: "A Konqueror player ?"
date: 2007-08-07
forum: Desktop Effects &amp; Customization
---

### Post by anders_ps3 on 2007-08-07
Hi all!

Have been strolling around the net trying to get a grip of what is the best "flash"-like player for me. To make a long story short: I need advice!

1. Please suggest a robust player plug-in for my Konqueror. A (ref to a/) HowTo would be useful, me being a newbie. 

2. Do I have to remove any packages in order to get it working? After a number of installs etc, adept now reports (searching "player") that the following packages are installed: gnash, kaffeine, kaffeine-xine, kmplayer-base, kmplayer-konq-plugins, libgnash0, libxine1, mozilla-plugin-gnash.

Bkgd info: I have a live-installed Kubuntu 7.04 on a ps3 jacked to an LG full-HD screen. Surfing goes otherwise fine; ADSL behind a Netgear router with factory settings.

Best regards,
Anders

---

### Post by Happy_Man on 2007-08-07
> **anders_ps3 said:**
> Hi all!

Have been strolling around the net trying to get a grip of what is the best "flash"-like player for me. To make a long story short: I need advice!

1. Please suggest a robust player plug-in for my Konqueror. A (ref to a/) HowTo would be useful, me being a newbie. 

2. Do I have to remove any packages in order to get it working? After a number of installs etc, adept now reports (searching "player") that the following packages are installed: gnash, kaffeine, kaffeine-xine, kmplayer-base, kmplayer-konq-plugins, libgnash0, libxine1, mozilla-plugin-gnash.

Bkgd info: I have a live-installed Kubuntu 7.04 on a ps3 jacked to an LG full-HD screen. Surfing goes otherwise fine; ADSL behind a Netgear router with factory settings.

Best regards,
Anders
What about just using Flash? It's in the repos; just use ```
sudo apt-get install flashplugin-nonfree
```

If you don't want to use flash, then Gnash is your best bet; unfortunately, it's not nearly as compatible.

---

### Post by anders_ps3 on 2007-08-07
Hi!

Yes, I tried it, but it didn´t work. (Said to be due to the odd architecture of the ps3, and Adobes unwillingness issue code for ps3/konqueror.) Did you mean that on the repository?

Thanks anyway =-)

---

### Post by anders_ps3 on 2007-08-07
Hmm, I just read the Kubuntu package list in Adept after trying to fetch the lot: no flashplugin-nonfree that i could see. Should I? Or does it emerge under another name(s)?

Or do I use Adept incorrectly? (I had checked: "Canonical-supported...", "Community-maintained...", "Proprietary drivers...", "Software restricted..." in the Adept > Manage Repositories tab. Then I hit "Close" and subsequently, "Reload".  Was that right?)

---

### Post by miggols99 on 2007-08-08
The adobe flash player is only available for the i686 architecture. For a media player I recommend kaffeine for KDE as it plays just about everything. Gnash only supports up to flash 7 I believe, so I think you'll be able to play youtube videos. It looks like you've already got kmplayer installed as a plugin. Remove it and install kaffeine-mozilla
```

sudo apt-get remove kmplayer-base kmplayer-konq-plugins
sudo apt-get install kaffeine-mozilla

```

---

### Post by exhuma.twn on 2007-08-10
> **miggols99 said:**
>  ... It looks like you've already got kmplayer installed as a plugin. Remove it and install kaffeine-mozilla
```

sudo apt-get remove kmplayer-base kmplayer-konq-plugins
sudo apt-get install kaffeine-mozilla

```

Uh... oh... That's still a matter of taste, and you have the choice. Generally mplayer works just fine. On the other hand, I am experiencing a lot of trouble with kaffeine. If kaffeine works for you fine. But try to give both a spin and see which one you like best. I think there might also be a xine plugin available. Which is also worth a look.

Don't just blindly delete ;)

Also, somebody pointed out, that the "nonfree" flash plugin is only available for i686 machines. As you pointed out you are new to linux hence you might  not have heard the term before. So I'll go on a wee tangent and tell you what it means. Grab some popcorn, this is going to be lengthy... But hopefully interesting.

:popcorn:

i686 is a sub-classification of "processor architectures". It's part of the larger "x86" family (which also includes good old 286, 486, pentiums,...). Desktop PC's largely run with processors of that family. Recently there is another family emerging, namely the amd64 family of processors, and the name itself says it all. The number of amd46-based PC's has grown quite steadily over the past years.

Next to those two common architectures there is also the "PowerPC"-family. Largely found on MAC's (although they also ported to the x86 architecture lately). And if I am not mistaken (correct me if I'm wrong) the "Cell" Processor (which is inside the Playstation3) is based on the PowerPC architecture.

Now, your programs need to be compiled for your specific architecture so they can run. As the number of PowerPC-based machines is far lower than the others, It can take quite some time until a "binary" for this architecture is released (if ever). So you might not get lucky with playing all flash-based content on your PS3. Yes, this is very annoying and disappointing. I know.

Maybe you can find some repositories targetet for the PS3 which contains binaries of those packages.

Alternatively you might have better luck with a source-based linux distribution like Gentoo. Be prepared though that setting up Gentoo might prove to be less intuitive as setting up Ubuntu! But you might learn a lot of interesting things ;)

---

### Post by miggols99 on 2007-08-10
I recommend Kaffeine because it is a KDE app. If you were using (X)ubuntu, I would recommend MPlayer, which is an excellent gtk media player.

---

