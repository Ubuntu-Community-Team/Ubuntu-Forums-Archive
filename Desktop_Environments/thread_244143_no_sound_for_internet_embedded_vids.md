---
title: "no sound for internet embedded vids"
date: 2006-08-26
forum: Desktop Environments
---

### Post by johnnyboy on 2006-08-26
Not getting sound for embedded videos on firefox 1.5.0.5.  Run 6.06.  It's nothing hardware related as sound on other stuff works.  Used totem-xine and the sound didn't work.  Switched over to gstreamer with all the required plugins (ffmpeg, ugly, bad, etc.), still doesn't work.  No idea.  Any help much appreciated.

---

### Post by neko18 on 2006-08-26
You're using the Totem Firefox plugin, I assume?

---

### Post by Carbonfish on 2006-08-26
Hi johnnyboy,

You may have already done this, but I found this:   [http://ubuntuguide.org/wiki/Dapper#H...ozilla_Firefox](http://ubuntuguide.org/wiki/Dapper#H...ozilla_Firefox)
instrumental in getting things set up (although I still haven't resolved my RealPlayer sound issue).

Give it a look.  ;)

---

### Post by johnnyboy on 2006-08-26
Yes I am using totem firefox. 

Thanks for the link.  I ran the commands in the terminal and was prompted with a notice verifying that all of the plugins were already updated and installed on my com.  So I really don't know what is going on.

---

### Post by johnnyboy on 2006-08-26
Scratch that.  Thx for the link again carbonfish.  I didn't think that the vids I was watching were flash... I was wrong.  I edited the firefoxrc file (as instructed on the link).  Changed the DSP from "none" to "aoss"... sound now works fine.

---

### Post by rykel on 2006-08-26
> **johnnyboy said:**
> Scratch that.  Thx for the link again carbonfish.  I didn't think that the vids I was watching were flash... I was wrong.  I edited the firefoxrc file (as instructed on the link).  Changed the DSP from "none" to "aoss"... sound now works fine.

Hi, I see no instructions in the UbuntuGuide about editing anything called "firefoxrc"... anyway, I am trying to play sounds from Google Video, ajaxTunes etc.

Any idea?   :confused:

---

### Post by Carbonfish on 2006-08-26
Hi,

I personally haven't tried Google video (I guess I should) but have you followed the above how-to, and if you have and it still doesn't work, perhaps try the Restricted Formats how-to, which you can find here:   [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Try that and see if that helps, otherwise I will have to defer to brighter minds.

KC

---

### Post by rykel on 2006-08-26
I have set up everything properly as far as I can tell...

Anyway, I managed to "solve" the problem by running firefox from a terminal with the following command, "aoss firefox". (which means running firefox with Alsa-OSS)

I am now able to hear flash movies, google video, listen to songs on ajaxtunes.com and baidu.com etc.

HOWEVER, I can only listen to one thing at a time... that is, if I am listening to a google video, my flash movie would go mute.

I hope there is a way to use ESD instead of aoss!

---

### Post by Breeegz on 2006-09-06
<--2nd post
> **Carbonfish said:**
> Hi johnnyboy,

You may have already done this, but I found this:   [http://ubuntuguide.org/wiki/Dapper#H...ozilla_Firefox](http://ubuntuguide.org/wiki/Dapper#H...ozilla_Firefox)
instrumental in getting things set up (although I still haven't resolved my RealPlayer sound issue).

Give it a look.  ;)

uhh, which one should I look at in the wiki?  I'm having the same issues (sound works, just not streamed from the internet) , and I couldn't find where I needed to edit some firefox file and what I need to edit it to...

any help would be great...

---

### Post by Goatie on 2006-09-06
I had the exact same problem... and since the link didn't work I just read through most of the stuff in the ubuntu guide about mozilla firefox 'till I found what I was looking for.
All I had to do was install the plugin and update it, then the sound worked.
[click here](ubuntuguide.org/wiki/Dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox) for the solution :)


This is only the second day I'm playing around with Ubuntu 6.06 and I've already learned alot just by reading the manual, the unofficial guide and by searching these forums.

Me heart Ubuntu *giggles*

---

