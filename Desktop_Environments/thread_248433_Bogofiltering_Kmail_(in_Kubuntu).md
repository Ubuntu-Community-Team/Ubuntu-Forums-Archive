---
title: "Bogofiltering Kmail (in Kubuntu)"
date: 2006-09-01
forum: Desktop Environments
---

### Post by Hoary on 2006-09-01
Hello, I'm a newbie. So I'm not utterly stupid, just utterly ignorant. (Still, feel free to insult me.)

I have to use the email account provided by my employer, which doesn't believe in such fripperies as spam filtration. I'm deluged by offers from Russian pornographers, Japanese dating clubs and the like. I used to use Mozilla's email client, which did a mediocre job of spam filtration; much better than nothing. Of course I deleted all the trash before I installed Kubuntu: it hadn't occurred to me that it would be useful in any way.

So here I am, new to Kubuntu and newly using Kmail. I followed the "Anti-Spam Wizard". I believe that Bogofilter is now turned on. Certainly every incoming message has a Bogofilter score attached. Trouble is, it's a uniform 52%. I tentatively infer that Bogofilter is ready to start up but hasn't learnt anything. man:bogotune talks of feeding the program a pile of spam and a pile of non-spam: I have loads of non-spam and three days from now I'll have a pile of spam as well. Is this the thing to do?

Kmail's help seems to be Kontact's help, which doesn't say anything useful that I can see. Kmail does have a button marked "Filter Classify as spam" and I've used it for all spam since I noticed it a couple of hours ago; either this does nothing or it hasn't yet reached some initial threshold, as all messages (from friends, colleagues, Canadian drug-pushers) are still 52%.

I'm leaving for a two week vacation a few days from now and if I don't get this fixed first my mailbox will be a real nightmare when I return!

---

### Post by mjm115 on 2006-09-07
I am having the same exact issue with Kontact and Kmail.  I too have ran the Anti-Spam wizard with no success.  I am switchting over from super slow evolution and I am not interested in Thunderbird, as I need the PIM capabilities.

I have also followed the tutorials from the following sites with no success:

[http://david.jamesnet.ca/kde/kmail_bogofilter.html](http://david.jamesnet.ca/kde/kmail_bogofilter.html)
[http://kmail.kde.org/unsupported/bogofilter.txt](http://kmail.kde.org/unsupported/bogofilter.txt)
[http://www.techforce.com.br/index.php/news/quem_somos/linux/mini_how_to_kmail_and_bogofilter](http://www.techforce.com.br/index.php/news/quem_somos/linux/mini_how_to_kmail_and_bogofilter)

These offered no assistance whatsoever.  I do have bogofilter installed, and I have all updates.

Any assistance would be appreciated.

---

### Post by editrix on 2006-09-07
Because my bogofilter is working, it's hard to say what's wrong. But I do know that you have to set 2 filters to get it to work.

First, in Configure Kmail, in your account settings, there's a box that says:

Filter messages if they are greater than ... (the default is 50000 bytes, which I've left as is.)

Make sure this box is ticked, because this tells Kmail to use your filters. i.e., none of the filters will work if it isn't ticked.

Then, in your filter rules, make sure the first 4 filters are the bogofilter ones:

Bogofilter check
Spam handling
Classify as spam
Classify as NOT spam

Then, of course, you have to teach Bogofilter. So you have to manually move spam to a spam folder, and when you have maybe 100 in there, run the Bogofilter manually on it. Do this a few times (new spam every time).

---

### Post by mjm115 on 2006-09-08
Thanks,

but for some reason, it automagically started working.

---

