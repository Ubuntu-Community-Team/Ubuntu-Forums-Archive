---
title: "Transparency in program icons in top tray? Not working properly..."
date: 2006-08-31
forum: Desktop Environments
---

### Post by kendals on 2006-08-31
Hey guys.

[[IMG]http://img422.imageshack.us/img422/51/screenshotks3.th.png[/IMG]](http://img422.imageshack.us/my.php?image=screenshotks3.png)

As you can see by my screenshot, icons like Gaim in the notify tray, or checkgmail, have a grey background, rather than being transparent like all the other icons.

How can I make them transparent as well? Thanks! :confused: :rolleyes:

---

### Post by John.Michael.Kane on 2006-08-31
kendals that is the theme your using causing that. you will have to try a diffrent theme.

---

### Post by kendals on 2006-08-31
Oh, but I like the default Ubuntu theme :(

Any other themes that look the same, but get rid of the yucky grey background issue? Thanks for the quick reply, btw :)

---

### Post by John.Michael.Kane on 2006-08-31
theres a few pre-installed with ubuntu.
**click system > preferences > theme**  there should be a few listed there that may fit the bill.

For themes that are not included you can look over at  [**gnome-look.org**]("http://www.gnome-look.org/")

---

### Post by kendals on 2006-08-31
Thanks, SD. :P

---

### Post by OffHand on 2006-08-31
Which theme did you use to get the tray icon trasparant?

---

### Post by kendals on 2006-08-31
Nothing yet :(

---

### Post by seamus7 on 2006-10-13
CheckGmail's preference menu only allows you to change the background color to another color. I myself am trying to find the CheckGmail icons. There are three: new mail, no mail, and error in order to edit them. But all this is pointless if we can't turn the background color off in CheckGmail preferences.

---

### Post by David Corrales on 2006-10-13
The lies in the icons, not the theme. Compliant icons should be png's with transparency around the image.
You should contact the developer so they update the icons or replace them yourself.

---

### Post by andrei.kouznetsov on 2007-06-14
The problem is in GTK: [http://checkgmail.sourceforge.net/#faq](http://checkgmail.sourceforge.net/#faq)
And hopefully it will be fixed in the next major release: [http://bugzilla.gnome.org/show_bug.cgi?id=150726](http://bugzilla.gnome.org/show_bug.cgi?id=150726)

---

### Post by jimbo99 on 2007-06-14
Pidgin is the official replacement for gaim.  You might consider downloading and installing it.  Maybe they fixed it.

As far as that goes as far as I recall the gaim was properly created to work with transparency.  If it had not I would have noticed it.  Did you change the icon yourself?

I agree that if you didn't modify the default theme it should work.  But you should consider other themes.  There are some nice ones.

I also noted you were logged in as root.  That is not a good thing.  After working with Linux in the proper way you will get over the hurdles that forced you to log in as root.  But as a root user if you work on an account other than root and then log in as that account you could/will have problems with all sorts of things due primarily to permissions.  Anyway, just a thought.

Icons are all over the place in Linux.  I know it is pretty bad.  I wanted to change the appearance of the trashcan icon and if you look you'll see there's no choice there to change it in properties.  So, I spent all this time copying icons to various folders under a theme and then managed to get something working.  It took me a long long time to do that.  But alas, today I found that the theme I used was stored in a hidden folder in my home folder.  That hidden folder was called .icons.  In that folder was the theme icons I had installed and in there was a simple way to change the icon for the trash.  I was very impressed and now am happy that I can change the trash icon at will with little effort.

---

### Post by mcduck on 2007-06-14
For the Checkgmail problem, you could try using Mail Notification Applet instead. It handles Gmail as well as POP/IMAP mail accounts, and at least with all of the themes I've used it has had transparent background..

---

