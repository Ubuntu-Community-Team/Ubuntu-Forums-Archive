---
title: "I need a P2P Client"
date: 2006-01-08
forum: Desktop Environments
---

### Post by CarlosinFL on 2006-01-08
Can someone please recommend a good P2P client I can use on my Ubuntu machine?

---

### Post by kairu0 on 2006-01-08
Limewire is good, but I mainly use Bittorrent Official.

---

### Post by soulestream on 2006-01-08
gtk-gnutella, limewire, giFt, amule

take your pick. 

soule

---

### Post by earobinson on 2006-01-08
amule works 2

edit... to late

---

### Post by shade11 on 2006-01-08
Frostwire is a good choice.

---

### Post by CarlosinFL on 2006-01-08
I have Limewirei installed but when I click on "applications > internet > limewire", nothing happens. It does not attempt to load or start. I get no errors and no reaction.

I would love to use Limewire on this machine but I think there is something wrong or missing with the required Java for Limewire.

I used the [www.ubuntuguide.org](www.ubuntuguide.org) for installing Limewire.

---

### Post by GTvulse on 2006-01-08
[QUOTE=Carlwill]I have Limewirei installed but when I click on "applications > internet > limewire", nothing happens. It does not attempt to load or start. I get no errors and no reaction.

I would love to use Limewire on this machine but I think there is something wrong or missing with the required Java for Limewire.

I used the [www.ubuntuguide.org](www.ubuntuguide.org) for installing Limewire.[/QUOTE]
Limewire only works with Sun Java. Read the section on Sun Java in the  [Restricted Formats section of the Ubuntu Wiki]("https://wiki.ubuntu.com/RestrictedFormats"). And the next section on how to select a default java VM version.

---

### Post by lrmall01 on 2006-01-08
What happens if you open a terminal and type java -version?

---

### Post by Iandefor on 2006-01-08
Get Automatix and run it. It'll give you the option of installing Frostwire. That's a really good client.

---

### Post by leech on 2006-01-08
There's also edonkey2000 for it, along with a nice gtk GUI.

