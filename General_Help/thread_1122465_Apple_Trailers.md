---
title: "Apple Trailers"
date: 2009-04-11
forum: General Help
---

### Post by rkapadia16 on 2009-04-11
I can't seem to view apple trailers on ubuntu. I am new to unbuntu. Is there any way of viewing apple trailers? All I get is a white screen when I try to play a trailer.

Thanks.

---

### Post by juancarlospaco on 2009-04-11
***Moonlight***

install it.

---

### Post by rkapadia16 on 2009-04-11
How do I install Moonlight?

---

### Post by coffeecat on 2009-04-11
Moonlight isn't going to help. Apple trailers are simply ordinary .mov video files.

Install mozilla-mplayer and mplayer. That should do it. Or right-click and download the .mov file and play this in mplayer or vlc.

I'm having difficulty playing an Apple trailer with the mozilla-mplayer plugin in a virtualised Linux Mint6 at the moment, although the trailer downloaded fine and played in vlc. Mozilla-mplayer has always worked in the past for me so I'll try in one of my normal Ubuntu installations later and get back to you.

---

### Post by N_Nick on 2009-04-11
> **rkapadia16 said:**
> How do I install Moonlight?

Take a look at:

```
http://nancib.wordpress.com/2009/01/10/moonlight-got-easier-for-ubuntu-users/
```

---

### Post by rkapadia16 on 2009-04-11
Thanks for the website. I have one question:
[I]
Running on Ubuntu, or possibly any recent Debian-based distro, and want to give it a try for yourself? You can snag Moonlight from directhex’s repo and be assured that if he updates his package you’ll get the update notification from the Update Manager. Just add this line to your /etc/apt/sources.list

    deb [http://ppa.launchpad.net/directhex/ubuntu](http://ppa.launchpad.net/directhex/ubuntu) intrepid main[/I]

How do I add this line to /etc/apt/sources.list?

---

### Post by coffeecat on 2009-04-11
**rkpadia**, I've checked in my ordinary Ubuntu installation and Apple Quicktime trailers are playing fine with the default Firefox Totem plugin. Install the package ubuntu-restricted-extras in Synaptic, and that should include the codecs for Apple Quicktime .mov files.

---

### Post by rkapadia16 on 2009-04-11
> **coffeecat said:**
> **rkpadia**, I've checked in my ordinary Ubuntu installation and Apple Quicktime trailers are playing fine with the default Firefox Totem plugin. Install the package ubuntu-restricted-extras in Synaptic, and that should include the codecs for Apple Quicktime .mov files.

I tried that and it still doesn't work. I still get the white screen. No sound. I have MPlayer and VLC installed.

---

### Post by N_Nick on 2009-04-11
> **rkapadia16 said:**
> *deb [http://ppa.launchpad.net/directhex/ubuntu](http://ppa.launchpad.net/directhex/ubuntu) intrepid main*

How do I add this line to /etc/apt/sources.list?

```
sudo gedit /etc/apt/sources.list
```

and just paste it at the end.

Note: i haven't tested moonlight myself.

---

### Post by ukblacknight on 2009-09-27
I'm having trouble with Apple Trailers.  Trying to view any of the HD videos [here]("http://www.apple.com/trailers/sony_pictures/cloudywithachanceofmeatballs/"), however nothing happens when I click on a resolution.  I tried using wget to get the .mov file, that returned nothing, VLC doesn't play anything and mplayer returns an error: Couldn't resolve name for AF_INET6: [www.apple.com](www.apple.com)

Anyone else experiencing this problem?

---

### Post by Catarina on 2009-09-27
> **ukblacknight said:**
> I'm having trouble with Apple Trailers.  Trying to view any of the HD videos [here]("http://www.apple.com/trailers/sony_pictures/cloudywithachanceofmeatballs/"), however nothing happens when I click on a resolution.  I tried using wget to get the .mov file, that returned nothing, VLC doesn't play anything and mplayer returns an error: Couldn't resolve name for AF_INET6: [www.apple.com]("http://www.apple.com")

Anyone else experiencing this problem?

I tried it out, on Linux Mint 7, and it opened it up, but it just wouldn't play: the "Play" icon just kept blinking. I installed ubuntu-restricted-extras, remains the same, and I've got both Totem and MPlayer on my system. :confused:

---

### Post by ukblacknight on 2009-09-27
I too, have MPlayer, ubuntu-restricted-extras installed, also mozilla-mplayer.

It's like the file doesn't exist?  I know it works because my mate sent me the link, who'd just watched it (on Snow Leopard).

---

### Post by polki@mac.com on 2009-09-28
Someone on this forum made a script:


```

#!/bin/bash
# atget - download trailers from Apple website

# Usage if no parameters give
if [ -z $@ ]; then
  echo " atget <apple-trailer-url>"; exit
fi

# Prepend 'h' before resolution to create a valid url
newurl=$(echo $@ | sed 's/_\([0-9]*[0-9][0-9][0-9]\)p.mov/_h\1p.mov/g')

# Download trailer and save to the desktop
#wget -U QuickTime/7.6.2 "$newurl" -O $HOME/Desktop/${@##*/}

# Play trailer with mplayer (using 200MB cache to be sure trailer is dl'd first)
mplayer -cache 200000 -user-agent 'QuickTime/7.6.2 (qtver=7.6.2;os=Windows NT 5.1Service Pack 3)' $newurl

```


I named mine "appletraier", made it executable and then run it in terminal by typing:

"./appletrailer http://movies.apple.com/movies/magnolia_pictures/ongbak2/ongbak2-clip_720p.mov"

Just copy the links from Apple's site and enjoy the trailers :-)

---

### Post by philinux on 2009-09-28
Apple are blocking gstreamer. I think a fix is in karmic. On Jaunty just now.
[https://bugs.launchpad.net/gstreamer/+bug/418064](https://bugs.launchpad.net/gstreamer/+bug/418064)
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/434993](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/434993)

---

### Post by ukblacknight on 2009-09-28
> **polki@mac.com said:**
> Someone on this forum made a script:


```

#!/bin/bash
# atget - download trailers from Apple website

# Usage if no parameters give
if [ -z $@ ]; then
  echo " atget <apple-trailer-url>"; exit
fi

# Prepend 'h' before resolution to create a valid url
newurl=$(echo $@ | sed 's/_\([0-9]*[0-9][0-9][0-9]\)p.mov/_h\1p.mov/g')

# Download trailer and save to the desktop
#wget -U QuickTime/7.6.2 "$newurl" -O $HOME/Desktop/${@##*/}

# Play trailer with mplayer (using 200MB cache to be sure trailer is dl'd first)
mplayer -cache 200000 -user-agent 'QuickTime/7.6.2 (qtver=7.6.2;os=Windows NT 5.1Service Pack 3)' $newurl

```


I named mine "appletraier", made it executable and then run it in terminal by typing:

"./appletrailer http://movies.apple.com/movies/magnolia_pictures/ongbak2/ongbak2-clip_720p.mov"

Just copy the links from Apple's site and enjoy the trailers :-)

Cheers for this!  I put a copy of it in to /usr/bin/ so I can just do "viewat <apple-url>" :)

---

### Post by philinux on 2009-09-28
This is fixed in Karmic 9.10

---

### Post by smoohta on 2009-09-30
Correct me if I'm wrong, but Karmic release is about a month away right?
How is it that this kind of thing doesn't get updated in jaunty/intrepid/hardy as well? all Ubuntu users who want to view Apple trailers are supposed to upgrade to Karmic now? :)
One of the bugs philinux linked to was opened a month ago- even if it does get pushed to older versions, when would that ever be?

Sorry, I'm just ranting here ;)

---

### Post by philinux on 2009-09-30
> **smoohta said:**
> Correct me if I'm wrong, but Karmic release is about a month away right?
How is it that this kind of thing doesn't get updated in jaunty/intrepid/hardy as well? all Ubuntu users who want to view Apple trailers are supposed to upgrade to Karmic now? :)
One of the bugs philinux linked to was opened a month ago- even if it does get pushed to older versions, when would that ever be?

Sorry, I'm just ranting here ;)

I agree. I would hope a fix would be backported to earlier releases. I made the comment regarding karmic to show that it is fixable.

---

### Post by smoohta on 2009-09-30
Hey Everyone,
I've patched the Jaunty Totem source with the commits from the bugs philinux pointed to (specifically - commits d3180aafb8597a6244a9e98425c721b1a6b0a33c and c3a784b72a70b9fae5ef9279faa15ea4dc49933c).
I've built .debs using the Ubuntu (or debian I guess...) way of building the packages (e.g. dpkg-buildpackage and not usual make) - my first time :)
Anyway... I wanted to upload the .deb files to launchpad but the instructions for that seem a little too much for me (at least for now) to handle, does anyone know of a good place to put the files so anyone who wants to can download them?

Thanks :)

