---
title: "New Login in Nested Window (10.10)"
date: 2011-03-30
forum: Desktop Environments
---

### Post by iaindb on 2011-03-30
Hi,

I've seen this option for previous versions of Ubuntu, but neither of these commands seem to work for Maverick 10.10:

$ Xnest -query localhost :1

Just shows a black window.  If I try and start applications in it as another user (exporting DISPLAY and so on) it eventually crashes.

$ gdmflexiserver --xnest

returns with 

** (gdmflexiserver:11794): WARNING **: Not yet implemented

and `gdmflexiserver --help` says:

  -n, --xnest               Ignored - retained for compatibility

Is this still possible in Maverick?

thanks :)

---

### Post by iaindb on 2011-03-30
well it's always the way that you find the answer _after_ posting...

It turns out Xephyr is the new Xnest.  They look almost identical so it must have been a fork...

Anyhoo for those interested, this is how to use Xephyr to open a login in a nested window:

Assume you have two usernames, "iain" and "iainh".  You are logged in as your usual "iain", but you want to test something as the user "iainh"

Start a terminal and ssh to the second user:

ssh -Y iainh@localhost

Then start Xephyr
$ Xephyr -screen 1680x1050 :1 &

(change resolution to fit inside your screen, and ":1" must be an unused DISPLAY.  If it doesn't work, try :2)

in the terminal, start a gnome session:
$ DISPLAY=:1 gnome-session &

No doubt you could use kde-start also.  Now you should see a gnome session for the second user INSIDE the Xephyr window.

Now you can use two independent graphical logins together!

Obligatory screenshot showing the two log-ins (note the different usernames "iain" and "iainh"):
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=187618&stc=1&d=1301539652[/IMG]

---

### Post by henrythemouse on 2011-10-21
I know this post is two years old, but it was the only post i could find that gave me a solution to this problem. I'm using Ubuntu 10.4.

Thank you for posting this.

It works.

---

