---
title: "Screensaver/sleep under XGL/Compiz"
date: 2006-08-17
forum: Desktop Environments
---

### Post by Cable on 2006-08-17
How can I change the options pertaining to the screensaver and the monitor turning itself off after a certain amount of time under XGL/Compiz?  My monitor keeps turning itself off, and I don't want it to!

---

### Post by swamytk on 2006-08-17
I hope GNOME "Power Management" tool in System->Administration menu will do.

---

### Post by Cable on 2006-08-17
I thought it would be fine, but the settings I have chosen there apparently don't apply to XGL/Compiz.  I have it set to never turn off the monitor, and yet it still turns off.

---

### Post by neymac on 2006-10-25
The same here and I tried evereything without success.

Dapper with XGL/Beryl

---

### Post by squidward_tentacels on 2006-11-21
Im having the identical problem, with XGL, Dapper. I have tried power-saving options, even disabling gnome-power-manager from the start up programs alltogether....still no luck, as stated above, these options just dont seem to apply to gnome. The really wierd part is, It was working fine on this machine, with no hardware changes, until I reinstalled ubuntu. I reinstalled xgl exactly the same way I did the first time.....:confused: 

If anyone has a work-around, or any of the previous posters in this thread found a solution, Please share....Its driving me crazy;) 

I think my next step, if no one knows whats going on with this will be to reinstall xgl/ beyrl.

---

### Post by squidward_tentacels on 2006-11-21
OK, reinstalling XGL / Beryl / Emerald didnt do it, The only fix I could find for this was to apend xgl to a gnome session, rather than choosing xgl as a seperate system session....I kinda wanted to keep them seperate,in case xgl decided to stop playing well with others:p , but its the only way I found to stop the monitor from turning off after 10 minutes of inactivity. I was going to link the Beryl wiki with the steps to do this but,

"Beryl Wiki has a problem

Sorry! This site is experiencing technical difficulties.

Try waiting a few minutes and reloading.

(Can't contact the database server: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) (localhost))" 

I wonder if they were running Beryl too, LOL!

So, basicly the fix is as follows;
<code>

sudo gedit /etc/gdm/gdm.conf-custom

</code>

And add this to the bottom of the page;

<code>

0=Xgl
[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true

</code>

And change the default session back to gnome.

---