---

### Post by smoohta on 2009-09-30
Never mind the above post...
If anyone wants it- the fixed totem package (for Jaunty) can be found at [https://launchpad.net/~smoohta/+archive/ppa](https://launchpad.net/~smoohta/+archive/ppa) :)

---

### Post by andrew.46 on 2009-10-31
Mind you there is an easier way for those who simply want to view these trailers in a browser window which has been working very well for me. You will need to have a decent copy of MPlayer installed, preferably current svn + w32codecs from MEdibuntu. Then install the gecko-mediaplayer:

```
$ sudo apt-get remove totem-mozilla
$ sudo apt-get install gecko-mediaplayer 
```

and then add the lines suggested above to your $HOME/.mplayer/config in the following manner:

```
user-agent='QuickTime/7.6.2 (qtver=7.6.2;os=Windows NT 5.1Service Pack 3)'
``` 

I suspect a less ornate user-agent setting would work but this was suggested previously and certainly works well enough on my system. Then simply open the trailer with Firefox as in previous times. I attach a screenshot to show this in action.

All the best,

Andrew
[I]
**Edit:** Hmm.... I might have been talking rubbish about the user-agent setting, looks like newer versions of gecko-mediaplayer have Quicktime emulation built in...[/I]

---

### Post by petaloid on 2010-06-08
@andrew.46

How do you get the up to date svn and w32codecs?

---

### Post by proggy on 2010-06-08
> **andrew.46 said:**
> 

```
$ sudo apt-get remove totem-mozilla
$ sudo apt-get install gecko-mediaplayer 
```[CODE]
then install media connectivity in Firefox
https://addons.mozilla.org/en-US/firefox/addon/446/

---

### Post by petaloid on 2010-06-08
Actually I found my own solution.
I added the Medibuntu repository and then because I am running 64bit ubuntu I downloaded and then installed w64codecs from there.
I couldn't find svn, but the media player worked fine without it.

So for 64bit users here are the steps that I followed:

1)Add Medibuntu repos
2)Install w64codecs and mplayer and then gecko-mediaplayer
3)Restart Firefox

And then you're done.

---

### Post by andrew.46 on 2010-08-25
Hi petaloid,

> **petaloid said:**
> How do you get the up to date svn and w32codecs?

My apologies for missing this post quite some time ago! I run a guide on these forums for the svn MPlayer, the most recent version of this guide can be seen here:

Howto: Build the svn MPlayer under the latest release version of Ubuntu 
[http://ubuntuforums.org/showthread.php?t=1542240](http://ubuntuforums.org/showthread.php?t=1542240)

All the best,

Andrew

---

