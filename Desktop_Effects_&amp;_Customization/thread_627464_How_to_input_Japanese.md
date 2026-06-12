---
title: "How to input Japanese"
date: 2007-11-30
forum: Desktop Effects &amp; Customization
---

### Post by maxidius on 2007-11-30
Hi all,

I want to know how to add a keyboard on the desktop which is used to input Japanese language. I install the support for few other languages, including Japanese, but I can't find out where to do so.

Thank you for any help, guide or advice.

-- Max

---

### Post by jujoje on 2007-11-30
Hopefully this will help:

[https://help.ubuntu.com/community/SCIM]("https://help.ubuntu.com/community/SCIM")

Haven't tried it in Gutsy yet, but should work pretty well.

---

### Post by Zorael on 2007-11-30
Oh man, this was *not* easy to do. :> I'm not sure I remember the whole procedure, but at least I can get you on the right track.

You'll want to install the scim, scim-anthy, scim-bridge, and scim-tables-jo packages. Also skim if you run KDE. There may be other packages, but hopefully dependencies will get you the ones you need.

Once installed, you'll want to run scim-setup (from a terminal or a run box. If you use Skim, beware that scim-setup has more settings than skim has, so you probably want to browse both of them.

In scim-setup, I disabled all/most keybinds. You don't need any next/previous input method if you only want to toggle between Japanese and random other rômaji tables. Perhaps Trigger, but I doubt it.

In Global setup, be sure to select Anthy. It should be there if you have scim-anthy installed. Disable all its hotkeys. If you have HIRAGANA and KATAKANA in that list as well, disable if you wish, I don't use them much at least.

In the Anthy tab, set it up as you wish. You may want some of those keybinds enabled, like Cirle input mode and Circle kana mode. These likely changes between hiragana and katakana input, not sure.

In JIS Kana Layout under Kana typing, Customize it if you want to add your own shortcuts. For instance, I wanted a proper Japanese &#65374; (who doesn't? :> ), so I mapped ~ to it. Also note that you can force lowered kana by prefixing it with an x (xtsu -> &#12387;, etc). Or add your own shortcuts.

Under GTK, I put the Toolbar "On Demand", since I use the keybinds instead.


Now, to actually use it, you right-click any SCIM-aware input field, pick Select Input Method, and pick SCIM/Simple Composite Input Method. Then you can use your keybinds. This is cumbersome however, and it won't work in Firefox, so you'll want to set SCIM as the standard input method.

Googling, I see [there's a guide here](https://help.ubuntu.com/community/SCIM) that covers that and some of what I already mentioned here.

Good luck. :>

---

### Post by maxidius on 2007-11-30
Thank you all. I am a newbie in Ubuntu. This is the first time I try Ubuntu. In about 2 years ago, I used Fedora, it has something similar to Windows, which I can put an icon of keyboard on desktop and just toggle between English and Japanese. Of course, the Linux way is a bit more complicated. But I forgot how to do that too, as I did not use Linux very often. 

Let me try and give you a follow-up later. I may come back with some other questions. 
Thanks for your quick replies.

---

### Post by maxidius on 2007-12-01
Just a follow-up:

It seems simpler than I thought. I looked for more details in keyboard and language support, and I happen to see the SCIM where some settings are found. After trying many ways to play with the settings, I found out that, the default is to use Shift + Space to toggle on/off Japanese/English. 

Also, what made me unable to input Japanese was because I did not specified the keyboard 
type; i.e., US or Japanese keyboard. Once this is done, I can input Japanese hiragana, 
katakana, and change to Kanji from the hiragana inout.

Thanks again for the info.

---

