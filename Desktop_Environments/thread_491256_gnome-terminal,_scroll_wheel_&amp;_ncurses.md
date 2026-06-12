---
title: "gnome-terminal, scroll wheel &amp; ncurses"
date: 2007-07-03
forum: Desktop Environments
---

### Post by dpb on 2007-07-03
Hello,

I'm having a problem with ncurses applications (mutt & vim specifically) and gnome terminal.  Whenever I use the scroll wheel in the application, it performs some action in the application.  for instance, in mutt, it scrolls through a bunch of messages, and marks them all as read.  In vim, it seems to jump up or down half a page.  If I'm running without a ncurses app going, it scrolls back in the buffer (which is fine).

How can I control this behavior in my ncurses app?  Does anyone have any experience with this?  What is happening is not expected by me, and often leads me to get frustrated.  I actually like the interaction the scroll wheel allows, but it's not very useful they way it comes configured by default.    Is there a setting in vim/mutt that allows me to respond to whatever is being sent to the application?  Is it a specific key-press?  It doesn't appear to be pg-up pg-dwn, as that scrolls a full screen at a time.

In mutt it appears to go up/down 9 lines, in vim it also appears to go up/down 9 lines.  I can't figure out why this happens?  It also appears as though it's generating 9 individual down/up sequences.  e.g., it doesn't jump 9 lines down, it sends "down arrow" 9 times.

I would appreciate any help I could get here. :)

Thanks!

---

### Post by tillo on 2007-07-03
I'm sorry I'm not really an expert about mouse bindings on terminal, but I know that shift+button (or scroll) should avoid any program hook. I can't tell you how to disable it.

---

### Post by andrew.46 on 2007-07-05
Hi,

 I realise that you have deliberately setup the mouse for vim and mutt but surely they were designed from the ground up for use with the keyboard only? I use only keyboard for vim, mutt and slrn with no great problem, just a matter of getting used to it.

                  Andrew

---

### Post by dpb on 2007-07-05
I have not deliberately set up the mouse for use with vim or mutt.  Ubuntu seems to have shipped that way. I don't want to use it, I simply want to know how to alter the behavior of the scroll wheel in a full screen ncurses app that is running through gnome-terminal.  Basically, I would be fine with turning off the interaction altogether.  What happens is occasionally, when grabbing my mouse, my finger will slip and hit the scroll wheel.  I don't want that to modify my ncurses app.

As I said, I don't have this problem with xterm, only with gnome-terminal.  It is obviously interpreting my mouse wheel movement as a "up/down arrow 9 times" command.  I would like to modify that behavior, or turn it off.

---

### Post by andrew.46 on 2007-07-05
Hi,

 Not sure how to untangle the repository versions but you could compile from source. For mutt:

[http://people.aapt.net.au/~adjlstrong/mutt.html](http://people.aapt.net.au/~adjlstrong/mutt.html)

and at the base of this page for vim:

[http://people.aapt.net.au/~adjlstrong/dapper.html](http://people.aapt.net.au/~adjlstrong/dapper.html)

Or you could have a look at ~/.muttrc which might have a mouse setting or either ~/.vimrc or the system vimrc file.

                   Andrew

---

### Post by dpb on 2007-07-17
Just wanted to follow up with my solution.

I cannot figure out how to stop this interaction with the mouse wheel & gnome-terminal, so I instead adjusted the behavior on an application by application basis:

In Mutt, I rebound the up and down arrows:

```

  bind pager <Up> previous-line
  bind pager <Down> next-line

```

whereas, previously they had been used to move from message to message.

In Vim, I don't mind the behavior, so I left it as default.

The key was that the mouse wheel up or down is generating a series of 9 up button or down button presses.

Anyway, I guess there is more than one way to skin a cat, and I'm instead choosing to live with the cat because I've kind of grown attached to it.  :)

---

### Post by hncaldwell on 2008-06-18
The problem is with vte (the terminal widget that gnome-terminal uses).  A feature was added that sends a number of up/down keystrokes instead of regular scrolling if it is using the alternate screen or scrolling is restricted (one or both of which are the case when using ncurses applications).

I wrote a patch for vte to make the feature toggle-able, and a patch for gnome-terminal that allows you to turn it off or on for a profile.  I filed a bug for this at:

[https://bugzilla.gnome.org/show_bug.cgi?id=538195](https://bugzilla.gnome.org/show_bug.cgi?id=538195)

You can get the patches there.  Unfortunately, it looks like the vte developer isn't very receptive to the idea of making the feature configurable, which is kind of baffling to me.

The gnome-terminal patch makes the setting available under the "Scrolling" tab in the profile editor.

---

### Post by patrickjlbyrne on 2008-06-27
Hi,

Sorry for hijacking this thread, but it is the first discussion that I have found that looks at all relevant to what I am seeing

I am trying to get mouse input working in gnome-terminal. This code:

[http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/mouse.html](http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/mouse.html)

..is not working correctly. I can compile and run it it gnome-terminal, but mouse clicks do not appear to be generate mouse events to ncurses. Same happens in an xterm.

Can someone indicate how I might persuade gnome (metacity?) to pass mouse events to a terminal?

Thanks,
Patrick Byrne

---

