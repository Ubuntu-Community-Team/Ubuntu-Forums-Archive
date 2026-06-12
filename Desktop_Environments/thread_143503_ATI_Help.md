---
title: "ATI Help"
date: 2006-03-12
forum: Desktop Environments
---

### Post by SHodges on 2006-03-12
Before I start, I realize that there are several ATI driver installation threads and that it's probably annoying to have yet another thread started on the topic, but I used search terms as best I could and didn't find a solution, so hopefully I'm not stepping on too many toes here.  Ok, I downloaded the Xorg version drivers from ATI's website, did the sudo sh stuff in the terminal, got the installer to come up and all that, and got the installer to install all the stuff, I assume no problem because it never gave me any sort of error message, I looked over the html release notes, exited, and then tried to run the aticonfig like it said.  I tried a lot of stuff, like just typing the directory it gave me into terminal and also sudo, but those usually just gave me "no file/directory" messages, but I finally got "sh /usr/X11R6/bin/aticonfig --initial" to give me something that makes me think I'm at least on the right track, but I'm a complete linux newb right now and don't really know what all this sh/sudo/apt-get stuff does for me beyond a very basic understanding, so I don't know.  Anyways, when I put "sh /usr/X11R6/bin/aticonfig --initial' into terminal, I get this message:
/usr/X11R6/bin/aticonfig: /usr/X11R6/bin/aticonfig: cannot execute binary file

So, where do I go from here?


[IMG]http://i3.photobucket.com/albums/y100/jcdenton1558/ATIDrivers.png[/IMG]

There's a screenshot of everything if that helps any.  Thanks for any assistance.

---

### Post by Jaimolistico on 2006-03-12
You can install the ATI drivers of the repository and type in a terminal "fglrxconfig". Follow the instructions and the ATI card is configured! It runs for me (I have a Radeon X300).

---

### Post by SHodges on 2006-03-12
[QUOTE=Jaimolistico]You can install the ATI drivers of the repository and type in a terminal "fglrxconfig". Follow the instructions and the ATI card is configured! It runs for me (I have a Radeon X300).[/QUOTE]
How do I install the drivers from the repository?  I'm not very experienced with Ubuntu, I haven't really been using it for that long now.

---

### Post by dicecca112 on 2006-03-12
post your xorg.log and xorg.conf.  I never launched the .run with the sh command.  I just launched it with sudo.  Best guide is to follow this one [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584).  But after you do all that it won't work.  then you open a terminal type sudo aticonfig, and there will be a bunch of code there, you pick your display, singal, dual, etc, and type sudo aticonfig --(whatever aticonfig settings you picked) and it should say adding fglrx something or other to xorg.conf.  then launch fglrxinfo from terminal and it should say ati and not mesa

---

