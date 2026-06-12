---
title: "Inspiron Mini 9 - Flash 10"
date: 2009-01-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Solange82200 on 2009-01-20
Hi UGm6hr, can you help me with something similar? I have a Dell Mini 9 with Ubuntu and am trying to upgrade to Flash 10, to see if it helps my choppy video problem when streaming online video. Anyway, no matter how many times I install Flash 10, when I go to about : plugins, it says that this Flash 9 is installed:    

File name: libflashplayer.so
    Shockwave Flash 9.0 r152

Can you give me the code that I should type into Terminal, that would force my Mini to use Flash 10 instead? Thanks a million

---

### Post by ugm6hr on 2009-01-21
I am afraid this is a completely different issue - hence I have started a new thread for you.

I have never installed Flash 10 successfully, so can't help.

All I can suggest is trying to remove Flash 9, then reinstalling 10; however, while I have previously installed Flash 9 manually from the Adobe website, I have had less luck with 10.

---

### Post by Solange82200 on 2009-01-21
Thanks for the fast response. How do I remove Flash 9 though? I'm very new to Ubuntu, and it seems like a lot of things require typing code into Terminal or something...

Edit: I thought about what you said, and I thought maybe I can go into Synaptic Package Manager and delete it? I did a search for Flash in there and I think I found it. It says flashplugin-nonfree, and in description says Adobe Flash Player. Im a little scared to delete it though, what if I can't get 10 on, then I may be stuck with no flash player...

---

### Post by ugm6hr on 2009-01-21
> **Solange82200 said:**
> It says flashplugin-nonfree, and in description says Adobe Flash Player. Im a little scared to delete it though, what if I can't get 10 on, then I may be stuck with no flash player...

That's the one: flashplugin-nonfree

Or you can remove with Terminal:
```
sudo apt-get purge flashplugin-nonfree
```

If Flash 10 doesn't work any better, you should be able to reinstall with:
```
sudo apt-get install --reinstall flashplugin-nonfree
```

That should remove Flash 10 (if it is installed) - but I have to say I've never done that.

Perhaps if you tell us what online video that you find choppy to see whether it is the same for me?

---

### Post by Solange82200 on 2009-01-21
Thanks Ugm6hr, I am going to try what you mentioned. In case you have a moment, here are some of the videos my son has had trouble viewing:

[http://tailedfox.com/page-naruto-shippuden-92](http://tailedfox.com/page-naruto-shippuden-92)

It is watchable, but it stutters. I have a super crappy work laptop, not sure what it's specs are, but they play fine on it. Mind you, I understand that a netbook isn't going to have the power of a laptop, but since I've seen some people saying they have no problems watching stuff, I figured I'd try to fix it...

Edit: Good news and bad news. Taking off Flash 9 worked, I was able to get Flash 10 on there. The bad news is that now videos appear even MORE choppy. Im not sure if it has to do with Flash, or maybe because Im on internet network at work, but it is looking horrible. I think I may just change back to flash 9...

---

### Post by Solange82200 on 2009-01-21
Yikes, now Im having problems getting the original flash reinstalled. I put the codes in Terminal that you said, and it gave me this long speech about how it was reinstalling it, and it even said it was succesful, but then afterward, when I went into "about : plugins", it still shows Flash 10....

---

### Post by ugm6hr on 2009-01-24
OK.

I'm afraid I haven't installed Flash 10 (I don't want it), so you'll have to do some of the searching yourself.

Look in /usr/lib/ for firefox, firefox-3.0, firefox-3.0.5, flashplugin-nonfree and find all instances of libflashplayr.so and delete them all (you will likely have to do this with "gksudo nautilus").

Then try installing Flash 9 again with the command as previously.

Flash 9 appears to install in /usr/lib/flashplugin-nonfree, while I suspect Flash 10 is in one of the other directories somewhere; hence the reason why Flash 9 doesn't reinstall over the top of 10.

---

### Post by Cowchip7 on 2009-04-21
I see that Adobe Flash 10 is now in the Dell Mini repositories. Is it worth upgrading from Flash 9?

---

### Post by anjilslaire on 2009-04-21
Not using Dell Ubuntu, but I've gotten much better performance on all of my systems using FLash 10 compared to 9, including my Mini 9 and an Inspiron 1420.

---

### Post by Cowchip7 on 2009-04-21
> **anjilslaire said:**
> Not using Dell Ubuntu, but I've gotten much better performance on all of my systems using FLash 10 compared to 9, including my Mini 9 and an Inspiron 1420.

Anyone out there have experience with Flash 10 and Dellbuntu? If not, I guess I'll wait for the package manager to tell me to update. :)

---