[http://forum.edonkey.com/viewtopic.php?t=79914](http://forum.edonkey.com/viewtopic.php?t=79914) For the command line

[http://ed2k-gtk-gui.sourceforge.net/download.shtml](http://ed2k-gtk-gui.sourceforge.net/download.shtml) for the GUI to it.  You'll need both.

Leech

---

### Post by UbunT00L on 2006-01-09
I am using mlDonkey, with the kmldonkey gui.  I can connect to openft, kazaa (fasttrack), gnutella, gnutella2, overnet, edonkey2000, direct connect, bittorrent...etc.

I don't think any other program can do this.  Word of advice though, make sure you're connected to some good servers before trying to download anything.

---

### Post by leech on 2006-01-09
mlDonkey works pretty well, though is a bit more difficult to set up.  Don't ever try to set it up in Windows, it's really a pain!

Leech

---

### Post by Thirsteh on 2006-01-09
[Azureus](http://azureus.sf.net)

It's Bittorrent, but it rocks.

---

### Post by cutOff on 2006-01-09
Azureus of course.

[HOWTO: Installing Azureus on Breezy]("http://www.ubuntuforums.org/showthread.php?t=75272&highlight=azureus")


Regards

---

### Post by UbunT00L on 2006-01-10
Anyone try KTorrent?  I've been using it for the past few days and am quite impressed with it.  Azureus is cool, but I'm not a huge fan of java.  KTorrent seems to have the same features, but without the need for java (KDE dependancies instead).

I basically use Ktorrent for large files (movies mostly or albums), and use kmldonkey for small obscure files (mostly individual music songs).

---

### Post by Suger on 2006-01-10
rtorrent is a nice ncurses bittorrent client, but I don't think it has made it to the Ubuntu repos yet (maybe I should brace myself and do it).

[http://libtorrent.rakshasa.no/](http://libtorrent.rakshasa.no/)

---

### Post by byen on 2006-01-10
ok..a little silly question..
What do you guys download from them? A long time ago... i used to download all kinds of files until i found out that one of my classmates got caught and fines..that scared the crap outta me... is there like a safe limit ?

---

### Post by slux on 2006-01-10
Frostwire isn't a very good development IMO. Just rips a single reminder off Limewire and otherwise just repackages their code. Perfectly legal under the terms of the GPL, sure, but I think the original devs ought to get the credit they deserve.

---

### Post by stoeptegel on 2006-01-10
Latest SVN version of Ktorrent is processing well, there are bugs but i think it's usable for most people now. It isn't my preferred client yet, but it will get there when i look at the bug sloving scheme.

@Suger
Yes please make a rtorrent package if you feel like, ncurses apps rock. :p

---

### Post by ronmarley1 on 2006-01-10
Automatix will install DC++ amule and Limewire.  Frostwire too, which is a GPL clone of Limewire.  Here's the link to Automatix: [http://www.ubuntuforums.org/showthread.php?t=80295&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=80295&highlight=automatix)  There's a double-edged sword here, though.  Automatix makes it very easy for folks to install a ton of apps.  The bad part is that if you're new to Linux, learning how to install stuff is a skill you'll eventually need, and Automatix is something a newbie can use.

---

### Post by nalmeth on 2006-01-10
I use Apollon for the gIFT network. 

sudo apt-get install apollon gift kaboodle

(apollon uses kaboodle to preview files)

it doesn't come with fasttrack though you can add it if you want.

The only problem is that it doesn't have a filter, so sometimes you get some search results you were not anticipating (..cough)

I only recommend this if you don't have a problem ignoring some search results you may find offensive. 

I have not tried mlDonkey yet, so you may want to go there first. 

BTW on start-up it will ask you were your gIFT files are. They are in /usr/share/gift.

---

### Post by CarlosinFL on 2006-01-10
Anyone know why I can't get Limewire working on my machine? I have Java installed on my machine but it appears just noth the correct version or something to that nature...

```
stricom@ubuntu:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

```

I followed the ubuntuguide.org for installing Limewire but the part about installing the required Java did not work. Any tips and or suggestions?

When I click the Limewire icon, nothing happens or errors out. It's just not responding and I think it's because of the java.

---

### Post by nalmeth on 2006-01-10
If you think Java is the problem, try automatix to install the right version. It's much easier than following other howto's:

[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

---

### Post by CarlosinFL on 2006-01-11
Yes, I am 99% sure that the problem is having the right version of Java on my machine. Let me try the suggested above.

Thanks!

---

### Post by cutOff on 2006-01-11
Try that

```
sudo update-alternatives --set java /usr/lib/j2re1.5-sun/bin/java
```

---

### Post by Lord Illidan on 2006-01-11
Ares also works with wine

---

### Post by slux on 2006-01-11
[QUOTE=ronmarley1]Automatix will install DC++ amule and Limewire.  Frostwire too, which is a GPL clone of Limewire.[/QUOTE]

Eh... The point of my previous post was that Frostwire is just a Limewire ripoff. **Limewire IS GPL** and that's what makes Frostwire possible in the first place and it's a completely unnecessary fork.

---

### Post by MaX on 2006-01-11
Freeloader is a nice bittorrent client for GTK.

Very nice, allows for specifying ports to get outside the firewall.

---

### Post by maaloxx on 2006-01-13
[QUOTE=Carlwill]Yes, I am 99% sure that the problem is having the right version of Java on my machine. Let me try the suggested above.

Thanks![/QUOTE]
Go to the terminal and type limewire and vcut and paste the error.

---

### Post by cb951303 on 2006-01-13
[QUOTE=slux]Eh... The point of my previous post was that Frostwire is just a Limewire ripoff. **Limewire IS GPL** and that's what makes Frostwire possible in the first place and it's a completely unnecessary fork.[/QUOTE]
why unnecessary? You want to pay for limewire?

---

### Post by Turin Turambar on 2006-01-13
Is there something like SoulSeek for Linux? I need a program like that on Ubuntu! :)

---

### Post by Turin Turambar on 2006-01-16
Ok, I found it - Nicotine!! Looks even better than SoulSeek on XP! :)

---

