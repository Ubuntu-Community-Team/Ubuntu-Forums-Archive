---
title: "keyboard layout added on boot"
date: 2010-04-27
forum: Desktop Environments
---

### Post by nikosm on 2010-04-27
Hello,

This is Karmic on a Lenovo notebook with US-Keyboard.

I made two custom keyboard layouts as per [this guide]("http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11") and added them. One of them is basically the USA layout with some symbols swapped and additional characters, but everything that can be typed by the USA layout can be typed by this one as well. 

On each boot, the USA layout is automatically added. I suspect it's because my locale is US and gnome wants to be sure that I can type in important commands like "sudo". Is there any way to disable this (if true)? Setting my layout as default doesn't fix this. Calling setxkbmap on startup doesn't fix it.

As a temporary work-around: can I remove a layout by command line (and add this command to the Startup)?

Thanks!
Nikos

---

### Post by tom4everitt on 2010-04-27
I had the same problem with Lucid for a while (very similar keyboard layout setup also). But it fixed itself with the regular updates...

---

### Post by nikosm on 2010-04-27
> **tom4everitt said:**
> I had the same problem with Lucid for a while 

Thanks for the fast answer. Just to clarify: was your locale also US and did the USA keyboard add itself on boot? If so, I'll wait to install Lucid and hope for the best!

thanks again,
Nikos

---

### Post by tom4everitt on 2010-04-28
Yes, my locale is US. I prefer to have my system in english although I'm really swedish. My keyboard is a Swedish keyboard, so I always add a Swedish keyboard layout, and erase the US layout. This time however, every time I logged in the US layout was back, and chosen as primary. Very annoying, even if it only takes a few seconds to switch. 

This bug bothered me through the beta releases of Lucid, but has now fixed itself (most probably from a regular update). I notice now that you experience this bug in Karmic. That wasn't the case for me. For me it only appeared in Lucid. But there's still a good chance it fixes itself when you install Lucid I guess :) 

Good luck! 


PS. I wish I had a more useful answer.

---

### Post by nikosm on 2010-04-28
Thanks for your answer, i wanted to be sure that your experience is exactly what happens to me. 

Maybe Karmic with all the updates is quite similar to an early version of Lucid, which would mean that there is hope it will go away by itself when installing Lucid. 

You have been very helpful, thanks a lot!
Nikos

---

### Post by simosx on 2010-05-07
> **nikosm said:**
> 
I made two custom keyboard layouts as per [this guide]("http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11") and added them. One of them is basically the USA layout with some symbols swapped and additional characters, but everything that can be typed by the USA layout can be typed by this one as well. 

On each boot, the USA layout is automatically added. I suspect it's because my locale is US and gnome wants to be sure that I can type in important commands like "sudo". Is there any way to disable this (if true)? Setting my layout as default doesn't fix this. Calling setxkbmap on startup doesn't fix it.

As a temporary work-around: can I remove a layout by command line (and add this command to the Startup)?

This thing with Karmic where the 'us' layout is re-added during boot was an Ubuntu feature (not a GNOME thing). That is, it was a distribution feature/bug.

The layout settings are stored in GConf, and you can read them with
[INDENT]
gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd[/INDENT]

The result of that command is something like 'layouts = [us,gr]', so you can use 'gconftool-2' with the '--set' parameter to force the 'layouts' list to your liking. You can write a script for this, and add to the Startup Applications (in System &#8594; Preferences).

Instead of creating new compose sequences, I recommend to select the appropriate keyboard layout.
For existing compose sequences, see /usr/share/X11/locale/en_US.UTF-8/Compose
You can search the document by Unicode character and see if there exists a sequence that can produce the said character. The list in that file is almost the same with what GNOME supports.

If you use the US English layout, you can select the "US English (with dead keys)" variant which supports all combinations of Latin characters with accents (such as &#7785;&#491;&#333;ö&#466;&#335;&#337;).

---

### Post by nikosm on 2010-05-11
Geia sou Simo!

> **simosx said:**
> 
[INDENT]
gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd[/INDENT]

The result of that command is something like 'layouts = [us,gr]', so you can use 'gconftool-2' with the '--set' parameter to force the 'layouts' list to your liking. You can write a script for this, and add to the Startup Applications (in System &#8594; Preferences).


Great! This will do as a temporary fix.

> **simosx said:**
> 
Instead of creating new compose sequences, I recommend to select the appropriate keyboard layout.


I agree with you for seldom use of special characters. In my case though I find that I am more efficient if the special characters I use are easy to compose (as opposed to use dead keys). E.g. I write german often, so I want ä to be ALT-GR + a instead of a dead : followed by an a. I also like to tune some other minor things, e.g. I write LaTeX often, so I prefer {} and [] exchanged so {} is typed without Shift and other such small things. Finally, for the greek keyboard layout, I added the latin alphabet in the 3rd Level, so that you can easily write "&#920;&#945; &#963;&#959;&#965; &#963;&#964;&#949;&#943;&#955;&#969; &#941;&#957;&#945; email &#945;&#961;&#947;&#972;&#964;&#949;&#961;&#945;" without having to switch layouts. I made two customized layouts for these reasons.

> **simosx said:**
> For existing compose sequences, see /usr/share/X11/locale/en_US.UTF-8/Compose
You can search the document by Unicode character and see if there exists a sequence that can produce the said character. The list in that file is almost the same with what GNOME supports.

Nice! Good to know, could be useful in the future.

Thanks a lot for your help!
Nikos

P.S. I attach the mentioned layouts if you want to have a look (the international one types - in order of preference - german, italian, polish, french, spanish)

---

### Post by simosx on 2010-05-11
> **nikosm said:**
> 
...snip...
Thanks a lot for your help!
Nikos

P.S. I attach the mentioned layouts if you want to have a look (the international one types - in order of preference - german, italian, polish, french, spanish)

These two layouts are good work. I recommend to make effort to publicise them. If you have a blog, do a write-up (instructions to install, etc) and post the link.
If there are more users who find the gr.txt layout usable, it could be a good addition to add the layout as a variant to the Greek layout.
If you have a blog with open-source content, contact me with PM to discuss  adding to [http://planet.ellak.gr/](http://planet.ellak.gr/)

---

