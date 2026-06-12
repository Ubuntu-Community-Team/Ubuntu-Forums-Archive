---
title: "Two problems, one of them related to Dell."
date: 2007-06-17
forum: Dell  Ubuntu Support
---

### Post by FoxboyJT on 2007-06-17
I run Kubuntu, (GNOME hates me).

The problem I'm having with my Dell Inspiron E1505, is that the mediabuttons don't work. I *need* the volume control. Help please?

And the next problem I have.
One of my friends thought it would be funny, to use my allready-root Konsole, and type "deluser root" several times, and now I can't fix anything. Can I get help with that too please?

NOTE: I still have a root Konsole open

---

### Post by HermanAB on 2007-06-17
Howdy,

1. Volume - use the Kmix application to change volume.  Getting the media keys to work will require some effort, but you'll need to google for solutions.
2. To get your system to work properly again - simply re-install Ubuntu without formatting the /home partition.  You do have a separate /home partition right?  If not, now you know why you need a separate /home partition...
3. Give your 'friend' seven lashes with a wet noodle.

Cheers,

Herman

---

### Post by FoxboyJT on 2007-06-17
Isn't there some other option? It was a pain to install Kubuntu.

---

### Post by HotShotDJ on 2007-06-17
All I can offer is that on my Dell E1505 with Kubuntu, all the media keys work with no additional tweaking from me.  Even the MediaDirect button works -- it opens AmaroK.  I did NOTHING to cause this behavior.  It was the default upon installation.  And I agree with previous poster... except I'd forget about the wet noodle... I'd destroy him completely!  You can go into a recovery console (reboot, press esc when "GRUB" appears, choose recovery option from the Grub menu) and add your username using the command line (I've always used kuser to do this, so I don't know the specifics).  You'll also have to manually add the new user to various groups.  Unless you know what groups Kubuntu sets up for the first user by default (I sure don't) you'll have a difficult time restoring thing back to good without doing a full reinstall.

---

### Post by FoxboyJT on 2007-06-17
Well, it wasn't my user account, it's the one that's hidden from the user and is there for sudo/su. And it had it's own group. Meh, this is just such a pain. Thanks though.

---

### Post by HermanAB on 2007-06-18
If the root account is messed up, then re-installing is the easiest way to recover - believe me, simple advice coming from an old greybeard...

Cheers,

Herman

---

### Post by daller on 2007-06-18
About the mediabuttons, you can use keytouch to configure them...

Install it, and the editor:

```
sudo apt-get install keytouch keytouch-editor
```

...But I really think you should reinstall first!

---

### Post by HermanAB on 2007-06-18
Other key configuration utilities are xbindkeys and hotkeys.  Each has its strengths and weaknesses.  Hunt them down and read some about them, those things are easy to use and it can be very satisfying to hook your 3 or so often used applications to some unused function keys, so you can fire them up with a single key press.

I could only vaguely remember about them so I searched for 'keys' and la voila.

Cheers,

Herman

---

### Post by Gadren on 2007-06-20
I just wanted to post and say that I had a similar problem, and that keytouch worked amazingly well... a very smart piece of software.

---

