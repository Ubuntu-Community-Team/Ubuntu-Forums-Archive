---
title: "mumbles 0.4 released! - Notification Eye Candy"
date: 2007-08-30
forum: Desktop Effects &amp; Customization
---

### Post by dot_j on 2007-08-30
Hi all,

I posted [here]("http://ubuntuforums.org/showthread.php?t=418373") a while back when I released mumbles 0.3. We'll I'm happy to report that mumbles 0.4 is now out!

For those of you that have tried it out in the past, this version comes with more plugins, themes, growl network support and other bug fixes and additions.

If you haven't yet used mumbles, it is a desktop notification system with a different take on notifications - similar to libnotify in Ubuntu, but based more on Growl for OSX.

Version 0.4 even comes with a .deb package making for easy installation on Ubuntu.

Screenshots, download information and more of the usual can all be found at:

[mumbles-project.org]("http://mumbles-project.org")

If you try it out, please let me know what you think. Thanks and I hope you dig it.

dot_j

---

### Post by magicrobotmonkey on 2007-08-30
it works good with irssi for me

---

### Post by Rupertronco on 2007-08-30
Just finished installing it. Fast install, very clean, low resource usage and looks spectacular!

Edit: Also very useful. Most of my eye candy is fairly useless (think wobbly windows). This is excellent.

---

### Post by lusepuster on 2007-12-06
Has development of Mumbles stalled? I see latest update was in August  31st... I am really excited about this project since it is one of the few things I have been missing a lot since my switch from Mac OS X...
Hoping for this project to grow strong and beautiful.

---

### Post by Niklas Schröder on 2007-12-06
is there any way to remove the icon from the notification area?  it's got a different background color from the rest of the bar...

---

### Post by dot_j on 2007-12-06
Development has slowed as I've been busy with work and such, but the project is in a bit of a mid-life design stage - comments/suggestions about the future of the project are welcome. What else would you like to see?

To start mumbles without the panel use -d (--daemon) on startup - and see -h (--help) for other options.

---

### Post by Niklas Schröder on 2007-12-06
cool.  :)  thanks.  two things i'd like to see in the future.

1. complete transparency (atm there is a thin black box around the notifications...  and yes, i'm using compiz)
2. integration with ubuntu gutsy notifications such as misc applets and battery notifications (update notifications would be nice too.  ;) )

---

### Post by lusepuster on 2007-12-06
Hi dot_j, 

A simple GUI to install/remove plugins and enable/disable them would be really nice and wouldn't have to be very complicated. thinking of it a bit like the amarok script manager or something...?

---

### Post by andrewsomething on 2007-12-06
> **lusepuster said:**
> Hi dot_j, 

A simple GUI to install/remove plugins and enable/disable them would be really nice and wouldn't have to be very complicated. thinking of it a bit like the amarok script manager or something...?

Agreed. That would go a long way to making this something used by more people.

---

### Post by dot_j on 2007-12-06
Plugin management (plugin-specific notifications, enable/disable, etc) is definately the next thing I want to work on. It does involve digging deeper into/learning more about glade/gtk, so contributions, mockups, ideas would be greatly appreciated. Please feel free to contact me on the site & get involved. One of the main reasons releases are so slow at the moment is most new features at this point require learning more before I can pursue certain things. So any contributions would most likely get development rolling at a faster pace.

Plugin contributions would also be grealy appreciated (and are hopefully easy to write) - see the site for details/tutorials.

Niklas: I don't see the box around the notification - have you tried using the "round" theme? Does it show then as well?

I've also heard a lot of requests for system level notification support I had stayed away from interacting with libnotify specific messages as I had considered them sufficiently different, but it is among the most requested features, so it will most likely be an option in the next release (but this is something I definitly want to make a user option).

---

### Post by lusepuster on 2007-12-07
Is there any way of discriminating different messages? I don't want a 'mumble' to pop up with a new pidgin message when pidgin is in fact the focused and active application. Just a thought. It might be hard, if the dbus message sent by pidgin is the same regardless if the window is focused or not, of course.

Maybe that could be implemented through the pidgin-libnotify plugin...?

---

### Post by Niklas Schröder on 2007-12-07
haven't tried the round theme.  can't figure out how to change it...

---

### Post by Ub1476 on 2007-12-07
Does this work with Swiftfox? If it does, where can should it put the plugin folder?

Also is there a list of available applications this works with?

Thanks:)

---

### Post by lusepuster on 2007-12-07
Schröder; right click the mumbles tray icon and choose 'preferences'.

Ub 1476; Take a look at the project web page, says it all.
Currently, Amarok, Rhythmbox, Pidgin, Gaim are among the supported apps by default, and there are plugins/extensions available for Firefox, thunderbird and Evolution.

But, any app using DBUS can be brought to give messages through Mumbles.

---

### Post by durand on 2007-12-07
Wow, this is pretty amazing. Works great even without compiz! Thanks. You could use launchpad to host a mini deb repository if you want.

> But, any app using DBUS can be brought to give messages through Mumbles. Not to mention, any app can technically be supported using mumbles-send.

---

### Post by dot_j on 2007-12-10
> **lusepuster said:**
> Is there any way of discriminating different messages? I don't want a 'mumble' to pop up with a new pidgin message when pidgin is in fact the focused and active application.

The focus issue is a slightly harder one - of the applications currently supported in mumbles, the DBus signals are focus agnostic. It does seem to me to be more on the specific application (I may want music track change notifications even if I'm on the window, for example), but I think a good compromise would be to make it a setting of the mumbles plugin (where hopefully any magic that would have to be done, could be). I've had the same request for pidgin focus checking from a co-worker, so hopefully we can come up with something.

> You could use launchpad to host a mini deb repository if you want.

I have wanted to do this, but haven't really looked into what building a python app on PPA entails. If anyone has any experience here, I would really appreciate some assistance.

> Does this work with Swiftfox?

I haven't tried, but if it supports the standard Firefox extensions, it should work just fine. If you try, let me know how it goes.

---

