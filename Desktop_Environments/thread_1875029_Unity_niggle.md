---
title: "Unity niggle"
date: 2011-11-04
forum: Desktop Environments
---

### Post by beacon on 2011-11-04
I used Unity for a short time, then changed to Gnome. However, feeling that I hadn't given Unity a chance, I set it up again when I had to reinstall. I admit to liking it much more now, but I do have a niggle about one irritating feature. It is difficult to go the the arrow to move back one page, without having it obscured by the applications panel (if that is what it is called) which suddenly appears from the side. It takes a good deal of care to go back a page without that unnecessary disruption. I feel the arrow should be placed so that it is not so close to the stimulus for the panel.

---

### Post by BillyBoa on 2011-11-04
Did you try installing the proprietary video drivers?

---

### Post by lynrock on 2011-11-04
I'm guessing that you mean the back arrow on Firefox? It doesn't matter because anything close to the left edge can trigger the launcher. I have problems with the folder triangles in Nautilus tree view.
There are two things you can adjust. If you haven't already, install compizconfig Setting Manager, then find the Unity plug-in. It is possible to change which mouse gesture reveals the launcher, 'top,' 'side' (default) or 'bottom'. Top doesn't seem to work very well at the moment. The other setting is 'edge reveal timeout' which sets how long the mouse needs to be against the edge to trigger the launcher. Personally I'd rather wait half a second when I need it rather than having it pop out when I don't.
Hope this helps.

---

### Post by beacon on 2011-11-04
Thanks very much for both replies. They are much appreciated. I'm not certain I fully understand the advice from Billy Boa, although it is not complicated. It's just my own ignorance. When I go to additional drivers, two items are listed. The first is ATI/AMD proprietary FGLRX graphic driver (post release updates). I tried to activate it, but after some minutes when it seemed to be downloading, or whatever, I was told it couldn't be used on my equipment, even though I have a brand new and up-to-date computer. So I activated the other, (ATI/ADD Proprietary FGLRX graphic driver). Is that what was meant?

I haven't yet had a chance to try lynrock's suggestion, but will as soon as possible. It looks as if it might be just the job, although I wonder about mouse gestures (top, bottom, etc), since I know only left and right click.

Thanks again

---

### Post by beacon on 2011-11-04
Please help. I installed compizconfig setting manager, but now the launcher remains visible, and I can't hide it. Perhaps I should have paid more attention to the critical comments about compiz, as several posters noted that it doesn't work well with 11.10.

---

### Post by typhoon_tip on 2011-11-04
Don't worry, I have yet to find a way to properly destroy the system and having to reinstall fro scratch. :D

If you are not familiar with compiz, just do this:

Close any app running, then in a terminal window:
```
unity --reset
```

Be prepared for a lot of screen action and appearing/disappearing of elements. And a lot of warnings/errors on the terminal (just ignore them). After the Desktop is back, DO NOT close the terminal. Instead, logout and then login again. Everything should be as it was before.

If you want to tweak just the settings of the app launcher, just go to view the settings of the unity plugin in ccsm (compiz config setting manager) and be careful not to untick anything, as this may cause the entire window manager to reload and mess up. Settings for the launcher are under "Experimental" tab.

Happy resetting :popcorn:

---

### Post by beacon on 2011-11-04
Thanks Typhoon. I suppose I ought to have posted the fact that nothing ever seems to work for me as it should. Followed instructions, but after a lot of screen work I got 'svg: error opening file:no such file or directory'. 
 Everything stopped, and after an hour it is still stopped. However when I try to close I am told a process is still running. I'm afraid to do anything more in case I really Mess up.

Anything to help?

---

### Post by beacon on 2011-11-09
I have had no more responses since my bad luck with compiz, so I suppose I am stuck. However, I have to say that this has become more than a niggle, and I am changing to Mint.

---

### Post by Copper Bezel on 2011-11-09
Unity is a part of Compiz - it's a plugin, like Gnome's Shell is to Mutter. You didn't install Compiz, but its ("advanced") settings manager. Changing some settings can break things, but most likely, you just have the auto-hide behavior turned off in the Unity plugin, so poke through that and make sure that the Launcher's "hide" behavior isn't set to "never."

To avoid the Launcher displaying randomly, you can actually set it to only appear when you hit the upper left corner of the screen, as with Shell's overview. That Launcher Reveal Mode toggle that was mentioned earlier can be set to any edge or corner (but Left and Top Left are the only settings that would make sense there.) (The "mouse gestures" referred to earlier just mean which side of the screen you're touching with the pointer.)

