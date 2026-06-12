---
title: "In need of qingy assistance"
date: 2009-02-13
forum: General Help
---

### Post by archeryguru2000 on 2009-02-13
Is anybody aware of a HOW TO tutorial for qingy?  I've been trying for a couple of days now to get it working.  I've been mainly following these two cites:
[B][U][Qingy 1]("https://help.ubuntu.com/community/qingy")
[Qingy 2]("http://mzanfardino.wordpress.com/2009/01/30/replacing-default-desktop-manager-with-qingy-on-ubuntu-intrepid/")[/U][/B]
Both have good advice... but neither give assistance for possible errors.  After installation, the error I'm greeted with is as follows.
```

Loading, please wait...
mknod: /dev/fb0: File exists
(!) [ 1081:    0.000] --> Caught signal 15 (sent by pid 5901, uid 0) <--
Splashy caught signal number 6. Exiting..._

```
I'm not quite sure if this is a splashy error or a qingy error (or something else even).  My splashy works without qingy (before qingy install and after qingy unistall).  So I'm inclined to say that the error is qingy related.  Has anybody else been able to install both splashy and qingy?  Maybe these two just do not play well with each other.

~~archery~~

---

### Post by archeryguru2000 on 2009-02-18
bump, anybody?  Please. 

~~archery~~

---

