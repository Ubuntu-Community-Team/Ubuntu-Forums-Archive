---
title: "Random FF &amp; TB Crashes"
date: 2009-02-28
forum: General Help
---

### Post by garbetjie on 2009-02-28
Hey all.

I've been experiencing some rather annoying and weird issues lately, pretty much only with my Firefox and Thunderbird installations. I'll try to outline the issues:

**Thunderbird:**
There are one or two specific emails that seem to make Thunderbird crash. It is literally as though I'd issued a "kill PID" command on it. No warning, no Quality Feedback Agent. It just dies. Strange this is, is that it only seems to happen on specific emails. It's only happened on two emails so far, both of which were from two different people. On one of the emails, I can view other emails from the same sender, and they don't cause the client to crash.

**Firefox:**
Thie first issue happened today, as I had clicked a link that opened another window which was about to open up the "Print Page" prompt. I saw the window open, and before any of the data was loaded, it crash. The entire Firefox process. I normally wouldn't be that phased if it was Firefox crashing, but this seems like it *could* follow in the same vein as Thunderbird.

So, I was basically wondering whether anyone else has experienced the same issues? If so, have you managed to fix these issues (and if so, how)?

For the record, I'm running the latest versions of Firefox (3.0.6) and Thunderbird (2.0.0.19), each of which do have some plug-ins installed. My OS is Ubuntu 8.10, with all the latest security releases and recommended updates installed.

Cheers,
Geoff

Edit: Trying to access the same page (that caused Firefox to crash), although from a different location, it works correctly, and Firefox didn't crash. O_o

---

### Post by jman6495 on 2009-02-28
hi
i have the same problem!
what version of ubuntu have you got?
i am running jaunty

---

### Post by Mayfairy on 2009-02-28
It occasionally happens to me when using Firefox. 
Sometimes when I'm opening a page and sometimes when I'm out of computer and my screen is locked, so no one can use it. 
When I'm witnessing the issue it's always on new page loading, or refreshing an old page. Apparently when I'm away from the computer it happens cause of the page reload. 
I have loads of tabs (about 10) open at all times. The only self-refreshing page I know of would be my Facebook account. 

This doesn't bother me too much cause I'm using Tab Mix Plus crash recovery function. It always brings back my tabs like they were at the time of the crash. 

Earlier I used to use the built-in crash recovery that nearly half of the time created a crash loop where FF crashed right away when it was loading the tabs. I could recover FF again only by choosing a new session, where I lost all the tabs I had open, which was a major pain cause I never remembered which tabs I had open.

---

### Post by garbetjie on 2009-02-28
I'm running Intrepid Ibex (8.10). So everything *should* be stable. My guess is that it could just be a deadly mix of plug-ins. I don't know whether it would be the actual OS that would be causing the issues. I suppose I *could* always do a re-install, although I'm not particularly excited at that prospect.

---

### Post by Rackstar on 2009-02-28
Hey,

I just posted a thread about experiencing random crashes with FF, TB and evolution. Maybe the same problem? (No answer yet)

[http://ubuntuforums.org/showthread.php?t=1082809](http://ubuntuforums.org/showthread.php?t=1082809)

Ruben

---

### Post by Tanker Bob on 2009-02-28
I have experienced seemingly random Thunderbird crashes for some time. It seems to be related to calendar updates in Lightning through Provider for Google calendar, but its hard to say because the program is always in the background when it fails. Same death as described - like I killed the process. Are you using Lightning and Provider for Google calendar?

I used to have a lot of Firefox crashes, but they always seemed related to the Flash plugin. Can't absolutely swear to it, but it hasn't crashed since the plugin updated a while back.

---

### Post by garbetjie on 2009-03-02
@Tanker Bob: I have the Lightning plug-in for Thunderbird, but I'm not using the Google Calendar provider.

Something that is rather interesting that I have just managed to pick up. I *sort of* received another email from one of the people who managed to make TV crash last time. The thing is, this email was actually forwarded (inline) from *another* person. I managed to open the mail fine, but as soon as I scrolled down to the part that was from the problematic person, TB crashed.

I'm starting to get the feeling that it might actually be something to do with the sender's mail, and/or the contents thereof. Thoughts?

---

### Post by Tanker Bob on 2009-03-02
@ garbetjie: Maybe something like it. I have been paying more attention and noticed that after I start up Thunderbird after a crash, there's a new email in the box. But, I had no opportunity to ever open it before the crash.

---

### Post by garbetjie on 2009-03-03
Another day, another crash. Same thing happened - opened another email, and as soon as it was opened - whether in the preview pane, or in fullview, TB crashes.

I can't even open up the email to view the message's source - I can never get into the email :(

---

### Post by kris1351 on 2009-03-05
My Thunderbird started randomly crashing about every 30 seconds yesterday after a system update. Any fixes out there?

---

### Post by jman6495 on 2009-03-19
Ohh... The Gimp to now!

---

### Post by Rackstar on 2009-04-12
Got it!

Had to disable WINS resolution in Samba.

See my blogpost for more information:
[http://ninetynine.be/blog/2009/04/fix-random-crashes-firefox-thunderbird-and-evolution-on-ubuntu-810/](http://ninetynine.be/blog/2009/04/fix-random-crashes-firefox-thunderbird-and-evolution-on-ubuntu-810/)

---

### Post by Tanker Bob on 2009-04-12
> **Rackstar said:**
> Got it!

Had to disable WINS resolution in Samba.

See my blogpost for more information:
[http://ninetynine.be/blog/2009/04/fix-random-crashes-firefox-thunderbird-and-evolution-on-ubuntu-810/](http://ninetynine.be/blog/2009/04/fix-random-crashes-firefox-thunderbird-and-evolution-on-ubuntu-810/)

Thanks for the tip, but I don't have Samba installed. Still have random crashes in Thunderbird, though.

---

### Post by FabriceV on 2009-07-19
Same problems. Evolution and Firefox crash extremely frequently. Sometimes, some applets crash few seconds later (trash, system monitor...). The logout can break too, with a later complete desktop freeze and I do not arrive to reboot with keyboard.
I use Intrepid, Jaunty was even more buggy, so I have retrograded... But now internet applications are unusable.

---

### Post by FabriceV on 2009-07-20
Apparently, as long as I did not launch Evolution, Firefox did not crash. Even so Evolution did not crash I later have got Firefox crashes. In my case, the problem seems directly related to Evolution... But why Firefox is able to crash because of Evolution...

I will try to remove completely evolution and reinstall it...

---