Gnome Shell runs quite peaceably over Ubuntu, by the way, so switching to Mint doesn't get you much there. (Mint is a derivative of Ubuntu. It mostly just includes codecs and things that Ubuntu can't legally ship and a few Windowsy plugins and applets. And, of course, it uses Gnome Shell rather than Unity.)

---

### Post by Seb71 on 2011-11-09
> **Copper Bezel said:**
> 
Gnome Shell runs quite peaceably over Ubuntu, by the way, so switching to Mint doesn't get you much there. (Mint is a derivative of Ubuntu. It mostly just includes codecs and things that Ubuntu can't legally ship and a few Windowsy plugins and applets. And, of course, it uses Gnome Shell rather than Unity.)
Linux Mint 11 (latest version currently available) still uses Gnome 2.3, not Gnome Shell.

---

### Post by Copper Bezel on 2011-11-09
For the next three weeks, yes. = )

---

### Post by Stovey on 2011-11-09
> **beacon said:**
> ...It is difficult to go the the arrow to move back one page, without having it obscured by the applications panel (if that is what it is called) which suddenly appears from the side...

Hi Beacon, this can be a little troublesome.  This thread has some good solutions, but I wanted to add that you can use "ALT-LEFT ARROW" to go back one page.

---

### Post by Seb71 on 2011-11-09
If the problem is only with Firefox, you can also move the Back/Forward arrows from Firefox more towards the middle of the window or to the right side.

---

### Post by beacon on 2011-11-10
Thanks for the two replies and for your patience; I sometimes falter at the most obvious points. I have just tried again with the suggestion by typhoon_tip and had exactly the same results with all kinds of notations about failures and such like, until I reached 'svg error opening file: no such file or directory'. Then it all came to a halt as before. Is it safe to leave it like that, or should I uninstall something or other?

Thanks very much for your advice Copper Bezel. I have the launcher behaviour button on auto. It doesn't seem to make any difference which choice I tick, the launcher launches whenever the arrow is near the left side.

I have just come across the messages from Stovey and Seb71. Many thanks. One or both of those suggestions may be just the job.

---

### Post by Copper Bezel on 2011-11-10
beacon, to clarify, I didn't mean the third option, the "Hide" behavior. I meant the first option on that page, the "Reveal Mode" behavior, which is set to "Left" by default.

---

### Post by beacon on 2011-11-10
Thanks again Copper. I'm sorry that I was unclear when I posted. I mean to say that in answer to one point, I had made certain that the auto-hide behaviour was ok. 

I had in fact meant to reply to another aspect, but I am slightly confused by the terms, 'first option' and 'third option'. The first option under launcher that I can see is behaviour, then there are several others, and the 7th one seems to be the launcher reveal mode that you appear to refer to. As I said, it seems to make no difference which of the two choices (left side or top left-hand corner) I use. The behaviour is the same.

---

### Post by Copper Bezel on 2011-11-10
Odd. I mean, if you have that option set, it should work.

The layout thing is strange, though. Probably a crime that I'm taking this screenshot under Shell, but does it not look like this?

[[img]http://dl.dropbox.com/u/17749392/Screenshots/20111105/ccsm%20%28copy%29.png[/img]](http://dl.dropbox.com/u/17749392/Screenshots/20111105/ccsm.png)

---

### Post by beacon on 2011-11-10
Thanks again Cooper for your continued help. 

I'm really getting embarrassed. I can take a screenshot, but I have been working flat out and can't seem to send it. All the info is about sending to an email address without mentioning copying it to something like a forum entry. 

I can say that my layout is not like yours, and it is headed 'comfity', but that is what comes up when I type unity into the Dash.

---

### Post by Copper Bezel on 2011-11-10
Sorry, I guess I could have been clearer - these options are in CompizConfig Settings Manager, which you installed earlier, not in Confity, which is a third-party configuration tool I'm not entirely familiar with and which doesn't seem to allow you to set all of the available options. I guess you must have installed it at some point in this process?

Instead of typing "Unity" into the Dash, type Compiz, and CompizConfig will come up. Unity's settings are available in the Unity plugin settings screen. When you run CompizConfig, you'll see a bunch of little tiles for settings for each of Compiz's plugins, and you might need to scroll down a bit to find Unity's. (It's the purple icon, though, easy to spot. = D)

---

### Post by beacon on 2011-11-11
Thanks yet again. All has been explained, and I am now au fait. I don't know how confity was installed, but either I followed instructions in another thread or did something off my own bat. In any case, I am most grateful for your help, and added to the advice from Seb and Stovey I think I am well on my way. I'll mark this as solved once I remember how to do it.

---