### Post by archeryguru2000 on 2009-02-19
Ok, after a couple of hours, I finally have Qingy loaded and installed.  I'm not quite sure that it is operating to full capacity though.  Upon booting up, I'm greeted with a qingy log-in screen.  =D>  So I did a little dance (ok you didn't necessarily need to know that).  But after logging in, it takes me back to the qingy log-in screen.  :-k  So, I am required to log into a terminal and execute $: startx  This allows me to jump into my gui desktop.  Shouldn't I be able to choose my gnome session and go directly to that desktop?  I have the option available during my log-in, but it routes me back to the log-in screen... again.  Any suggestions, anybody?

~~archery~~

---

### Post by archeryguru2000 on 2009-02-23
Ok, here's my progress... or lack thereof!  Here's my /etc/qingy/settings file:
```

# Directory containing X sessions
x_sessions = "/etc/X11/Sessions/"
# Directory containing text mode sessions
text_sessions = "/etc/qingy/sessions/"
# Directory where qingy should put its temporary files
temp_files_dir = "/var/lib/misc"

# Full path to the X server
# x_server = "/usr/X11R6/bin/XFree86"
# Full path to the 'xinit' executable
xinit = "/usr/X11R6/bin/xinit"

# Parameter we should pass to the X server
x_args = "-nolisten tcp"

# How verbose should qingy be?
# Possible values are debug, error
# Default value is error
log_level = error

# Where should qingy messages be logged?
# Values can be one or more of the following:
# console, file, syslog
# Default value is console
# log_facilities = console, file
log_facilities = console

# Offset to search for an available X server number.
# This number affects the DISPLAY env variable.
# Default is 1, setting it to 0 will make buggy OpenGL implementations
# (like the ATI one) work with qingy, but it will also make it impossible
# to start an X server from console using startx without passing it
# extra parameters.
#x_server_offset = 1

# Where should we start the X server?
# Accepted values are:
#   qingy_tty (default) to start it in the same tty qingy is running in
#   unused_tty to start it into an unused tty
x_server_tty = unused_tty

# Scripts that should be executed just before/after qingy GUI is fired up/shut down
#pre_gui_script  = "/path/to/pre_guiscript.sh"
#post_gui_script = "/path/to/post_gui_script.sh"

# Where are the screen savers?
screensavers_dir = "/usr/lib/qingy/screensavers"

# How much should we wait (in minutes) before the screen saver is fired up?
# A value of 0 disables screensaver completely.
screensaver_timeout = 5

# How much should we wait (in minutes) before the screen enters power saving mode?
# A value of 0 disables the feature
screen_powersaving_timeout = 30

#screensaver "pixel"
screensaver "running_time"#="%H:%S:%M"

# Where are the themes?
themes_dir = "/usr/share/qingy/themes"

# What theme do you want (you can also specify 'random')
# theme = random
theme = "default"

# Who is allowed to shut down the system?
# Allowed options are 'everyone', 'root', 'noone'
# default policy is everyone
# shutdown_policy = everyone

# How should latest user be calculated?
# global means get latest user that logged in using qingy from whichever tty
# tty    means get latest user that logged in using current tty
# none   means do not get (and set) latest user
# default policy is global
#last_user_policy = global

# How should latest user session be calculated?
# user means get last session of each user
# tty  means get last session of current tty
# none means do not get (and set) latest session
# default policy is user
#last_session_policy = user

# What happens when we press the 'sleep' button?
#sleep = "/usr/local/sbin/hibernate"

# whether we should clear background image during dialogs (default is no)...
# this is the default setting, it gets overridden if the theme you are using
# sets the same setting differently...
# clear_background = yes

# whether to allow session locking; if you enable this, when you try to
# switch to a qingy-controlled tty whose owner is not your current
# user, you will be asked for the password of that user before being
# allowed to continue. If you are root, of course, you can switch
# to any tty you chose to. Default setting is 'no'.
#lock_sessions = yes

# whether to allow session timeout; if you enable this, after the amount
# of minutes specified in idle_timeout variable, idle_action will be
# performed. Allowed actions are:
# lock     will lock user session asking you for your password
# logout   will close your session
#idle_timeout = 30
#idle_action  = lock

# these options are valid only if qingy is started from tty3
#tty = 3
#{
#	theme = "fireplace"
#	screensaver "pixel"

#	# Should we auto log in?
#	# Totally insecure, but very convenient ;-)
#	# Note that this section must be put inside a tty=n{} block
#	# Also, if you decide to use this feature, it is better
#	# that you also make this settings file readable only by root
#	autologin
#	{
#		username = "myuser"
#		password = "mypassword"
#		# You can also use 'session=lastsession' to automatically choose last user session
#		session  = "Text: emacs"
#		# if set to 'no', qingy will autologin only once every system restart
#		relogin  = no
#	}
#}

keybindings
{
	prev_tty    = "win"      # switch to left tty
	next_tty    = "menu"     # switch to right tty
	poweroff    = "ALT-p"    # shutdown your system
	reboot      = "ALT-r"    # restart your system
	screensaver = "ALT-s"    # activate screen saver
	sleep       = "ALT-z"    # put machine to sleep
#	kill        = "CTRL-c"   # kill qingy
	text_mode   = "CTRL-ESC" # Revert to text mode
}

```

After booting up the computer, I'm greeted with the qingy log-in screen.  I log into the computer (choosing gnome as my session) and the screen prints 'Logging in... blah blah blah.'  But then I'm greeted with a large amount of text output whereas the last line reads 
```

Running local boot scripts /etc/rc.local

```
and then the qingy log-in screen again.

However, if I choose terminal as my session.  I'm logged in.  I then issue the command startx, and all is well (or at least as well as it can be).  I'm thinking that my problem must be within my /etc/X11/Sessions/ folder but not quite sure where to actually look.  I have a file named gnome located there, but I don't think that is my issue.  I think it must be something related to how/where qingy is calling the session... maybe?  I've even changed the line in the /etc/qingy/setting file from
```

# Directory containing X sessions
x_sessions = "/etc/X11/Sessions/"

```
to
```

# Directory containing X sessions
# x_sessions = "/etc/X11/Sessions/"
x_sessions = "/usr/share/xsessions/"

```
But no such luck, exact same results.  Any suggestions would be greatly appreciated.

Thanks,
~~archery~~

---

### Post by archeryguru2000 on 2009-03-05
Is anybody else having difficulties getting Qingy to work with Splashy on 8.04... or is it just me?  It's getting awfully lonely here.  :-\"

~~archery~~

---

### Post by archeryguru2000 on 2009-04-23
Ok, I've finally given up on qingy.  Apparently it just does not work!

---

### Post by vkurup on 2009-08-28
First of all, I applaud your persistence. I finally have gotten qingy working (on Debian), but wanted to post because I ran into the same problem you did. The files in /usr/share/xsessions are not the files that qingy wants. It wants files whose contents are the full path of the window manager, so a file named 'gnome' whose contents are '/usr/bin/gnome-session', or a file named 'dwm' whose contents are '/usr/bin/dwm'.

This seems to work, although there are still some configuration issues. 

This link was helpful:
[http://bbs.archlinux.org/viewtopic.php?pid=590667](http://bbs.archlinux.org/viewtopic.php?pid=590667)

---

### Post by archeryguru2000 on 2009-08-29
> **vkurup said:**
> First of all, I applaud your persistence. I finally have gotten qingy working (on Debian), but wanted to post because I ran into the same problem you did. The files in /usr/share/xsessions are not the files that qingy wants. It wants files whose contents are the full path of the window manager, so a file named 'gnome' whose contents are '/usr/bin/gnome-session', or a file named 'dwm' whose contents are '/usr/bin/dwm'.

This seems to work, although there are still some configuration issues. 

This link was helpful:
[http://bbs.archlinux.org/viewtopic.php?pid=590667](http://bbs.archlinux.org/viewtopic.php?pid=590667)

Wow, thank you for your reply... but I've ditched qingy months ago.  I may try again sometime in the future though (I can never leave anything alone :P ).

Thanks again,
~~archery~~

---

