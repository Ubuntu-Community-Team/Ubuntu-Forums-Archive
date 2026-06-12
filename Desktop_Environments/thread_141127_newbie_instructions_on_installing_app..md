---
title: "newbie instructions on installing app."
date: 2006-03-07
forum: Desktop Environments
---

### Post by diggaboy on 2006-03-07
[SIZE="3"]I[COLOR="Blue"][FONT="Comic Sans MS"]I have my breezy system up and running. I want to un rar a movie I downloaded. Can i use synaptic manager to get a app. that will do this for me? i searched in synaptic manager using rar,decompress, unzip etc. and found no apps to install. i then found one on the net called Archive and downloaded it to my desktop. i un zipped it and read the readme file. It says under Quick Start " type this ($ is the shell prompt): "
                                                                          " $ ./install.sh"
 I am at a loss as how to continue. any help will be appreaciated . thanks diggaboyhttp://ubuntuforums.org/images/smilies/confused.gif[/FONT][/SIZE][/COLOR][/SIZE][/SIZE[/SIZE]]

---

### Post by chimera on 2006-03-07
umm, yeah, believe me, no matter how cool it looks, using default font, size and color is still more readable than fancy font undersized blue stuff you managed to create...

since synaptic didn't find anything, did you enable any extra repositories? (if not, don't make another thread on how to do it, just search the forums for "enable extra repositories breezy", it's been ansewered hundred times over)

As for playing the movie, you'll need to install win32codecs (availible in the extra repositories), and a movie player like xine+xine ui(ditto). Oh and good luck with ubuntu, don't give up yet!

oh and the "$ ./install.sh" thing, you're supposted to type that in the terminal (which you can get in applications->accesories->terminal menu), and you don't type the $. Although you won't need it now if you enable the extra repositories, it comes in handy lots of times. I'd recommend you to learn how to use it (again, search forums+google)

---

### Post by diggaboy on 2006-03-07
Thanks for the quick answer. Could you suggest an app. to unzip rar. files? thanks again.

---

### Post by Garyu on 2006-03-07
I don't remember the forum, probably absolute beginner talk, but there is a sticky somewhere about a script called Automatix. You should get this and install it. The instructions are very easy to follow.

Automatix will install rar tools for such archives, as well as codecs for movies, MP3-music and DVDs. It is also an easy way to install some applications like wine (which will make you able to install and run windows-software in linux).

---

### Post by akiro.yamamoto on 2006-03-07
If I remember correctly, after you enable the extra repos. in Synaptic search for rar.
When you install that, it will provide support for rar Archives in the Archive Manager
(Applications >> Accessories >> Archive Manager) or just double click on the file you downloaded. That should do the trick.

---

### Post by diggaboy on 2006-03-07
thanks to all , diggaboy

---

### Post by Sutekh on 2006-03-07
Follow this link to enable the universe/multiverse repositories

[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

Then install the unrar packages
```
sudo apt-get update
sudo apt-get install unrar-nonfree
```

---

### Post by deathbyswiftwind on 2006-03-07
Id recommend automatix [http://ubuntuforums.org/showthread.php?t=80295](http://ubuntuforums.org/showthread.php?t=80295) super easy to use and then he can also have all the codecs and everything else

---

### Post by stanz on 2006-04-05
[quote=akiro.yamamoto]When you install that, it will provide support for rar Archives in the **Archive Manager**
(Applications >> Accessories >> **Archive Manager**) or just double click on the file you downloaded. That should do the trick.[/quote] Hi All...
Question::
I downloaded the '[Checkinstall]("http://asic-linux.com.mx/%7Eizto/checkinstall/download.php")', from the site, 
I decided to try to *"open/save"* with default option: [B]open with: Archive Manager
[/B]Figuring i should try to learn what that's all about.
I soon learnt- i have no clue, where to *"save/extract"* such a "*file/program"* !?
Any help or advice would be a lesson learnt, for me!!
Thanks...

---

### Post by Sutekh on 2006-04-05
[QUOTE=stanz]Hi All...
Question::
I downloaded the '[Checkinstall]("http://asic-linux.com.mx/%7Eizto/checkinstall/download.php")', from the site, 
I decided to try to *"open/save"* with default option: [B]open with: Archive Manager
[/B]Figuring i should try to learn what that's all about.
I soon learnt- i have no clue, where to *"save/extract"* such a "*file/program"* !?
Any help or advice would be a lesson learnt, for me!!
Thanks...[/QUOTE]
Which version of Checkinstall did you download?

The source code? The .rpm? The .deb?

 - If the source code then you can extract it to a folder on your desktop (for convenience) and then follow the instructions for installing source in this link

[http://www.psychocats.net/ubuntu/installingsoftware.php](http://www.psychocats.net/ubuntu/installingsoftware.php)

 - If you downloaded the .rpm or the .deb, **quit** the archive manager and the follow the instructions in that link.

---

### Post by stanz on 2006-04-06
Hi All.. Hey Sutekh... Here's the version & link.

**_[[COLOR=#5F2D06][B]**[/COLOR]]("http://www.ubuntuforums.org/member.php?u=46914")_[/B]Debian binary package:                 [checkinstall_1.6.0-1_i386.deb]("http://asic-linux.com.mx/%7Eizto/checkinstall/files/deb/checkinstall_1.6.0-1_i386.deb")

Thanks for the link- a good bookmark! 
I guess i was thrown off, by AManager & its option, feeling its default actions "install & place", the perticular file. 
Also, I'm reading the 'README's', and follow instructs...of course having doubts
& not totally sure of things.
I suppose i'll take 'em out of usr/lib & usr/share/bin, where i placed 'em!
Thanks again!

---

