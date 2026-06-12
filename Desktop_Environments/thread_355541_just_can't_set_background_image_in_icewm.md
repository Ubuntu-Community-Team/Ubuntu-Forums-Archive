---
title: "just can't set background image in icewm"
date: 2007-02-07
forum: Desktop Environments
---

### Post by vronp on 2007-02-07
Hi all,

I have what I believe to be a healthy icewm setup but I just cannot get a background image to display.  This is driving me nuts.

I have my ~/.icewm/preferences file edited correctly to point to the image I want to use as a background.  But, no dice.

All I have ever seen on the desktop is the "ubuntu brown".

Experts, please help me out.

thanks,

---

### Post by Peter76 on 2007-02-07
My guess is that if you only see the Ubuntu brown, that you have gdm configured to start icewm-gnome or something; change your session to icewm and see if that works

---

### Post by fuscia on 2007-02-08
i can't get it to work either. i've always just used feh for wallpapers when i'm using a plain wm. a typical command for using feh, for wallpaper, would be *feh --bg-scale imagefile.whatever*. *tile, center, etc.* can be used instead of *scale*. it's a good image viewer, as well.

---

### Post by berserker on 2007-02-08
I had to make sure that icewmbg was running.  I did this by ensuring that /usr/share/xsessions/IceWM.desktop was executing "/usr/bin/icewm-session" rather than just "/usr/bin/icewm".

---

### Post by jplowman on 2007-08-02
I have had the same problem ever since using icewm. 

Before I was using icewm with rox-filer, and rox-filer set the desktop for me. Now I've switched to PCManFM - I have an oldish laptop so I'd like to use the lightest-weight file manager possible (suggestions?).  But I'm back to having no desktop image. 

I've tried converting the image from jpg to xpm. I've tried moving the image into the ~/.icewm directory. When it didn't work in ~/.icewm/preferences, I created the file ~/.icewm/prefoverride with the same command (DesktopBackgroundImage="~/.icewm/tsunami.xpm"). When it didn't work there, I copied the theme I'm using (IceBuntu) and put the same command into the default.theme file. I've made sure the /usr/share/xsessions/IceWM.desktop file said Exec=/usr/bin/icewm-session (i.e. it starts icewm-session, not just icewm). I even tried to make sure the xinitrc and xsession files in /etc/X11 would invoke icewm-session, not icewm. After every change I ran icewmbg just to be sure.

Nothing worked. I never saw the image on the background even for a moment.

Any ideas? The only clue I have is that, from the tty prompt (I use no display manager) I can run "startx" but "startx icewm-session" always crashes. 

Are there any lightweight programs that will give me a background? The black-white checkerboard that Icewm is throwing up by default is headache-inducing.

Seems like a shame, though, to have to run another program to do what IceWM is supposed to handle itself, especially when my motive for using it is that it is lightweight.

(Edit: Thanks Fuscia! Installed feh and added your command to ~/.icewm/startup. Works like a charm.)

---

### Post by kerry_s on 2007-08-02
are you guy's using the full path?
i use rox but i still set the icewmbg or my conky won't blend in. but mine didn't work till i used the full path.

---

### Post by jplowman on 2007-08-02
Sorry, I'm a bit of a noob. My path is the list of directories which is searched when I try to execute a command, yes? I know icewm-session is in my path. Is that what you mean? What is a "full path"?

---

### Post by kerry_s on 2007-08-02
> **jplowman said:**
> Sorry, I'm a bit of a noob. My path is the list of directories which is searched when I try to execute a command, yes? I know icewm-session is in my path. Is that what you mean? What is a "full path"?

the full path start from the top root(/), so it is like /home/"your login name"/where you got the picture.

my log in name is user & i have the picture i want to use in a folder named Desktop, so mine looks like this> /home/user/Desktop/piss.jpg
alot of times we like to cut it down, like this> ~/Desktop/piss.jpg < which has the same meaning as the full path, this "~" is to signify the users home account, "/Desktop" tells what folder and "piss.jpg" is the image i want to use. the short cut didn't work for me. see the first pic in that other post, that's my exact setting.

---

### Post by jplowman on 2007-08-02
> **kerry_s said:**
> the full path start from the top root(/), so it is like /home/"your login name"/where you got the picture.


THANK YOU Kerry_S. That was the problem. Anyone else with the icewm background problem, TRY THIS. You must include "/home/*yourusername*/" NOT just "~/" in the image path you set in icewm's preferences (or prefoverride) file.

DesktopBackgroundImage="~/.icewm/tsunami.jpg"  <-- didn't work
DesktopBackgroundImage="/home/*myusername*/.icewm/tsunami.jpg"  <-- worked

God what a relief! :biggrin:

---

