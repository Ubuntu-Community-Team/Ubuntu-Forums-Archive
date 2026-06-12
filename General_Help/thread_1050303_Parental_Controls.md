---
title: "Parental Controls"
date: 2009-01-25
forum: General Help
---

### Post by oneadvent on 2009-01-25
I am a computer guy, and recently I have been going to...less reputable sites, so anyway, at this point I have had my wife change all the passwords and make a very basic acct for me, which only she has the password for.

Now that you have accepted that above, what my question is:

Is there parental control software for Ubuntu that is so good that I couldn't find a way around it. I know how to use proxys and I know how to lookup ip addresses and turn off processes (although I dont know if I can do that without knowing my password.) I want to be totally locked out of any sites that aren't "good."

Thanks.

---

### Post by adamlau on 2009-01-25
Ask David Duchovny :) . What prevents you from booting into live media (Ubuntu, Slax, et al.) and continuing going about your old ways? Nothing. You are your best parental control.

---

### Post by oneadvent on 2009-01-25
Humm, good point...

I will have her destroy those disks...it would take too long to download another, and my head would clear by then.

I also thought about going to recovery mode, but I would have to change the password for that to work, so I'm clear on that.

I'm sure there would be a way with windoze, so there should be a way with good ol' linux.

---

### Post by mb_webguy on 2009-01-25
When it comes to computers, anything that can be done can be undone, broken, or bypassed.

There are various extensions (and combinations of extensions) in Firefox that can prevent the user from accessing certain websites, but those extensions can be disabled, or the user can create a new profile or else use a different browser.  If no other browser is installed, the user can install a new one.  If the user doesn't have the privileges to install new software, he can boot into a LiveCD and use that to browse.  If the computer has a BIOS password that prevents him from booting the computer and thus using a LiveCD, then he can go use a friend's computer...

Ultimately, the best solution for your problem is willpower.  (Though setting a BIOS password might help -- after all, the harder it is to do, the less willpower you'll need to avoid doing it.)

---

### Post by oneadvent on 2009-01-25
Wow you guys aren't helping much.

I do not want ways around security software. I want it to be tough to get to those things.

I mean something like NetNanny for linux.

(The bios password was a good idea though)

---

### Post by Crafty Kisses on 2009-01-25
Here's a couple of things you can try:

[LIST]
[*]Create separate accounts for each kid, they really should never have any type of root access.

[*]You can set your CD-ROM not to boot CD's. You may want to do this if you don't want one of your kids to use the LiveCD and bypass the filters.

[*]You can also set a BIOS password.
[/LIST]
Upon further research, there does appear to be a program/script you can download, look at this thread for more information: [http://ubuntuforums.org/showthread.php?t=843510](http://ubuntuforums.org/showthread.php?t=843510).

---

### Post by sisco311 on 2009-01-25
Well, porn is cool, but take a look at this howto:
[http://ubuntuforums.org/showthread.php?t=843510]("http://ubuntuforums.org/showthread.php?t=843510")

---

### Post by oneadvent on 2009-01-25
Can you install Limewire without admin?

I will check that program out!

---

### Post by mb_webguy on 2009-01-25
> **oneadvent said:**
> Wow you guys aren't helping much.
[...]
I mean something like NetNanny for linux.
I know a 12-year-old who figured out a way around NetNanny in less than an hour.  :)

A common saying in computer security is that the best security is the person in the chair.  You can pretty well lock down a computer from remote access, but if a person has physical access to the computer, there's no "silver bullet" solution to control that user's activities.  You can make it hard for them (and setting up a limited account for the user, installing some IP blacklisting software, adding a password to the GRUB recovery mode option, and adding a password to the BIOS certainly makes it difficult), but as long as someone has physical access to the computer there's no guarantee they won't find some way to do what they want to do.

And in your specific case, by addressing the ways around certain precautions, we can address further precautions to take until we get to the point where you will feel comfortable using your computer without the temptation to do things you feel you shouldn't.

---

### Post by oneadvent on 2009-01-25
Is there a place to get a list of "blacklist" sites, so that it can be added to a program.

For instance, hidemyass.com lets you use them as a proxy, and so does other sites, probably more than a hundred.

There are other sites like 4chan.org that isn't necessarily "bad" but should be blocked too.

I'm going to have my wife do the managing, so its gotta be something that she can keep up to date without spending forever.

---

### Post by mb_webguy on 2009-01-25
You might want to check out the [ProCon Latte]("https://addons.mozilla.org/en-US/firefox/addon/1803") extension for Firefox.  I considered it a year or so ago for a system I was putting together for my nephew, but discarded it because it was easy to disable.  However, they've now added the ability to remove it from the Tools menu, to lock out the Firefox Add-ons menu, and even to lock the about:config page.  While I can still think of two or three ways it can be bypassed (which I won't tell you unless you ask), it's otherwise pretty solid.  

Of course, it only applies to Firefox, and not other methods of accessing the web...  For a more comprehensive solution, you may want to consider something like [OpenDNS]("http://www.opendns.com/").

---

