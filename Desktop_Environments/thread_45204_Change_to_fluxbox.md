---
title: "Change to fluxbox"
date: 2005-06-29
forum: Desktop Environments
---

### Post by Granden on 2005-06-29
Hi!
After a installation of Ubuntu 5.04 and used apt-get install fluxbox how do I do so the computer not use the graphical log in interface and as well when I use startx it starts with fluxbox and not gnome?

---

### Post by llamakc on 2005-06-29
cd /usr/share/xsessions

cp gnome.desktop fluxbox.desktop

Now edit fluxbox.desktop to look like:

[Desktop Entry]
Encoding=UTF-8
Name=FluxBox
Comment=This session logs you into FluxBox
Exec=/usr/bin/fluxbox
# no icon yet, only the top three are currently used
Icon=
Type=Application
# end

Save it, and restart gdm:

/etc/init.d/gdm restart

You'll see the option now.

---

### Post by Granden on 2005-06-29
1. Okej thanks, but that doesnt remove the graphical login interface right?
2. And this I can change to is0-8859-15 right? Cause Im from sweden.
Encoding=UTF-8
3. How do I turn of X when Im logged in tried different combinations of ctrl and so but nothing worked. Havent tried them all but how do I do?

---

### Post by llamakc on 2005-06-29
That won't remove gdm, the graphical login manager. It adds an entry for the session.

And yes, change the encoding. I didn't even catch that. Thanks for noticing.

Do you REALLY want to turn off X completely? You can simply go to a command prompt by choosing one of the tty's with the key combo of:

ctrl-alt-F1,2,3 keys (F1-F6 on a standard Ubuntu install)

and go back to X with ctrl-alt-F7 (so X lives at F7, and F1-6 are the other command line tty's.

---

### Post by Granden on 2005-06-29
Oh right I can use ttys didnt thought of that but can I have x on F1-F4 and on F5-F6 have without X (bash) so its totaly text based?

---

### Post by oggah on 2005-06-30
I got xfce4 booting right now, but want to change to fluxbox. How do I?
ok. sudo apt-get install fluxbox. and then?

---

### Post by dphipps on 2005-07-24
I tried apt-get install fluxbox and all I get is this.

root@ubuntu:~ # apt-get install fluxbox
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package fluxbox
root@ubuntu:~ #

---

### Post by varunus on 2005-07-24
dphipps, have you enabled the extra repositories (universe, multiverse, and backports) as stated by the Ubuntu Guide ([http://www.ubuntuguide.org)?](http://www.ubuntuguide.org)?)  Fluxbox should show up if you follow this procedure.

---

### Post by dphipps on 2005-07-24
Thanks, that helped me a lot.

---

### Post by danns on 2005-07-24
gdm starts on every run level except 1.  I'm not sure if this is the ubuntu way, but what I did to prevent gdm from starting at boot is to remove S##gdm from the run level (/etc/rc#.d) you want to run at.  By default it's set for 2 (/etc/inittab holds this information), so removing S##gdm (I think it is "S13gdm") from /etc/rc2.d will prevent gdm from running at boot.

Take note that all the files in rc#.d are sym-links to the actual scripts in /etc/init.d.  Don't delete the files from /etc/init.d.  You can recreate the links by simply:

sudo ln -s /etc/init.d/gdm /etc/rc2.d/S13gdm

The files in the rc#.d directories start with either a "K" or "S."  The "K" is for kill which will kill the process when that run level is called and the "S" is for start.

Once you remove the link in the appropriate run level you will probably want to restart or use telinit:

sudo telinit 1

will bring you down to run level 1 and then

telinit 2 

will bring you back to run level 2, the default.


Now, once you have killed gdm you have the bash shell login.  You'll probably want to set your window manager of choice to start up with X when you issue startx.  Simple, edit a file called .xinitrc in your home directory.  If the file is not there, it will be created:

vi .xinitrc

Simply add a line to start your windowmanager of choice.  Since you staid fluxbox:

exec fluxbox

Follow for other window managers:

exec wmaker (windowmaker)
exec gnome-session (gnome)
exec startkde (kde)
exec startxfce4 (for Xfce 4)

Got the idea?

Again, instead of doing all this you could just use ctrl-alt-F[1-6] to change between tty's and log in there for the console.

---

### Post by eeried on 2005-07-24
> cd /usr/share/xsessions

cp gnome.desktop fluxbox.desktop

Now edit fluxbox.desktop to look like:

[Desktop Entry]
Encoding=UTF-8
Name=FluxBox
Comment=This session logs you into FluxBox
Exec=/usr/bin/fluxbox
# no icon yet, only the top three are currently used
Icon=
Type=Application
# end

Save it, and restart gdm:

/etc/init.d/gdm restart

You'll see the option now.


On another thread I read you simply apt-get install fluxbox, logout, and there it is in the session list.

So I did  but I found fluxbox was very slow (I used it with Libranet and it's really fast but then in Libranet I had the choice not to install gnome or KDE, and so nor gnome nor KDE were installed, which may explain the difference)

Now does your way (file editing) make fluxbox independent and fast (my RAM is only 128MO and though Ubuntu-Gnome looks and works fine, I'd rather have the choice at times).

Many thanks in advance !

---

### Post by danns on 2005-07-24
[QUOTE=eeried]Now does your way (file editing) make fluxbox independent and fast (my RAM is only 128MO and though Ubuntu-Gnome looks and works fine, I'd rather have the choice at times).

Many thanks in advance ![/QUOTE]

Hmmm, that is a good question for which I do not have an answer.  The only thing this does is stop gdm but once you are in flux box there should not be much more of a difference had you started it via gdm or the method I outlined.

I guess if there are other processes that are stared along with the X session initiated by the XSession scripts Ubuntu uses, the same processes may not be started when running startx from the command line.  

If you want a quick test I believe you can issue:

sudo /etc/init.d/gdm stop

which should drop you out of X and shutdown gdm.  Log in as yourself and run X ( you may want to edit .xinitrc to start fluxbox though) and see if it is faster.  If not, then 

sudo /etc/init/d/gdm start 

Will get you back.

I ran Ubuntu on a Dell Inspiron 7500 (PIII ?) with either 64 or 128 mb of ram.  Gnome was pretty slow on this system so I switched to XFCE which was a bit more responsive.

---

