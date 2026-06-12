---
title: "Awesome Window Manager Setup Problem"
date: 2012-09-05
forum: Desktop Environments
---

### Post by Cogito² on 2012-09-05
I'm trying out Awesome WM, but I'm running into difficulties. I've installed it from the repositories fine, but I've run into problems when editing my rc.lua file. More specifically, nothing I change in that file seems to affect my window setup. At this point all I'm trying to do is to change my tag names and default layouts, but each time I restart awesome I keep ending up with tags 1 through 9 listed on the top. I get no errors even when I put garbage in the file, so I'm wondering if there is something keeping the file from being read.

I thought it might be because my $XDG_CONFIG_HOME variable wasn't set, but fixing it didn't change anything (and apparently it shouldn't matter if it's empty anyway). I added both .xinitrc and .xsession files in my home directory as well (I'm not sure if those are being read either).

So I guess my question is just: Has anyone here installed awesome through the repositories and run into similar problems? If so, I would gladly hear your wisdom.

Also, if this has already been asked I'm sorry and I'll gladly take a link. I've searched google and these forums and come up empty now after quite a bit of searching.

---

### Post by Toz on 2012-09-05
Did you copy /etc/xdg/awesome/rc.lua to ~/.config/awesome and are you editing the ~/.config/awesome/rc.lua file?

How are you changing the tag names? What code are you using? See: [http://awesome.naquadah.org/wiki/FAQ]("http://awesome.naquadah.org/wiki/FAQ")

---

### Post by Cogito² on 2012-09-05
Yes I did copy that file and editted as you're asking. And yeah your link is the guide I'm following. I tried both the example code and garbage (trying to force an error) and came up empty.

Thanks for the quick reply. I actually have to leave my office (where my comp is) for the night so I won't be able to fiddle with settings until tomorrow morning.

---

### Post by Toz on 2012-09-05
Perhaps you can post back the contents of your rc.lua config file. Here is the relevant part of mine that sets the different screen names:
```
-- {{{ Tags
-- Define a tag table which hold all screen tags.
tags = {
	names = { "main", "web", "mp3", "irc", "5", "6", "7", "8", "9"},
	layout = { layouts[1], layouts[10], layouts[1], layouts[1],
		   layouts[1], layouts[1], layouts[1], layouts[1],
		   layouts[1]
}}
for s = 1, screen.count() do
    -- Each screen has its own tag table.
    tags[s] = awful.tag(tags.names, s, tags.layout)
end
-- }}}

```

---

### Post by bigboard on 2012-10-17
Hi,

Hopefully you've solved your issue already, but as I had a similar problem, I though I'd post to tell you how I resolved it.

I had a previous rc.lua config file that had been working correctly with an older version of awesome. After an upgrade, I began having the same problem as you. Awesome would not use the rc.lua in ~/.config/awesome, and used the system rc.lua from /etc/xdg/awesome instead. From a command line I ran:

```
awesome -k
```This parses your configuration file for errors. Gusess what? I had an error. I copied the system rc.lua to ~/.config/awesome, made a minor change and restarted awesome. Problem fixed, awesome was now reading my personal rc.lua.

---

### Post by ~LoKe on 2012-10-22
I know this is a bit late but thought I should post something anyway.

Most programs with a user-based config file (~/.config/xxx) will fall back on their default config file if there is an error.  So if you ever have an app that behaves this way, make sure you have no errors.

AwesomeWM was notorious for giving me this problem years ago.

---

