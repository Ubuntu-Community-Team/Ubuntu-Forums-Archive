---
title: "Fix Gnome after KDE install"
date: 2005-11-29
forum: Desktop Environments
---

### Post by pchachte on 2005-11-29
I tried installing KDE 3.5 today, which broke my gnome setup somewhat.  In the process of trying to fix it, I might have caused other problems. I was forced to rename all my gnome preference files (see [http://http://www.ubuntuforums.org/showthread.php?t=96621&highlight=reset+gnome]("http://http://www.ubuntuforums.org/showthread.php?t=96621&highlight=reset+gnome"))
In any case, I can't get to firefox now.  When I type it into the console, I get:

> /usr/lib/mozilla-firefox/firefox-bin: symbol lookup error: /usr/lib/mozilla-firefox/components/libgfx_gtk.so: undefined symbol: pango_x_font_map_for_display


Also fonts on epiphany are now ugly.

I tried out another user on my system and everything works fine.

Any ideas?

---

### Post by aysiu on 2005-11-30
Yeah: ditch your user.
Create a new user from scratch.
Take the crucial settings (your internet bookmarks and your emails) from the broken account and copy them to the new user account.
Then, delete the old (broken) user account.

---

### Post by pchachte on 2005-11-30
I was thinking of doing that, but I'm not sure how best to transfer my home files without screwing up permissions.  Is there a way to do it without changing anything?

Thanks.

---

### Post by RAOF on 2005-11-30
You can tar everything together.  That preserves permissions.
So, for example
```
cd ~
tar cvzf firefox_prefs.tar.gz .mozilla
```
should wrap up all your firefox preferences (the .mozilla directory), preserving the permissions.  Then in your new user
```
cd ~
tar xvzf firefox_prefs.tar.gz
```
will unpack all the prefs, with the same permissions, except owned by the new user.

---

### Post by aysiu on 2005-11-30
You can also use the *chown* command. Let's say, for example, that your current username is raof, and your config files belong to the group raof (this is very likely--as my user group is also the same as my username).

Once you've created the new user--let's say the new user is called foar--copy over the config files to the new user (for this example, I'm assuming Thunderbird is the email client): ```
sudo cp -r /home/raof/.mozilla-thunderbird /home/foar/.mozilla-thunderbird
sudo chown -R foar:foar /home/foar/.mozilla-thunderbird
``` The *chown* command **ch**anges **own**ership.

---

### Post by pchachte on 2005-11-30
I'm glad this is coming up now, since I'm under no pressure and I still have my data in tact. 

Now my question is how to transfer over my encryption information.  I use an ssh tunnel to send mail through my university.  I also use ssh encryption for some pages which I look at through emacs-planner (i.e. M-x pgg-encrypt-buffer).  

I've never really understood ssh that well.  But in my new home, I can't send mail, nor can I open my encrypted files.  The problem is now that my account is carlos instead of charles and so my ssh keys no longer work.  How can I transfer ssh stuff into my new account?

Thanks in advance.

---

