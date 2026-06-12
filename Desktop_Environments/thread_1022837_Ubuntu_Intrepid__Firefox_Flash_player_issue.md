---
title: "Ubuntu Intrepid / Firefox Flash player issue"
date: 2008-12-27
forum: Desktop Environments
---

### Post by arepaking on 2008-12-27
Hello Experts,
I have found several websites that will not play their flash movies. All I got is a black square that does not load the movie to play.

For example, the following websites does not work:
1) Qik websiste ([www.qik.com](www.qik.com)) does not work with my Firefox. 
2) http://elfyourself.jibjab.com[/url] does not work either.
3) Weather Channel: [www.weather.com](www.weather.com) (The Radar Map does not work, the rest seems to work fine)

Does anyone knows how to fix this?

As a side note, I am able to play movies from YouTube. And I have installed Flash Player 10.

Thanks in advance for your support.

Kind Regards,
AK

---

### Post by howefield on 2008-12-27
Not much help other than to say, all three websites play for me, I'm using a bog standard 32 bit install with ubuntu-restricted-extras to get flash.

---

### Post by Hydrid on 2008-12-27
Try firefox in its safe mode or Uninstall your firefox and flash player and install them again.This worked for me

---

### Post by jonboy99 on 2008-12-27
I had similar issues and discovered old versions of flashplayer all over the place.  I ended up deleting any versions of libflashplayer.so from my system 
```
locate libflash
``` should find them.
I then went to the package manager and uninstalled both flashplayer 9 and 10, and then deleted my .mozilla folder in my home folder.
I then went back to the package manager, and reinstalled flash 10, which sorted it.

---

### Post by arepaking on 2008-12-28
> **jonboy99 said:**
> I had similar issues and discovered old versions of flashplayer all over the place.  I ended up deleting any versions of libflashplayer.so from my system 
```
locate libflash
``` should find them.
I then went to the package manager and uninstalled both flashplayer 9 and 10, and then deleted my .mozilla folder in my home folder.
I then went back to the package manager, and reinstalled flash 10, which sorted it.

Hi!
Thank you very much for your reply.
I have to admit that I am a noob using Ubuntu. Would you mind detailing a little bit more about the steps to perform?

For instance, after executing the "locate" command; how should I delete the libflash? 

Should I manually delete the .mozilla folder? how this folder will be create again?

Thank you so much for your clarification and guidance.

Kind Regards,
AK

---

### Post by jonboy99 on 2008-12-28
Personally I run nautilus as root, typing 
```
gksudo nautilus
```

However I am very much a linux amateur myself, and many will tell you you risk your system using nautilus as root like that as you have power to delete anything and screw up your system, so perform at your own risk!  A probably safer alternative would be navigating manually to the files using the terminal and use
```
sudo rm *filename*
``` for each file.


As to deleting the .mozilla folder, do it manually using the same methods as above.  It will wipe all your firefox settings, but be recreated by firefox next time you run it.  If it doesn't, simply reinstall firefox using the package manager. .mozilla is a hidden folder, bear this in mind if you can't see it, and choose 'show hidden files' from nautilus.

If you are very unsure as to whether you are deleting the right files, post up the the results of the locate libflash command, and ask.  libflashplayer.so in various locations is what you are after, possibly some others.

---

### Post by arepaking on 2008-12-28
Hey! Thanks again.

I did: locate libflash and I came up with this results:
```

/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/openoffice/basis3.0/program/libflashli.so
```

Should I delete both files? The other one seems to be part of openoffice.

One more thing,
Using the Synaptic Package Manager, I was able to find the Flash player 10 (flashplugin-nonfree) and uninstall it. Now, I went to youtube for example and I notice that the flash player 9 is installed but I cannot find it with the Synaptic. That being said, I was able to reproduce flash movies but with no sound.

How can I uninstall the flash player 9?

---

### Post by jonboy99 on 2008-12-28
Yep, leave the open office one, get rid of the other.

I can't find flash 9 in the repos for intrepid.  In Hardy (IIRC) flash 9 was in the flashplugin-nonfree and flash 10 was in the adobe-flashplugin package but they are both flash 10 in my intrepid.
I would delete the libflashplayer.so file you've found, then load firefox and go to youtube or somewhere to make sure flash ISN'T working.  Once you have confirmed this, go back to the repos, install flash 10 with either of the above packages mentioned (but only one of them), then see if flash is working.

---

### Post by arepaking on 2008-12-28
Issue Resolved!

I think what it was causing this issue was a firefox add-on called: NoScript.

I followed your instruction until deleting the .mozilla folder, after doing this the settings of NoScript was deleted as well and the next time I opened qik.com it prompted me about allowing this site or not. I disable this add-on and I was able to see all the website that I mentioned above.

Thank you very much for your help. I couldn't notice this without your support.

Kind Regards,
AK

---

### Post by jonboy99 on 2008-12-28
I think you've hit the nail on the head there.  I suspect that's been what's sorted it for me in the past too, I just never bothered reinstalling noscript after upgrading flashplayer.

Karma.  :)

---

