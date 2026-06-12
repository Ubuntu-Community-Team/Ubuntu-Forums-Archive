---
title: "Xbox 360/Ushare guide help"
date: 2009-05-04
forum: General Help
---

### Post by rdmike on 2009-05-04
Hi,

I am trying to follow this [guide]("https://help.ubuntu.com/community/Xbox360Media") to set up Kubuntu to work with my xbox360. 

So everything is going fine until I get to step #5 "Create a package and install." I am told to enter the command "sudo checkinstall -D make install" but when I enter that command in the terminal I get this error message "sudo: checkinstall: command not found."

So, my question is; how do I proceed from here?

---

### Post by Kaneda187 on 2009-05-05
You proceed to download and install twonky media! its great! 

Download version 5.0.55 from here
[http://www.twonkyforum.com/unsupported/5.0.55/]("http://www.twonkyforum.com/unsupported/5.0.55/")

then follow the guide here
[http://scrambled.wordpress.com/2008/01/06/howto-stream-music-pictures-and-movies-to-an-xbox-360-with-linux/]("http://scrambled.wordpress.com/2008/01/06/howto-stream-music-pictures-and-movies-to-an-xbox-360-with-linux/")

hope it works! worked great for me!

---

### Post by prem1er on 2009-05-05
> **Kaneda187 said:**
> You proceed to download and install twonky media! its great! 

Download version 5.0.55 from here
[http://www.twonkyforum.com/unsupported/5.0.55/]("http://www.twonkyforum.com/unsupported/5.0.55/")

then follow the guide here
[http://scrambled.wordpress.com/2008/01/06/howto-stream-music-pictures-and-movies-to-an-xbox-360-with-linux/]("http://scrambled.wordpress.com/2008/01/06/howto-stream-music-pictures-and-movies-to-an-xbox-360-with-linux/")

hope it works! worked great for me!

+1 for this. Twonky was great for me, although I don't think it is free anymore?  My roomate just bought a Popcorn Hour for all my media/TV needs now.  If you have an extra 200 bucks I suggest that.

---

### Post by askreet on 2009-05-05
I have the ubuntu distro's ushare working right out of synaptic.  For whatever reason editing the config and setting Xbox to TRUE doesn't work, you have to edit the /etc/init.d/ushare script and add the --xbox option to the startup... then it works pretty decent.

Maybe this helps you?

---

### Post by ronniet on 2009-05-10
> **askreet said:**
> I have the ubuntu distro's ushare working right out of synaptic.  For whatever reason editing the config and setting Xbox to TRUE doesn't work, you have to edit the /etc/init.d/ushare script and add the --xbox option to the startup... then it works pretty decent.

Maybe this helps you?

The Xbox option had me foxed for AGES. You _must_ put a lowercase 'yes'. **NOT** 'YES'. Took me **AGES** to figure that out!  :D

---

### Post by rdmike on 2009-05-17
The other step might help once I get things properly installed but we're not to that point yet. I cannot get past step five in this guide. How do I get through the process of installation?

---

### Post by rdmike on 2009-05-18
Any idea why when I get to step #5 "Create a package and install." I am told to enter the command sudo checkinstall -D make install" but when I enter that command in the terminal I get this error message "sudo: checkinstall: command not found?

---

### Post by rizman on 2009-05-18
> **rdmike said:**
> Any idea why when I get to step #5 "Create a package and install." I am told to enter the command sudo checkinstall -D make install" but when I enter that command in the terminal I get this error message "sudo: checkinstall: command not found?

You are probably missiong the checkinstall package.

Follow instructions on [this]("http://ubuntuforums.org/archive/index.php/t-153734.html") link to get checkinstall

---

### Post by rdmike on 2009-05-27
Thanks rizman for the checkinstall link, that worked.

Now, I may be daft but ut appears, in looking at the documentation that I have to have a cet5 running straight from my computer to my xbox? In windows I was able to access my xbox360 via the network. (I'm plugged into a linksys router)

---

