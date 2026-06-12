---
title: "Can I run Warcraft 3 from my Windows install thru Ubuntu?"
date: 2007-01-22
forum: Gaming &amp; Leisure
---

### Post by Happy_Man on 2007-01-22
Hi everyone.

I was just wondering if there was any way I could run Warcraft 3 from my existing install directory in my Windows partition from Ubuntu. I don't want to have to uninstall my game just to reload it in Linux, and the game won't accept my key (because it's already been used). Is there any way to do this?

---

### Post by Happy_Man on 2007-01-22
Hello? Is anyone out there?

---

### Post by Shatrat on 2007-01-22
You could try just copying everything from your /mnt/windows/Programblahblahblah to /home/yourname/.wine/drive_c/Programblahblahblah

I've done this in the past with other games and had it work.  I don't think it is a good idea to run the executable while it is still on the windows partition.

note, the path to the original files is probably different on your machine, basically just go wherever you mounted the windows drive.

---

### Post by Mike'sHardLinux on 2007-01-22
I have re-installed WC3 a ton of times and never had a problem. I am still able to play online, too. What do you mean it won't accept your key? What exactly does it say?

---

### Post by Josh1 on 2007-01-22
You will need to export the registry since it hashes your key in there. Should be able to play online after that.

---

### Post by ViperKnight on 2007-01-23
From what I know Warcraft3 doesn't store any useful data in the registry.  The cd-key is actually stored in one of the MPQ game-files much like Diablo II ;)

Several times I just copy the whole Warcraft 3 folder from one computer to the next, without bothering to properly install it and it still works on Battle.Net.

But you should be able to simply run your Warcraft3 installation from where it is in Windows (given that you have your partition set to something readable in both windows and linux).  I use Cedega which works perfectly, except for some odd colours on the videos.

Personally I have a small windows partition, smallish Linux partition and use a huge Ext3 partition to install Windows apps (there's a plugin for XP which allows read/write to ext3/2 which is much safer than using ntfs-3g or similar).  So with this I can actually get to my /home/accountname/.Cedega/Warcraft3installation-here from windows and play the game in windows as well and only need one installation :grin: .

With that I can simply run some windows apps in their installed directories straight off the drive without worrying about several installs just for linux/wine or windows ;)

For the cd-key problem, it's most likely somebody else has either stolen your key, you've given it to somebody else or they just outright guessed it.  If your copy is legal you can contact Blizzard...but they probably wouldn't do much.  Try changing realm (the little globe with a magnifying glass) and you should be able to play ;)

Bit long....but hope I helped.

---

